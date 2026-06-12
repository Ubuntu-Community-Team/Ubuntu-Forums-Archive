---
title: "detecting shutdown signal"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by node2network on 2010-09-02
This is my first post.
If my English is not polite, please forgive me.

My question is about my C program below.


```

#include <signal.h>
#include <stdio.h>
#include <stdlib.h>

void sigcatch(int);

int main() {
    if (SIG_ERR == signal(SIGTERM, sigcatch)) {
        printf("failed to set signal handler.n");
        exit(1);
    }

    while (1) {
        sleep(1);
    }

    return 0;
}

void sigcatch(int sig) {

    FILE *fp;
    fp = fopen("log", "a");

    if (fp == NULL) {

        fprintf(stderr, "Error: Unable to open %s\n", "log");
        exit(8);
    }

    fprintf(fp, "terminate!");

    close(fp);

    printf("catch signal %dn", sig);
    exit(1);
}

```

What I want to do with this program is to get the shutdown signal (SIGTERM).
But, when I executed "sudo shutdown -h now", it won't work and the log file
was not created.

Instead of "sudo shutdown -h now", I executed "kill <PID of the program>".
Then, I found that the log file was created at the current directory. 

Does anyone have any idea how my program can detect the shutdown signal when I execute "sudo shutdown -h now"?

---

### Post by theDaveTheRave on 2010-09-02
node2network

I think the issue may lie with the use of the ```
shutdown -h now
```

Essentially it drops the run level immediately, and you may find that your little program is 'stopped from running' before it has a chance to catch the signal, or it the disk can no longer be written to when it does catch it.

have you tried instead to use a longer time scale on your shutdown line (maybe 10 seconds, to give the whole thing time to register and write to disk?)

The other alternative is that you may need to change the permisions and run level of the program.

I don't know how 'linux savy' you are, but check out the different run levels, there is a tutorial out there on the ubuntu wiki.

David.

ps. you english was fine, you aren't going to start any flame wars ;)

---

