---
title: "setting up a original daemon"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by node2network on 2010-09-02
Hi, i'm a novice programmer.
I have a question about setting up a daemon of c program.
The daemon is simple, just adding a string to a file.
The daemon program (sample1.c) is bellow.

*sample1*
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

void foo() {

    FILE *fp;

    while(1) {

        fp = fopen("log", "a");

        if (fp == NULL) {

            fprintf(stderr, "Error: Unable to open %s\n", "log");
            exit(1);
        }

        fprintf(fp, "foofoo !\n");

        fclose(fp);

        sleep(60);
   }
}


int main(void) {
    if(daemon(0, 1) == 0) {
        foo();
    } else {
        printf("error\n");
    }
    return 0;
}

```

$ gcc -o sample1 sample1.c
$ ./sample1
Error: Unable to open log
(This process was not ended. So, Ctrl-C to terminate.)

Then, I changed the above program a little.
The modified program (sample2) is below.

*sample2*
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

void foo(FILE *fp) {

    while(1) {

        fprintf(fp, "foofoo !\n");
   }
}


int main(void) {

    FILE *fp;
    fp = fopen("log", "a");

    if (fp == NULL) {

        fprintf(stderr, "Error: Unable to open %s\n", "log");
        exit(1);
    }

    if(daemon(0, 1) == 0) {

        foo(fp);
    } else {

        printf("error\n");
    }

    fclose(fp);

    return 0;
}

```

This program worked correctly.

Why sample1 won't work as I expected?

---

### Post by node2network on 2010-09-02
My question isn't solved.
Please help me.

---

