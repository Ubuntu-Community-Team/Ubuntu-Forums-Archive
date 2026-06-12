---
title: "Wireless Troubles"
date: 2006-09-25
forum: Networking &amp; Wireless
---

### Post by opensourcerocks on 2006-09-25
Hi, 
I just installed Ubuntu into a older machine.
The only problem is that I can not connect into my wireless network. I put in ndiswrapper from a .deb file and installed my Linksys WUSB54G device. Ndiswrapper has told me that the hardware and the driver is present. Now the only problem is that I can not connect into my router. I have tried useing the Network connection tool with no luck. 
So here are the settings on my router:
WPA encryption
ASE? code
Numeric code 
Also I believe all router settings are correct. 

On the computer:
ESSID entered right
ASE|| selected
Numeric encryption code right
Auto DNS

Any help would be great
Thanks

Also I have had this wireless network thru SUSE linux before and Ubuntu once showed the networks in the area. (but not now:-k ) There is also no other way to connect it to the internet.

---

### Post by blabla on 2006-09-26
first thing I'd do is remove all encryption and see whether you can connect - if you can you know the encryption is at fault

---

### Post by opensourcerocks on 2006-09-26
I don't really want to do that because there are about 7-8 different wireless networks in the area. Since my network has work computers on it, I do not want to put them in risk

---

### Post by opensourcerocks on 2006-09-26
Do you think that turning off security is what I really need to do, to make this work.:confused: :-k

---

### Post by sharkcohen on 2006-09-26
Turning off security is what you will need to do to properly troubleshoot the problem.  You need to know if you are able to connect at all before you can go from there.

---

### Post by an.echte.trilingue on 2006-11-09
> **opensourcerocks said:**
> Do you think that turning off security is what I really need to do, to make this work.:confused: :-k

Depending on the nature of where you are at qnd what is on the computers on your network, turning off encryption for 10 minutes to troubleshoot is not going to hurt you.

---

### Post by wieman01 on 2006-11-09
You definitely need to turn off encryption to troubleshoot. Otherwise your system turns into a moving target, believe me. These links will help you.

**WUSB54G (post #20): **[http://www.ubuntuforums.org/showthread.php?p=1711070#post1711070]("http://www.ubuntuforums.org/showthread.php?p=1711070#post1711070")
**WPA2, WPA1 encryption: **[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

_**EDIT:**_
Since you don't have internet connection yet, you can install "ndiwrapper" by doing this from command line:
> sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils ndisgtk

---

