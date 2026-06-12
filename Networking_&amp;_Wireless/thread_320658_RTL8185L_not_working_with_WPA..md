---
title: "RTL8185L not working with WPA."
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by lipin on 2006-12-17
Hello
I've got LanTech WL54G-PCI wireless card with realtek rt8185l chipset on board. and I'm using Xubuntu 6.10. When I'm trying connect to unsecured network everything works fine but my network is secured with 64bit WPA key. Sometimes its connect to this network successfully (very rarely) but its works for seconds (3 pings aprox) and then stops. Once it was almost fine i had a got bitrate about 200-250 kB/s (as it should be) but web pages were loading very slowly. I suppose that there are some problems with uploading. I couldn't find out what is wrong so i simply surf on internet and read that there is possibility of using ndisdrivers. But my drivers won't work with ndiswapper-18. Modprobe gives me such a lot of text here is the ending:

Message from syslogd@ubuntutk at Sun Dec 17 22:09:43 2006 ...
ubuntutk kernel: [17179740.760000]  <e0b57095> wrapper_init+0x95/0x137 [ndiswrapper]  <c0130230> sys_init_module+0x140/0x1640

Message from syslogd@ubuntutk at Sun Dec 17 22:09:44 2006 ...
ubuntutk kernel: [17179740.760000]  <c0102dbb> sysenter_past_esp+0x54/0x79 

Message from syslogd@ubuntutk at Sun Dec 17 22:09:44 2006 ...
ubuntutk kernel: [17179740.760000] Code: 00 00 00 c7 45 f4 00 00 00 00 21 e2 8b 02 c7 45 ec a0 5d 11 c0 c7 45 e4 01 00 00 00 89 45 e8 8d 46 04 8b 58 04 89 45 f0 89 48 04 <89> 0b 89 5d f4 89 d3 8d 76 00 8b 03 c7 00 02 00 00 00 fb e8 42 

Message from syslogd@ubuntutk at Sun Dec 17 22:09:44 2006 ...
ubuntutk kernel: [17179740.760000] EIP: [wait_for_completion+102/176] wait_for_completion+0x66/0xb0 SS:ESP 0068:c9ff3e6c

I can't install linux drivers from realtek website because i don't have any compiler in xubuntu pre installed. I there any package with this driver exists ?.  Naturally in windows XP everything works fine. Maybe another information that i can give is when i'm using netstumbler under windows its shows that my network uses multiple AP. And i have got good signal only on one, sometimes windows jumps to another ap with lower signal but in general works fine.

I hope so that my English was good enough to explain all aspects. :)

Thanks in advance
Tomasz Lipinski (Lipin)

---

### Post by n00b@linux on 2006-12-18
There is already a linux driver for the RT8185L chipset, r8180.o:
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#RealTek80211g](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#RealTek80211g)
(see section 4.10 of that page and note the driver name).
I take it that```
sudo modprobe r8180
```does not work, ie. the driver is not present on your install.
I do not, however, know where you can get a binary of r8180.o :(
 
Alternatively, you could try ndiswrapper again.  One guy got it to work by passing a different device ID to ndiswrapper.  See Section B11 of this page:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

---

### Post by lipin on 2006-12-18
Yes I am currently using that driver but is not working with WEP protection. (Sorry for topic my mistake should be WEP instead of WPA). Simply (after browsing internet resources) it looks that i have got no choice and i have to stay in windows xp :-(.  It was a short linux story as always it is, yeah it looks that product is not mature enough nowadays, as well as it was about 4 years ago (my first contact with linux).

Greetings

---

### Post by n00b@linux on 2006-12-18
I can understand your frustration. I spent the first 6 months of my linux experience banging my head against a wall trying to get things working. That was 12 months ago. Since then I've gotten more skilled and can configure a system quite well by myself. You just have to have the time and patience to learn it and not everyone has that. That's not a bad thing by any means. You just have to be ready to invest the time needed to learn how to do things differently from the way that Windoze has taught you to do them.
 
I've got my wireless connection working and there's no reason why you can't. You just gotta have the time and be patient. Configuring wireless in linux is a rite of passage.
 
Alternatively, you could just take a look at the wireless cards that work 'out of the box' on Ubuntu and go out an buy one of those to replace your LanTech WL54G-PCI. Have a look at the documentation and follow the links :-D :
[https://help.ubuntu.com/community/NetworkDevices](https://help.ubuntu.com/community/NetworkDevices)

---

### Post by lipin on 2006-12-30
Before this 2007 year i had to make decision and i finally staying with linux installed under windows xp :-) and now xubuntu works fine. Who knows maybe I will play music from linux on New Year party i my flat. 2007 Year of the Linux (at least on my computer). 

Greetings
Lipin

---

