---
title: "libc6-dev-amd64 doesn't support to execute compiled module on i686?"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by ua6ta123 on 2010-07-30
Hello!
i installed libc6-dev-amd64 and probably success to compile the codes with inline-asm.
But i cannot execute the compiled module. Is there no way to run the command of 64-bit on i686?

simply done as follows:
1. dpkg libc6-dev-amd64 by Synaptic Manager
2. $ gcc -m64 testcode-with-inline-asm-of-amd64.c -o test
    (no error reported: Success to compile??)
    $ ./test
    bash: ./test : unable to execute binary file(in Japanese)
    $ gcc --version
    gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3

i tried to install Ubuntu10.04LTS-amd64 but unable because CPU is not x86-64 but only i686.

---

### Post by ua6ta123 on 2011-01-01
Hi everyone, I wish you a Happy New Year from Tokyo, Japan!

I bought a 64-bit PC in the end of last year around Christmas.

I installed Ubuntu10.04LTC-amd64 right after the purchase.

In this afternoon of 1 January, 2011, I checked and successed to execute the compiled modules compiled by gcc supported libc6-dev-amd64 on 32bit PC, on the 64-bit new PC.

Consequently I understood, libc6-dev-amd64 surely supports to execute compiled modules on 32-bit PC.

Thank you !!! :p

---

