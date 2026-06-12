---
title: "Thin Client"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by betete on 2008-02-14
Hello, I'm new in the Linux world and I have a question. I have two computers, one of them is a P4 HT 3.0Ghz with 1Gb of RAM, the second one is an old P586 with 32Mb of RAM. I installed Damn Small Linux in the old one and it runs nice, but there are some applications that would be very helpful, like Open Office, that  cannot run on that machine.
The other computer is running Ubuntu 7.04 and I also have Windows XP for some applications that I need.
My question is: is there any way that I can use the new computer as a server to run heavy applications from the old computer? For example, can I have Open Office or Firefox in the old computer but running in the new one?
I have read about thin clients and NoMachine software, would that work in my case.

Thanks

---

### Post by luvinit on 2008-02-16
Hi,
 Yes it is possible to do that I don't know what the minimum required spec would be but I find that my thin client runs quicker as a thin client than as a standalone pc. Most of the ones I see advertised have at least 64 mb ram. Be warned that there is not much material about setting up such a server but the quick install guide works well for many people.


[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

---

### Post by betete on 2008-02-17
Thank you very much luvinit. The iformation you gave is very useful. But I still have a doubt, when runnig a LTSP server, is it necessary for the client to boot from the network or can it boot from the local hard drive? What I really want is to run just some applications remotely but not the hole operating system. I think that the concept that applies here is a Remote Desktop.

---

### Post by luvinit on 2008-02-17
I don't know anything about running a "fat client", which I believe is the term for when you are using the resources of the client e.g. extra ram in combination with the boot from the server. The only two things I know of are having a pc with its own os on the hard rive, just connected to a server for internet connection and sharing of files/directories, or a thin client with everything on the server. My client is exactly that. It has Dreamlinux on it, among others, which runs nicely on the 256mb of ram on it, but so far I am enjoying the performance as a thin client more. Sorry I can't be any more help, but it is an area which is short on information in the Ubuntu and Linux in general.

---

### Post by LinuxNtwrkng on 2008-02-17
What you are looking for is remote X.  Your old computer will run it's own OS and it's own X server.  Your new computer will serve the applications.  The applications will run on the new computer, but be displayed on the old computer's terminal.

[http://www.quietearth.us/articles/2006/08/24/Ubuntu-Enabling-remote-Xwindows](http://www.quietearth.us/articles/2006/08/24/Ubuntu-Enabling-remote-Xwindows)

That should get you started.  If you have any more questions after reading that site, then come back and ask us.

---

### Post by betete on 2008-02-18
Hello again, thank you all for your support. Finally I could make NX server work and it's better than I imagined. So I run some applications, like xmms, localy and others like Open Office from the server.
I can tell you that the results are amazing considering that my old computer is just a Pentium I 586 and has only 32Mb of RAM.

---

### Post by betete on 2008-04-06
Hello again. This time I need your help to do something slighly different, but the same concept. I want to run a remote desktop. I have been using NX server in Ubuntu and it works great. What I want now is to install Ubuntu in a virtual machine using VMware, which I have already done, and connect to it usin NX client from a computer physically connected to the Host (Windows XP). Could you help me setting up the network?

---

