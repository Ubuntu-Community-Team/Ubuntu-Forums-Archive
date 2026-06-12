---
title: "can not reenable wireless card"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by Cuogar on 2007-07-09
Hi everyone, I have a couple of problems.
Every time I try to switch from one network to another, when the networks overlap, my wireless card is disabled and I am unable to enable it without restarting my computer, I also get a weaker signal strength in Linux, never more then 60%, then I do in windows.
I have a Presario V2000 with a Broadcom 4318 Air Force One wireless card, I did not need to install nidswrapper to get my wireless card to work but I did have to find a driver for my enable/disable button on my laptop. 
Thanks everyone for the help.

---

### Post by kevdog on 2007-07-09
Rather than rebooting did you try:

sudo /etc/initd./dbus restart

As far as your broadcom card, these do not work out of the box with Ubuntu.  You had to install some drivers somewhere along the installation process.  Please post
lshw -C network
This will give us a clue about your wireless driver.

---

### Post by Cuogar on 2007-07-09
I'm afraid that the sudo /etc/init.d/dbus restart didn't work, thanks anyway.
as for the output I got 

Hardware Lister (lshw) - B.02.08.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.08.01)
 fallowed by some stuff telling me what formats and options can be.
Is this right? :?  I am only just starting ubuntu

---

### Post by Crenfinkle on 2007-09-16
try replacing initd./ with init.d for future reference

---

### Post by bhavin66 on 2008-01-11
Hi,

I have the same setup Presarion V2000 (V2570NR).
For some strange ****#$@@ reason i did press the wireless button and now I am stuck.
Cannot reenable the wireless.

Please help.


Restarted the notebook several times. Wireless light comes on but goes off after a few minutes.
After a day of waiting.....
Restarted the notebook and everything seems to be working.

---

