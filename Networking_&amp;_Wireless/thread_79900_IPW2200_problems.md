---
title: "IPW2200 problems"
date: 2005-10-21
forum: Networking &amp; Wireless
---

### Post by usrk1 on 2005-10-21
Hi,

I'm a noob to Ubuntu and have problems getting my IPW2200 wireless card to work. I have gone through the recent thread and tried everything mentioned. I've spent 4 hours on it and given up. Kindly help.

Here is some more info:

- Installed Breezy Badger 5.10 today as a dual boot on a Dell Inspiron 6000. Everything but the wireless card seems to work.

- The wireles card works fine on the dual booting Windows XP system.

- Chose the non wireless card during install and plugged in my ethernet cable. This worked fine. During install, the network config phase failed with the wireless card twice, but I tried over and over again and it succeeded once. I had to redo the install however because of other partition related issues, and when I ran through the install again, decided to configure wireless later.

- dmesg shows: Detected ipw2200 Intel PRO/Wireless 2200BG

- The wireless card is on eth1. I commmented out all references to eth0 in /etc/network/interfaces. Verified the SSID and WEP key have no typos.

- I did the steps suggested by xMetaRidley:
[INDENT]sudo gedit /etc/modprobe.d/ipw2200[/INDENT]
[INDENT](added the line options ipw2200 hwcrypto=0)[/INDENT]
[INDENT]sudo modprobe -r ipw2200[/INDENT]
[INDENT]sudo modprobe ipw2200 hwcrypto=0 [/INDENT]
and rebooted.

- iwlist scan shows (for eth1) correct ESSID and Channel. Quality is 99/100 and Signal level is -21 dBm

- I ran ifup --force eth1 and noticed DHCPDISCOVER messages being sent but no DHCPOFFERS.

- Under gnome, my network connection icon has a warning sign on it. If I open it, the connection properties seem to only indicate eth0 (which is disconnected) and lo.

Thanks for any and all help!

---

### Post by pau on 2005-10-21
Hi,

I have bad news for you

Read this

[http://ubuntuforums.org/showthread.php?t=78983](http://ubuntuforums.org/showthread.php?t=78983)

And also this

[http://www.aei.mpg.de/~pau/amilo_1425_linux_en.html](http://www.aei.mpg.de/~pau/amilo_1425_linux_en.html)

This is a guide for a FSC that has the same card. I only got this to work ONCE with an installation of the 2.6.13 kernel per hand and yet the communication was breaking every 20 minutes. Still, you can give it a try.

Somebody told me to install madwifi, because he had an ibm with the same chipset... Well I did, following the guide 

[http://ubuntuforums.org/showthread.php?t=75451](http://ubuntuforums.org/showthread.php?t=75451)

But I ended up with something very odd... I cannot figure out HOW, but this affected my bios!! Everything was screwed up, no cpu stepfreq supported any more, no suspend, the highest cpu speed was 600 etc etc etc 
When I deleted the package everything went back to normality...

---

### Post by ibanez88 on 2005-10-21
I was having the same problem until I found this thread:

[http://ubuntuforums.org/archive/index.php/t-282.html](http://ubuntuforums.org/archive/index.php/t-282.html)

basically, don't use a GUI wifi-manager.  Not wifi-radar, not kwifi, I'm not sure about any of the Gnome tools.   Edit your interfaces file by hand per the link.  

The gist is that you have to specify "restricted" when you enter your key.  This will let you connect to hidden networks, etc.

---

### Post by cbudden on 2005-10-21
Mine worked straight off! (Acer machine tho)

---

### Post by usrk1 on 2005-10-21
Thanks for the replies, everyone.

After most of a day of struggling, I got the card to work. I didn't do anything different from what was mentioned in my first post. The card just started working after some time (something like 15 minutes) following my last boot. The last change I made was to comment out the hotplug section in the /etc/network/interfaces file. I basically commented out all references to eth0 (the regular, non wireless network card) in the file.

I've rebooted and hibernated a few times since and thankfully hadn't had a problem.

Overall, my Ubuntu install experience has been very good. I struggled some with the partitioning to dual boot and some with this wireless card. Otherwise everyhting worked out of the box. I never saw Gnome before and it rocks. With all the great firefox extensions and the spiffy desktop, there is no going back to Windoze.

---

### Post by matthew on 2005-10-21
Read through the first post in [this thread]("http://ubuntuforums.org/showthread.php?t=26623"). It has worked for me twice, once under Hoary and now with Breezy. I am using the same card (ipw2200) and I was also able to use WPA encryption. If you don't want WPA you can just follow the first half of the howto to get your ipw2200 working right.

[http://ubuntuforums.org/showthread.php?t=26623]("http://ubuntuforums.org/showthread.php?t=26623")

---

