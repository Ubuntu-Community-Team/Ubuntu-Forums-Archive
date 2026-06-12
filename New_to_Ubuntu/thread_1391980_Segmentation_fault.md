---
title: "Segmentation fault"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by newport_j on 2010-01-27
The following code works when compiled to 32-bit program and run on a 32-bit Ubunut 8.04. 
 
 
#include <stdio.h>
 
int main(int argc, char *argv[]){
 
int i, j, k;
double Rdiff;
double Temp;
FILE *fid; 
/* Initialize Sorce and Reciver locations */
fid = fopen("../TestJigs/Inputs/LIB/Acoustics/SorRec.in","r");
fscanf(fid,"%*[^\n]");
fscanf(fid,"%*[^\n]");
fclose(fid);
};
 
 
When it is compiled as a 64 bit program and run on a 64 bit Ubuntu it gives a segmentation fault. The error line or the crash line is:
 
fid = fopen("../TestJigs/Inputs/LIB/Acoustics/SorRec.in","r");
 
 
Now when I compile it to a 32 bit program and run it on a 64 bit Ubuntu it also crashes. 
 
I am not sure why it does. It seems to have something to do with fid.
 
Yours truly,
 
 
Newport_j

---

### Post by Hospadar on 2010-01-27
there is a developer forum which would be a better place for it.
what line does it crash on?

---

### Post by newport_j on 2010-01-27
The program crashes on the
 
 
fid = fopen 
 
 
line. It works as a 32 bit program on a 32 bit Ubuntu operating system, when compiled to a 64 bit program with a 64 Ubuntu operating system it fails.
 
 
newport_j

---

### Post by dearingj on 2010-01-27
> **newport_j said:**
> The following code works when compiled to 32-bit program and run on a 32-bit Ubunut 8.04. 
 
 
#include <stdio.h>
 
int main(int argc, char *argv[]){
 
int i, j, k;
double Rdiff;
double Temp;
FILE *fid; 
/* Initialize Sorce and Reciver locations */
fid = fopen("../TestJigs/Inputs/LIB/Acoustics/SorRec.in","r");
fscanf(fid,"%*[^\n]");
fscanf(fid,"%*[^\n]");
fclose(fid);
};
 
 
When it is compiled as a 64 bit program and run on a 64 bit Ubuntu it gives a segmentation fault. The error line or the crash line is:
 
fid = fopen("../TestJigs/Inputs/LIB/Acoustics/SorRec.in","r");
 
 
Now when I compile it to a 32 bit program and run it on a 64 bit Ubuntu it also crashes. 
 
I am not sure why it does. It seems to have something to do with fid.
 
Yours truly,
 
 
Newport_j

Have you verified, for certain, that the SorRec.in file actually exists in that location on your 64-bit install, and that you have permission to read from it? That seems like it could cause a segmentation fault like this.

---

### Post by avidday on 2010-01-27
> **newport_j said:**
> The program crashes on the
 
 
fid = fopen 
 
 
line. It works as a 32 bit program on a 32 bit Ubuntu operating system, when compiled to a 64 bit program with a 64 Ubuntu operating system it fails.
 
 
newport_j

I don't believe that is actually where it fails. I am betting it is the first fscanf, probably because the file handle returned is NULL (if you read the man page for fopen you will see it returns NULL if the file couldn't be successfully opened).

Why not try writing something slightly more sensible, like this:

```

if ( (fid=fopen("supersecretnavydata.txt", "r")) == NULL ) {
    perror("fopen failure");
    exit(1);
}
fscanf(fid,"%*[^\n]");
.......

```

---

