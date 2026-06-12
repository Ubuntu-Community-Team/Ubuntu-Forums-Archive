---
title: "I offer $$MONEY$$ for help!"
date: 2005-04-14
forum: Networking &amp; Wireless
---

### Post by razialx on 2005-04-14
I removed the text. I am sorry mods. Could you please change the title of the thread. Thanks.
***CONTENT REMOVED***
I am desperate for a guide to getting LEAP working in Ubuntu. My school uses LEAP, and I really wish to use Linux (Ubuntu!!) as my operating system. I have scoured the net looking for instructions on getting LEAP working, with no clear answer. I have installed xsupplicant, yet have no idea how I am supposed to use it. (I read the manual). Everywhere I go, people who have gotten it working give a brief explaination as to how, which would be useful to someone with more Linux Networking experience than I have.

I need step by step instructions if possible. What would I need to do from the point of a fresh install to get LEAP working. I plan on helping my other friends and teaching this to the help desk at our school once I know how to do this perfectly. From first install. Everything else I have read has been "well, do this with the AIRO utilities, or xsupplicant."  Thanks so much for ANY help you can give.

Also, note I have a Dell 8500 Laptop, with all hardware working fine. I have a Cisco Aironet 350 PCMCIA card. I am able to connect to my home network which does not use LEAP with no problem. I dual boot with Windows XP prof. which is mounted on an NTFS partition. However, I also have a 1 GB FAT32 partition, and since I can not apt-get at school(with no network connection) I download .DEB packages to this partition in windows. You would not have to take this in to account when writing a tutorial though, I can work around the lack of apt-get.

Tim Reynolds.
razialx

---

### Post by ubuntu_demon on 2005-04-15
offering money for help is not really in the spirit of the community. Most people in the community are glad if they can help and this is enough of a reward. I am not going to delete this thread. As far as I know it isn't forbidden to offer money for help :-p

I would help you for free. Too bad I don't know anything about CISCO LEAP.

---

### Post by uberlinux on 2005-04-15
good luc man, really.  I think it would be great to get more stuff going when it comes to cisco/linux interoperability, those 350's are great cards man. I wish I could help. I'll keep an ear out.

---

### Post by StacyWebb on 2005-04-15
just curious, have you tried vpnc or the actual Cisco client for Linux. Thats what I use to connect (KVpnc) you can import the pcf cisco file and use that for authentication. 
If it works I don't want any money

---

### Post by jdong on 2005-04-15
As to the money/reward issue:

I'll let this one slide; as the OP is pretty desperate to get things working.

If we see too many of these in the future, we will make an official policy (probably to ban publicly offered monetary rewards)

---

### Post by razialx on 2005-04-18
I am sorry for the money offer. 

I did not want to go against the spirit of the community, I am in fact just desperate to get this working. If I can, I will edit the title of the thread accordingly.

However, I still am no closer to solving this. I -know- this is possible, yet I can not find the path.

StacyWebb - I do not know what vpnc is, I will  look it up. I can not get the official Cisco drivers to install (even with the -id flag to only install the driver and not the GUI part). I may not have all the building packages I need to do that (I have build-essentials).

Stacy, If you could just give me a run through of what you did to get LEAP working, I would be so unbelievably appreciative. Thank you.

---

### Post by luca_linux on 2005-04-18
Try to install gcc in order to build the driver.
If you post the error messages, we will be able to help you.

---

### Post by StacyWebb on 2005-04-18
vpnc is a Cisco clone on the actually cd for the Cisco client there is a Linux client (KVpnc is just a gui for vpnc) you can find it here  [vpnc](http://www.unix-ag.uni-kl.de/~massar/vpnc/) version 0.3.2 should work for you.

Also when you run the make if you get errors post them and we'll walk though what you need to do, that's a lot easier to do the a general install.

---

### Post by razialx on 2005-04-19
I will install this when I get home. Thank you very much.

---

### Post by razialx on 2005-04-24
Ok, I have installed vpnc and xsupplicant, build-essentials kernel source (though I do not know if I have kernel headers or if i need them)

I can not get the AIRO drivers from CISCO to build or install.(have tried with -id and -C -id, no go on either) I get many many error messages. Do I need to have the AIRO driver installed?

I used apt-get to install vpnc, if thats alright. It installed version 0.3.2

---

### Post by razialx on 2005-04-24
Please wait , Compiling driver modules using sources in /usr/src/linux
In file included from mpi350.c:32:
/usr/src/linux/include/linux/kernel.h:72: error: syntax error before "void"
In file included from /usr/src/linux/include/linux/capability.h:45,
                 from /usr/src/linux/include/linux/sched.h:7,
                 from /usr/src/linux/include/linux/module.h:10,
                 from mpi350.c:33:
/usr/src/linux/include/linux/spinlock.h:43: error: syntax error before "_spin_tr ylock"
/usr/src/linux/include/linux/spinlock.h:44: error: syntax error before "_write_t rylock"
/usr/src/linux/include/linux/spinlock.h:46: error: conflicting types for `fastca ll'
/usr/src/linux/include/linux/spinlock.h:44: error: previous declaration of `fast call'
/usr/src/linux/include/linux/spinlock.h:46: error: syntax error before "_spin_lo ck"
/usr/src/linux/include/linux/spinlock.h:47: error: syntax error before "_read_lo ck"
/usr/src/linux/include/linux/spinlock.h:48: error: syntax error before "_write_l ock"
/usr/src/linux/include/linux/spinlock.h:50: error: syntax error before "_spin_un lock"
/usr/src/linux/include/linux/spinlock.h:51: error: syntax error before "_read_un lock"
/usr/src/linux/include/linux/spinlock.h:52: error: syntax error before "_write_u nlock"
/usr/src/linux/include/linux/spinlock.h:54: error: conflicting types for `fastca ll'
/usr/src/linux/include/linux/spinlock.h:52: error: previous declaration of `fast call'
/usr/src/linux/include/linux/spinlock.h:54: error: syntax error before "_spin_lo ck_irqsave"
/usr/src/linux/include/linux/spinlock.h:55: error: syntax error before "_read_lo ck_irqsave"
/usr/src/linux/include/linux/spinlock.h:56: error: syntax error before "_write_l ock_irqsave"
/usr/src/linux/include/linux/spinlock.h:58: error: conflicting types for `fastca 

some of the errors, the top part.

---

### Post by razialx on 2005-04-25
bump

---

