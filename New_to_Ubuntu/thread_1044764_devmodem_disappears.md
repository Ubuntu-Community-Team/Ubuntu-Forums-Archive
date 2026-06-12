---
title: "dev/modem disappears"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Rhys12 on 2009-01-19
I am new to Ubuntu. My daughter gave me a new hard drive for Christmas, so I migrated Windows XP over, then partitioned the hard drive and installed Ubuntu 8.04 to make a dual-boot machine.

The computer has a Softmodem with a Conexant chip. It worked fine under XP and still does. After about 14 hours of research and work, I got the linux driver installed under Ubuntu and got it to recognize the modem and log on.

The problem is that every time I shut down and reboot I have to run hsfconfig over, as it loses dev/modem. I found little under Ubuntu on this problem, but did find a reference to it on another linux forum, ([https://www.linuxquestions.org/questions/mandriva-30/devmodem-disappears-on-reboot-259908/]("https://www.linuxquestions.org/questions/mandriva-30/devmodem-disappears-on-reboot-259908/")). 

According to that, the problem occurs because the the program attempts to install the driver too early in the boot process, and it seems to occur with several varieties of Linux. Some work-arounds were offered, but none of them seems to work on Ubuntu.

Anyone have any solutions to this problem? How would you modify the boot process to move loading the modem driver to the end? It isn't much of a problem for me to run hsfconfig every time, but other people use the machine, like my 6 yr. old grandson.

---

### Post by Rhys12 on 2009-01-23
Never did get a solution, but I solved the problem by installing Gnome-ppp. It couldn't find dev/modem either, but when I clicked on "detect modem" it found it and doesn't lose the information each bootup so now all I have to do is click on "connect".

---

