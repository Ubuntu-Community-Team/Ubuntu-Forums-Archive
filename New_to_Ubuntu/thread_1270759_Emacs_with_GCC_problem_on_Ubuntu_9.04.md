---
title: "Emacs with GCC problem on Ubuntu 9.04"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by motrax on 2009-09-20
Hello !

I'm using emacs 22 on ubuntu 9.04. When using GCC/g++ in the shell from within Emacs I'm getting weird characters for error messages. I didn't have this problem on fedora 8 and 9, so I thought it might be an Ubuntu specific problem and I'm posting it here.

This is what I'm getting.

prepro_debug.cpp: In function â\200\230int main()â\200\231:
prepro_debug.cpp:28: error: â\200\230cinâ\200\231 was not declared in this scope
tapti@tapti-laptop:~/Documents/Coding/C++$  

I have enabled color by using ansi-color-for-comint, but that doesn't help either. Please help.

---

### Post by superdav42 on 2009-09-20
yea, that's weird. Looks like some sort of encoding issue. Does it matter what kind of terminal you run it it in? Have you tried xterm and a real terminal by pressing ctrl+alt+f1

---

### Post by motrax on 2009-10-02
Sry for the late reply. Ya, the problem does not occur if I try it in a real terminal. It only occurs when emacs opens in a new window (with GUI). Please help. 

Thnx.

---

