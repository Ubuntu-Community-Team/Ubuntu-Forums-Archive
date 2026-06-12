---
title: "Upgraded to Fiesty, Now Random Network Failure"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by leonatkinson on 2007-04-24
I upgraded to Fiesty yesterday.  Everything seemed OK, but I started noticing that some Web sites wouldn't finish loading.  I thought it could be network slowness but it hasn't gone away.  Regardless of Web browser, I cannot get [www.networksolutions.com]("http://www.networksolutions.com/") to come up.  Some data comes through, but it eventually times out.  However, if I connect from inside VMWare/Windows 2K/MSIE, I get through with no problem.

I get the same behavior in my laptop, while I'm at work. When I take my laptop home, it's fine.  Both machines were fine prior to upgrading.  So far, I haven't found any non-HTTP network services that are failing.

It's not a DNS issue.  I can resolve names fine.  I've watched the packets in WireShark.

I've looked at this being an issue with the Marvell network hardware.  It seems like the instructions for swapping in the proprietary drivers from Marvell were from Breezy days and aren't quite relevant to Feisty.  Also, since the laptop is running different hardware, it seems unlikely to be skge and tg3.  

I feel like I'm out of ideas after spending all day on this.  Well, I have one idea that I don't like--start over and switch back to Edgy.

Does anyone have any suggestions?

Thanks,
Leon

---

### Post by leonatkinson on 2007-04-24
A bit more of hopefully relevant information.

The office is connecting out to the T1s through a Linksys RV082 (Firmware version :    1.3.3.5 (Aug 9 2006 00:40:14)).  If I put my laptop on our backup service (a cable modem from comcast), it works.  So, it does seem to point to the router or the bonded T1s from SpeakEasy.

Also, from inside the LAN, I cannot connect to the admin panel of the router, unless I go though Win2K running on VMWare.

---

### Post by leonatkinson on 2007-04-25
I solved this...or rather, someone who works for me did.  The short story is that the router is misbehaving and the new kernel that came with Feisty isn't tolerant.  This is what I did.

[FONT="Fixedsys"]sudo vi /etc/sysctl.conf [/FONT]

Added the following lines to the end of the file.

[FONT="Fixedsys"]net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760 [/FONT]

Saved the file and did the following.

[FONT="Fixedsys"]sudo sysctl -p[/FONT]


That fixed the problem immediately.

There's more information here: [http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/]("http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/")

---

### Post by tanderson on 2008-01-10
OMG! Thank you so much for this!! Community rules!!!!

---

