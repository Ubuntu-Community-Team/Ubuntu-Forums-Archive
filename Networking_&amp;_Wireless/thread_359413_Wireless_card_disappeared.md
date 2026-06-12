---
title: "Wireless card disappeared"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by theRevMom on 2007-02-11
Previously, for 9 hours last night, finally got the laptop to see the wireless card (Netgear WG511v2)  -- see [http://www.ubuntuforums.org/showthread.php?t=344089&page=7](http://www.ubuntuforums.org/showthread.php?t=344089&page=7)

But then the system crashed.  When I was able to recover it, it no longer could see the wireless card.

I uninstalled everything and went through the whole process again at 
[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

But, there's nothing.  No lights. No recognition at all.

my iwconfig reads:
lo  no wireless extensions
eth0 no wireless extensions
sit0 no wireless extensions


My ifconfig reads the eth0 and the lo but nothing more.

the eth0 is built in.

I'm running a Dell lattitude C510

Prior to the crash, I had installed Network Manager.  I've since removed it.

I need two things:

First, I need help to figure out if the card is even working now. (No lights)

Second, if it is indeed working, I need help getting it recognized again.

---

### Post by theRevMom on 2007-02-12
I just ran dmesg 

there's a long list of repeated lines of
[17183497.XXXXXX] mrv8k: mrv8k-interrupt:eth1

then the last three lines are:
[17183497.888000] ACP: PCI interrupt for device 0000:07:00.0 disabled
[17183497.888000] mrv8k: mrv8k_initone: return -2
[17183497.888000]  mrv8k: probe of 0000:07:00.0 failed with error -2


ideas?

---

### Post by Floppyjoe on 2007-02-12
How do you feel about reinstalling the operating system and starting from scratch?

---

### Post by theRevMom on 2007-02-12
I can do that without any problem, but not tonight. I have to work early in the a.m.  
What does the error message indicate to you?

---

### Post by Floppyjoe on 2007-02-12
Off hand my guess is there is some problem with the driver for the card.
I can not explain why your computer would crash after installing a program.

---

### Post by theRevMom on 2007-02-12
The laptop has no means by which to back up the data he has on it (music, papers for school, photos from his photography class)... so I really can't do a complete rehash until he backs it onto his thumb drive.  I'll give that a try later in the week.

Thanks for all your help.

---

