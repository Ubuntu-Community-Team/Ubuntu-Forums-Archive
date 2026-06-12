---
title: "Problem with network after hibernation"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by standa on 2008-06-25
Hi,

I have 64-bit Ubuntu 8.04 on IBM Thinkpad x61s and I have the following problem:

I use a wired (ethernet) connection at home. I hibernate / close the laptop, and later try to connect at work (ethernet again, obviously a different connection) but I can't get connected otherwise than by restarting the computer! I tried 

/etc/init.d/networking restart

and

ifconfig eth0 down 
ifconfig eth0 up

and also

kill nm-applet

and start the nm-applet again but none of these worked.

Thanks for help!

Standa

---

### Post by xandr55 on 2008-08-12
I wish I could reply with something helpful, but rather just wish to report another version; my laptop fails to connect to any wired network after hibernation even one that it was just connected to. I have tried the same fixes as you as well as disabling and enabling networking from the gui, to no avail:(
Good luck though....

p.s. Dell Inspiron 5100, Hardy 8.04 (i 386), and despite many attempts at a fix, no wireless internet despite weeks of effort.

---

### Post by HDTimeshifter on 2008-11-07
My wired network connection won't reconnect after resuming from hibernate.  I'm running 64-bit Ubuntu 8.10 on an ASUS P5Q Pro motherboard with Atheros integrated NIC.  The Atheros NIC didn't work with 8.04 until I downloaded and recompiled the Atheros driver, but it worked right away with 8.10, so looks like they added support for it.  I don't know if the resume from hibernate network connection fail is a problem that's been around for a while or just with 8.10 (and 8.04) since I've only been running Ubuntu for 3 weeks since I built this PC and had it on continuously for the first 2 weeks for burn in with 8.04 and just turned on the hibernate feature a few days ago.  I've only noticed the problem 1 time since it's the first time I resumed from hibernate, and I had to reboot to get the network reconnected.  Also when I rebooted, the Ubuntu progress bar seemed to freeze up in a greenish tint that I've never seen before and I had to reboot again.

Edit:  I just fired it up today and the network reconnected.  I'll update in a few days to let you know if it's still a problem or not.

---

