---
title: "build-essential autoconf automake libxmu-dev (ns2 on Ubuntu 7.04)"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by tarm121 on 2008-12-24
Hi, I'm new to Ubuntu... A little bit about my Ubuntu world. I've just installed Ubuntu  7.04 on my laptop Aspire 1200X (Intel Celeron 1 GHz with 384 MB RAM) sharing with Windows XP O/S on 20GB HDD. Ubuntu 8.10 won't work on my laptop probably because of its minimum specs. Ubuntu 7.04 works fine on my laptop EXCEPT if I install updates from repositories that makes my systems hang! The system hangs even if I enable the "Desktop Effects".. Thus, I decided to leave it blank at the repositories.
:popcorn:
My intention of using Ubuntu 7.04 is because I want to run ns2.31 simulator for my project. Since I'm a newbie in Linux/Ubuntu World and ns2, then I choose to follow step-by-step instruction as shown in:

[http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04](http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04)

However, I'm stuck at the instruction at line:

$ sudo apt-get install build-essential autoconf automake libxmu-dev

First I got message:

E: Couldn't find package build-essential.

Then, by following some thread on the forum shown below, I managed to install build-essential by inserting the CD installer on the CD drive:

$ sudo apt-cdrom add
$ sudo apt-get update
$ sudo apt-get install build-essential 

However, there are still some error in installing "autoconf, automake, libxmu-dev". The error message are: 

E: Couldn't find package ............

I have tried to download it from the websites below, however, all are broken links... 

[http://packages.ubuntu.com/feisty/all/autoconf/download](http://packages.ubuntu.com/feisty/all/autoconf/download)

I know there could be an easy way to install those packages through "Synaptic Package Manager", however, I'm afraid if I enable those updates, my systems will hang again, and I have to re-install the O/S again.

I can't solve these problem, so, can anybody out there in the Ubuntu WORLD help me out...I really appreciate if you can give step-by-step instruction. 
 :(

---

### Post by taurus on 2008-12-24
Have you tried Hardy, 8.04?  Feisty has reached the end of it life so you will not get any support, no update, and no security fix.

---

### Post by tarm121 on 2008-12-24
> **taurus said:**
> Have you tried Hardy, 8.04?  Feisty has reached the end of it life so you will not get any support, no update, and no security fix.

Thanks Taurus... I've tried updating to 7.10 and it hanged.. So does the version 8.10 (most probably when using the graphical environment).. It works fine using recovery option... but not GNOME (*i think*). I'll try Hardy and will get back to you.. :P

---

### Post by tarm121 on 2008-12-25
Dear All,

I've installed Ubuntu 8.04 (Hardy Heron) and ns2.33 simulator. So far, everything seems working fine. For those who are seeking to run ns2 simulator on Linux with minimum hardware requirements, I'd reckon with this version. Thus, the problems with installing the build-essential, autoconf, automake and libxmu-dev could be avoided.

What you need to do, is 
1. Download Ubuntu 8.04
2. Burn the image onto the CD
3. Install the Ubuntu
4. Install the Updates
5. Install ns2.33 simulator following step-by-step shown in [http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04](http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04)
(except.. change ns2.31 to ns2.33)

Finally... you're ready to enter another room of ns2...
:guitar:

---

### Post by NANOspace on 2009-04-08
Hello all,
I have downloaded Ns2.33 on latest ubuntu 8.10. As used no problems but i'm having a problem in making scenarios through make-scen.csh in setdest folder. I tried to solve by installing tcsh. now i run the make-scen file like this: ./make-scen.csh and it tries to generate scenarios but gives the same error for each,like this:
scen 10 : setdest -v 1 -n 50 -p 0 -M 20 -t 500 -x 500 -y 300
scen_out/scen-500x300-50-0-20-10: No such file or directory.
0.000u 0.000s 0:00.00 0.0%	0+0k 0+0io 0pf+0w
if anyone can help?!
thanx ):P

---

