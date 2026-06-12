---
title: "Belkin F5D7050 on Ubuntu 7.04"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by chris.burns on 2008-02-05
Hi, 

I've noticed this topic has been covered quite frequently before but the information and solutions are heavily fragmented and appears to be confusing new users (like me) , hence the large number of posts. Despite the number of guides and How-To's it's not clear how to actually resolve this issue. 

I essentially cannot find the following information: 

**1) What chipset do I have? **
I simply cannot find a good way to determine the kind of chipset I have. Using the "lsusb" command I received an ID of 50:750 or somesuch. But this apparently does not help either in finding out the chipset.

**2) Is it possible to avoid downloading drivers?**
Several How-To's claim that because 7.10 resolves this issue that I can somehow update (?) Feisty to allow this as well. But  the commands do not work and it never even mentions chipsets. 

**3) Can I Get Linux Drivers or do I need Windows Wrapper Drivers?**
Some sites (perhaps older ones) recommend I download the Windows drivers from Belkin and then emulate (?) them on Ubuntu. But others suggest that I can use full Linux drivers. 

**4) Why is the USB bringing the system to a crawl?**
Whenever I plug in the USB it brings the entire system to it's knees. Stuttering the mouse and making booting impossible. Before I realized the USB was causing this I completely reinstalled Ubuntu trying to fix it. 

If Ubuntu wants to be a *replacement* operating system to Windows this situation can never happen. I'm a second year computer science major and this information is hard for me to follow. All the guides and information are fragmented in forum postings and never updated with new information. The ones that are updated are incomplete and assume skills and a comfort with UNIX commands that most users won't have.

---

### Post by raiwo on 2008-02-05
it's a belking USB dongle right? it uses zd1211rw 3-1:1.0: firmware version 4725 drivers & should work out of box, just plug it in!

---

