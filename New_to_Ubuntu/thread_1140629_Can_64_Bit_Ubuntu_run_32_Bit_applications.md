---
title: "Can 64 Bit Ubuntu run 32 Bit applications?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by 11010110 on 2009-04-27
Hi everyone, 

I am looking around at future replacements for my laptop and I noticed that System 76 uses a 64 Bit processor in the model i am considering along with the 64 Bit version of Jaunty. I have heard some things about how it is much more of a pain to use 64 because there is not very much software that works with it. Is this true? Would using the 64 bit version be worth all of the hassle versus using the 32 bit version? Say I had a program that was only made for 32 Bit processors could I run it in my 64 Bit environment?

I wont be upgrading for a while but I'm always itching to learn more!

Thanks in advance everyone! Any information is appreciated!


EDIT: Also would it in any way effect my use of Wine for running windows games and other apps and would 32 Bit versions of those still be compatible? I can't run very much right now due to my Intel Chipset so I would hate form one of my reasons for upgrading to be thwarted by the CPU lol.

---

### Post by Dougie187 on 2009-04-27
Yes

---

### Post by 11010110 on 2009-04-27
Thanks for the reply. If a 64 Bit processor and Ubuntu can run normal 32 Bit programs then what are all of the downsides that I keep hearing about?

---

### Post by jimmy the saint on 2009-04-27
To be clear.

A 64 bit processor can run 32 or 64 bit Ubuntu.

The the 64 bit Ubuntu will not, however, be able to run 32 bit appliations except when 32 bit libraries are used as a workaround.  Most applications have both a 32 and 64 bit package available in the repos, so youre system will just automatically install the correct one.  In addition most (all as far as I know) software can be made either way, you just need to get and compile program yourself.  You will probably not need to got that route though, Ubuntu's repos have just about anything you would want.

Most of the downsides have been worked out.  Every one in a while someone will release a program that is only good for 32 bit unless you want to compile it yourself.  Flash used to be a pain in the rear, but even that works fine now.  I'd go with  64 bit.  The issues are in the past

---

### Post by 11010110 on 2009-04-27
Thanks very much Jimmy the Saint for the explanation. I have tried to compile something in the past once and it ended up as an epic failure lol. So can anything be compile to work under 64 Bit if I am supplied with the source code?

Thanks again

---

### Post by Dr.Vista on 2009-04-27
It should, 32 bit systems can't run 64 bit software but 32 bits os's can.

---

### Post by Dougie187 on 2009-04-29
If you get source code, then you should be able to compile anything to run on a 64 bit machine.

Sometimes you might find prepackaged binaries that are made for a 32 bit operating system, and in this case, you might have to install the 32 bit library. Here there is a program called "getlibs" that can help you with this problem.

Otherwise everything should be able to run on a 64 bit OS.

The main downsides you hear are from people who don't know how or don't use a 64 bit os. Also, a while back support for a 64 bit os was pretty poor, so they are remembering more history than anything.

---

