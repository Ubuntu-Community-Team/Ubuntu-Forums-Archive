---
title: "Can't boot after installation 9.04"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by colormoon on 2009-04-25
I've installed 9.04 Jaunty last few days. After intallation finish, I restart and wait for boot to desktop but it show me an error.

BUG : Inf14 : CR2 ffff60f0
EDI00000... (and more)

I don't know what's the problem with it? and How can I fix it?
thank you.

---

### Post by Sef on 2009-04-25
What are your system specs?

---

### Post by colormoon on 2009-04-25
I use old computer.
1 Ghz intel celeron, 310M ram, HDD 60 Gb
I try ubuntu and xubuntu alternate installation. It show the same result.

---

### Post by colormoon on 2009-04-28
any idea?

---

### Post by skymera on 2009-04-28
Perhaps a memory error?

Boot the Ubuntu LiveCD again and choose "Memory Test".

It will take a while but will check your memory for any errors :)

I suggest this as "CR2 ffff60f0" seems like a bad memory issue

---

### Post by colormoon on 2009-04-28
Thank you for your reply
But... I try to test memory, and it said pass 100%. So, I try to install xubuntu 9.04 again by alternate CD. After installation finish, it still show me a bug:

BUG : Int 14: CR2 fffb0f0
   EDI 00000000  ESI 00000000  EBP c0731f3c  ESP c0731f1c
   EBX 00000046  EDX 0000000e  ECX 00000000  EAX ffffb0f0
   err 00000000  EIP c0119891   CS 00000060  flg 00070046

Stack : c011a26e 00000046 00000046 00000000 c0731f48
        c05009ff c05fb24c c07e1a60 00eefa2b 00000000
        007b1000 00000000 00eefa2b 00000000 c05f7b84

        c0118a66 00eefa2b c0731f60
        c0731fb8 c074144c c05f081c
        00100000 00000000 0087c52b

how should I solve this bug?

---

### Post by Somedeadguy on 2009-05-16
I'm having the exact same problem.  Did you find out a way around this?  I've tried totally reinstalling and everything.  My CD is fine, and my memory passes.  I don't get it!

---

### Post by lisati on 2009-05-16
I'm just guessing here, but I think that the reference to "int 14" could suggest that there's some kind of problem accessing one of your computer's serial ports.

"int 14" seemed vaguely familiar from my reading a few years ago for doing ASM programs on MS-DOS, I had to look it up (have a look [here]("http://heim.ifi.uio.no/~stanisls/helppc/int_14.html"))

---

### Post by Didius Falco on 2009-05-16
Hi,

Have a look through this LaunchPad bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/312554](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/312554)

I hope it helps...

Regards,

Didius

---

