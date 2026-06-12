---
title: "Aireplay-ng freezes"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by Alm4riC on 2008-09-17
A few days ago I installed Ubuntu 8.04 aka Hardy on my brand new HP laptop. Also an ipwraw driver for injection. I've a Intel 3945 wireless network card. Enfin, this is what i've done:

_Console 1:_
modprobe -r iwl3945
insmod /lib/modules/2.6.24-19-generic/ipwraw.ko
airodump-ng wifi0

_Console 2:_
Kismet opgestart

_Console 3:_
aireplay-ng -3 -b [MAC from AP] -h [MAC of client pc] wifi0

All of this is no problem, until aireplay "gets" the first ARP. Then Ubuntu freezes / hangs and nothing else is possible. I've tried this several times without any result. Now I don't know what to do. I searched Google but found nothing related to my problem...


Anyone? :)

---

### Post by Alm4riC on 2008-09-17
Caps Lock turns on when it freezes... Hmm?

---

### Post by ichundu on 2008-09-17
i have similar problem too with my desktop computer. i use a wireless usb adapter. there is something wrong with ubuntu about this, it doesn't happen in windows (the freezing issue and that caps lock pulse). don't know what it is, i can only hope some one tells us what's wrong with it... :mad:

---

### Post by lswb on 2008-09-17
Not sure if this is the problem, but if you insmod a module dependencies are not necessarily loaded. I believe with the ipwraw.ko module in the directory you've placed it you can load it with modprobe but run "sudo depmod" first, which will rebuild module dependencies. Then see if you can "sudo modprobe ipwraw" to load it.

If no luck with modprobe, you can run the command "modinfo ipwraw.ko" which should list any dependencies along with other information.

---

### Post by Alm4riC on 2008-09-18
> **lswb said:**
> Not sure if this is the problem, but if you insmod a module dependencies are not necessarily loaded. I believe with the ipwraw.ko module in the directory you've placed it you can load it with modprobe but run "sudo depmod" first, which will rebuild module dependencies. Then see if you can "sudo modprobe ipwraw" to load it.

If no luck with modprobe, you can run the command "modinfo ipwraw.ko" which should list any dependencies along with other information. 

Thank you, I'll try this when I'm home :)

---

### Post by Alm4riC on 2008-09-18
Hmm, now I get an error after trying what user lswb said:

insmod: error inserting '/lib/modules2.6.24-19-generic/ipwraw.ko': -1 File exists

After a reboot no difference....

---

### Post by lswb on 2008-09-18
The error is indicating that the module is already loaded. Did you "modprobe ipwraw" before "insmod /lib/modues..." ? If so it appears that modprobe loaded it successfully. Trying to load it again with insmod is causing the error message. (You can list loaded modules with the "lsmod" command, filter through grep to search for a certain one, like "lsmod|grep ipwraw"

---

### Post by Alm4riC on 2008-09-18
> **lswb said:**
> The error is indicating that the module is already loaded. Did you "modprobe ipwraw" before "insmod /lib/modues..." ? If so it appears that modprobe loaded it successfully. Trying to load it again with insmod is causing the error message. (You can list loaded modules with the "lsmod" command, filter through grep to search for a certain one, like "lsmod|grep ipwraw"

Yeah i know, but i forgot something to tell: when ipwraw is loaded, i want to start "airodump-ng wifi0". But i get the message:

Interface wifi0:
ioctl(SIOCGIFINDEX) failed: No such device

EDIT: yes, i "modprobe ipwraw" before "insmod /lib/modules...". But this has to reset when i'm rebooting?

---

### Post by lswb on 2008-09-18
It is only necessary to modprobe the module OR to load it with insmod, not both operations.

Apparently a few more steps are necessary for injection and monitor mode to work using this module. Here is a site I found with google by searching for "ipwraw interface aircrack" that might help:
[http://thew0rd.com/2008/08/19/tutorial-cracking-wep-using-backtrack-3/](http://thew0rd.com/2008/08/19/tutorial-cracking-wep-using-backtrack-3/)
It is not for ubuntu but most of it should be applicable. Take a good luck at the various ifconfig and start and stop commands. You can probably refine the search terms and find something more ubuntu-specific.

---

### Post by Alm4riC on 2008-09-18
> **lswb said:**
> It is only necessary to modprobe the module OR to load it with insmod, not both operations.

Apparently a few more steps are necessary for injection and monitor mode to work using this module. Here is a site I found with google by searching for "ipwraw interface aircrack" that might help:
[http://thew0rd.com/2008/08/19/tutorial-cracking-wep-using-backtrack-3/](http://thew0rd.com/2008/08/19/tutorial-cracking-wep-using-backtrack-3/)
It is not for ubuntu but most of it should be applicable. Take a good luck at the various ifconfig and start and stop commands. You can probably refine the search terms and find something more ubuntu-specific.

Thank you, good site!

"Take note of your wireless adapter&#8217;s interface name. Then stop the adapter by issuing: airmon-ng stop [device]"

I don't see any adaptor with the command iwconfig, only "lo" and "eht0", but not my "wifi0" (as yesterday).


This is new to me so please forgive any stupid questions (or bad English) :P

---

### Post by dublued on 2008-11-05
hey sorry to raise this from the dead.  did you ever resolve why it was freezing?  i'm having a similar issue and cannot figure it out

thanks

---

