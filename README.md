#include <stdio.h>
int main() {
    FILE *fp;
    char ch;
    int words = 0;
    int inWord = 0;
    fp = fopen("myfile.txt", "r");
    if (fp == NULL) {
        printf("Error: myfile.txt not found!\n");
        return 0;
    }
    while ((ch = fgetc(fp)) != EOF) {
       if ((ch >= 'A' && ch <= 'Z') || (ch >= 'a' && ch <= 'z') || (ch >= '0' && ch<= '9')) {
            if (inWord == 0) {
                words++;
                inWord = 1;
            }
        } 
        else {
            inWord = 0;
        }
    }
    fclose(fp);
    printf("\n===== RESULT =====\n");
    printf("File: myfile.txt\n");
    printf("Total Words: %d\n", words);
    return 0;
}

