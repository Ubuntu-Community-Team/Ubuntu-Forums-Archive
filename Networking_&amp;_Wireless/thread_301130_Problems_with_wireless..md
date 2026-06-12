---
title: "Problems with wireless."
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by Termajin on 2006-11-16
Eth1 IEEE 802.11b/g ESSID: " " Nickname: "Broadcom 4306"
     Mode: Managed Frequency=2.437 Ghz Access Point: Invalid
     RTS the: off Fragment thr: off
     Link Quality:0 Signal level:0 Noise level:0
     Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
     Tx excessive retries:0 invalid misc:0 Missed Beacon:0

I'm usind a Dell inspiron 5100 and a Linksys WRT54G. 

Any suggestions?

If you need any more info please tell me. I'm new to linux and I'm not sure what I should post.

---

### Post by Ashrael on 2006-11-16
First connect with cable to router, check if your router is using channel 12 or 13, if it does...set it to 7  or so...some wifi chips can't handle anything above 11...also check if your router has some mac adres list, if it does disable it for now...Check SYSTEM>NETWORKING and SYSTEM NETWORK TOOLS...See your WLAN adapter there? Is it set to DHCP? Well try this and give me some more info.....



ashrael

---

### Post by DavidTangye on 2006-11-16
I found that the best info on this topic, that got me up and going was in these forum threads:
 - [http://www.ubuntuforums.org/showthread.php?t=202834&highlight=8B2A](http://www.ubuntuforums.org/showthread.php?t=202834&highlight=8B2A)
 - [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by Termajin on 2006-11-17
So I tried this one.

- [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

and now I don't have a wireless option under system/administration/networking.

Wired and Modem is still there.

---

### Post by DavidTangye on 2006-11-17
> **Termajin said:**
> So I tried this one.

- [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

and now I don't have a wireless option under system/administration/networking.

Wired and Modem is still there.

That thread is very big, so I guess I should have specified which messages in it that were of particular use. 

I did not use any GUI to set up wireless, mainly because I wanted WPA encryption, and they do not seem to be able to set it up. One GUI does WEP I think, but that is old stuff that I did not want.

From memory, I did this:
[LIST=1]
[*]Read all the messages in those two threads
[*]Downloaded the link [http://compwiz18.blackhole.cx/bcm4318/get.php?file=bcm4318.all.tar.gz](http://compwiz18.blackhole.cx/bcm4318/get.php?file=bcm4318.all.tar.gz) which was on the first page of [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102). This is to a tarball that you unpack and run the unpacked script. It sets up almost all of the wireless config for you.
[*]As per the section *Sample configuration WPA1 & DHCP, ESSID broadcast enabled* in the thread [http://www.ubuntuforums.org/showthread.php?t=202834&highlight=8B2A](http://www.ubuntuforums.org/showthread.php?t=202834&highlight=8B2A), I
[LIST=1]
[*]I edited /etc/network/interfaces, and 
[*]I installed wpa-supplicant to use to create a WPA-PSK (pre-shared key), and cut and pasted this into /etc/network/interfaces.[/LIST]
[*]Then did something like
[LIST]
[*]sudo bash -c 'echo "ifdown wlan0" >/etc/init.d/Wlan0Down && ln -s ../init.d/Wlan0Down /etc/rcS.d/S40networkWLan0Down'
[/LIST]so the wireless would be setup properly to then start up properly by the subsequent init task, S40networking
[/LIST]

I suppose I had better update the wiki to reflect this.

---

