---
title: "Valgrind error"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by samking on 2010-05-25
I am new Ubuntu. Just installed Ubuntu 10.04.

$ uname -a
Linux linuxman-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

Installed Valgrind 3.6.0, without any issues. 

Getting following error while running valgrind against any executable. Can someone help me what is causing this issue?

$ valgrind ls -lt
==6122== Memcheck, a memory error detector
==6122== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==6122== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright info
==6122== Command: ls -lt
==6122== 
[COLOR=Red]**ls: ../sysdeps/x86_64/cacheinfo.c:257: handle_intel: Assertion `maxidx >= 2' failed.**[/COLOR]
==6122== 
==6122== HEAP SUMMARY:
==6122==     in use at exit: 86 bytes in 1 blocks
==6122==   total heap usage: 2 allocs, 1 frees, 186 bytes allocated
==6122== 
==6122== LEAK SUMMARY:
==6122==    definitely lost: 0 bytes in 0 blocks
==6122==    indirectly lost: 0 bytes in 0 blocks
==6122==      possibly lost: 0 bytes in 0 blocks
==6122==    still reachable: 86 bytes in 1 blocks
==6122==         suppressed: 0 bytes in 0 blocks
==6122== Rerun with --leak-check=full to see details of leaked memory
==6122== 
==6122== For counts of detected and suppressed errors, rerun with: -v
==6122== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 25 from 8)
Aborted

---

### Post by ibuclaw on 2010-05-25
Does the command:

```
ls -lt
```
work OK without Valgrind?

Looks to be memory corruption to me, but you could try reinstalling libc and core-utils.

Regards

---

### Post by samking on 2010-05-25
ls -lt is working fine. Valgrind is giving this error for all executables.

```
$ ls -lt
total 20
-rwxr-xr-x 1 samking samking 8372 2010-05-25 06:23 random
-rw-r--r-- 1 samking samking  166 2010-05-25 06:23 random.c
-rw-r--r-- 1 samking samking  188 2010-05-25 06:22 random.c~

$ valgrind ls -lt
==6931== Memcheck, a memory error detector
==6931== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==6931== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright info
==6931== Command: ls -lt
==6931== 
ls: ../sysdeps/x86_64/cacheinfo.c:257: handle_intel: Assertion `maxidx >= 2' failed.
==6931== 
==6931== HEAP SUMMARY:
==6931==     in use at exit: 86 bytes in 1 blocks
==6931==   total heap usage: 2 allocs, 1 frees, 186 bytes allocated
==6931== 
==6931== LEAK SUMMARY:
==6931==    definitely lost: 0 bytes in 0 blocks
==6931==    indirectly lost: 0 bytes in 0 blocks
==6931==      possibly lost: 0 bytes in 0 blocks
==6931==    still reachable: 86 bytes in 1 blocks
==6931==         suppressed: 0 bytes in 0 blocks
==6931== Rerun with --leak-check=full to see details of leaked memory
==6931== 
==6931== For counts of detected and suppressed errors, rerun with: -v
==6931== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 25 from 8)
Aborted
```[B]
[/B]

---

### Post by ibuclaw on 2010-05-25
OK, reboot and hold down the Left Shift key and select the memtest entry. Memtest86 will perform many different tests on your ram, some of which can take longer than 30 minutes. Ideally let thoroughly test your ram, let memtest86 run overnight.

Regards

---

### Post by samking on 2010-05-27
Why valgrind refering to x86_64 libraries, as I have installed Ubuntu i386 (AMD Athlon, doesn't support 64 bit).

Do I have to update any specific libraries?

---

### Post by ibuclaw on 2010-05-27
> **samking said:**
> Why valgrind refering to x86_64 libraries, as I have installed Ubuntu i386 (AMD Athlon, doesn't support 64 bit).

Do I have to update any specific libraries?

Valgrind is not referring to x86_64 libraries. It is referring to an assertion that occurs in a C source file that just so happens to be in a directory named x86_64 (does not necessarily mean that it is x86_64 specific) - You know the name and location of the file in the source tree due to debugging information being inlined into the executable/libraries.

Because the assertion happens with a number in memory, hence why I suggested you run a MemTest, as this looks more like Memory corruption, rather than a system error.

Regards
Iain

---

