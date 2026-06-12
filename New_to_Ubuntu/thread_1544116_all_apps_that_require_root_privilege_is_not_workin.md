---
title: "all apps that require root privilege is not working"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by eshant_engineer on 2010-08-02
please help me to sort out this problem...whenever I open any thing that requires root privilege doesn't open + terminal also...

LOGS:
```
Aug  2 13:07:46 eshant-EZEE kernel: [ 1047.747614] gnome-terminal[3559]: segfault at 7fff47ad1fd8 ip 00007f0ad225b87d sp 00007fff47ad1fe0 error 6 in libc-2.11.1.so[7f0ad21f4000+17a000]
Aug  2 13:09:08 eshant-EZEE kernel: [ 1129.817848] gksu[3625]: segfault at 7ffeff89ffe8 ip 00007f8f80bb287d sp 00007ffeff89fff0 error 6 in libc-2.11.1.so[7f8f80b4b000+17a000]
Aug  2 13:09:49 eshant-EZEE kernel: [ 1170.827107] gksu[3660]: segfault at 7fffe83c3ff8 ip 00007f4941ab3b10 sp 00007fffe83c4008 error 6 in libc-2.11.1.so[7f4941a3e000+17a000]

```

What log is telling is error in line 6 of libc-2.11.1.so. What is the solution for this problem

Thank You

---

### Post by Rubi1200 on 2010-08-02
>  
Common causes
A few causes of a segmentation fault can be summarized as follows:
[LIST]
[*]attempting to execute a program that does not compile correctly. Note that most compilers will not output a [[COLOR=#0645ad]binary[/COLOR]]("http://ubuntuforums.org/wiki/Binary_file") given a compile-time error.
[*]a [[COLOR=#0645ad]buffer overflow[/COLOR]]("http://ubuntuforums.org/wiki/Buffer_overflow").
[*]using uninitialized pointers.
[*]dereferencing NULL pointers.
[*]attempting to access memory the program does not own.
[*]attempting to alter memory the program does not own ([[COLOR=#0645ad]storage violation[/COLOR]]("http://ubuntuforums.org/wiki/Storage_violation")).
[/LIST]
 
From this article:
 
[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)
 
Hope this helps.

---

