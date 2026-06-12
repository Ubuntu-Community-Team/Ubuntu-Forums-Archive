---
title: "compile any c/c++"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by biky2004indra on 2008-12-23
Hi,
I am in a big problem. Please help me. my problem is that when i am trying to compile any c/c++ program using the command g++ -lm sample.c -o sample, where sample.c is my c program name, the the following error message is giving : /usr/bin/ld: 1: Syntax error: newline unexpected
          collect2: ld returned 2 exit status
I am using UBUNTU 8.10 and it was updated regularly. I have tried in various way to debug, but no one is working. How can i solve it. someone suggested to uninstall everything and reinstall again. i have already uninstalled g++ and gcc & then reinstalled again. but no positive result. can anyone tell me how can i solve it without formatting the ubuntu.
Thanks and waiting.

---

### Post by biky2004indra on 2008-12-23
Hi,
I am in a big problem. Please help me. my problem is that when i am trying to compile any c/c++ program using the command g++ -lm sample.c -o sample, where sample.c is my c program name, the the following error message is giving : /usr/bin/ld: 1: Syntax error: newline unexpected
          collect2: ld returned 2 exit status
I am using UBUNTU 8.10 and it was updated regularly. I have tried in various way to debug, but no one is working. How can i solve it. someone suggested to uninstall everything and reinstall again. i have already uninstalled g++ and gcc & then reinstalled again. but no positive result. can anyone tell me how can i solve it without formatting the ubuntu.
Thanks and waiting.

---

### Post by igknighted on 2008-12-23
gcc is the command to compile C code, not g++

---

### Post by biky2004indra on 2008-12-23
ok, but why it is not working when i am trying to compile c code with gcc

---

### Post by igknighted on 2008-12-23
> **biky2004indra said:**
> ok, but why it is not working when i am trying to compile c code with gcc

Can you copy/paste the command and the error it gives you?

---

### Post by biky2004indra on 2008-12-23
Thanks for your reply.
command is : gcc -lm sample.c -o sample
error msg is : /usr/bin/ld: 1: Syntax error: newline unexpected
               collect2: ld returned 2 exit status

---

### Post by igknighted on 2008-12-24
I've never used -lm, what is this for (thats WAY too long a man page to search :P)

Also, many libraries gcc needs to actually work are not installed by default.  Try installing the build-essential package if you haven't already.

---

### Post by biky2004indra on 2008-12-24
I have already installed build-essential package.
But givin the same error.

---

### Post by igknighted on 2008-12-24
can you post the code you are trying to compile (use the code tags)

---

