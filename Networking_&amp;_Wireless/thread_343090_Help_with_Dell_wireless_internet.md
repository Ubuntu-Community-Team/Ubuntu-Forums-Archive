---
title: "Help with Dell wireless internet"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by coyoteboi on 2007-01-20
Hi, I just installed ubuntu and everything looks great, much better than Windows.  Only problem is I cant get my internet adapter to work.  Any ideas on how to get a driver installed or something??  Its a dell inspiron 2200 with a WLAN miniPCI card.  I have a windows driver but it wont work with ubuntu.

---

### Post by mssever on 2007-01-21
What wireless chipset do you have? You can find out by typing ```
lshw -class network | less
``` (press q to exit the viewer)

Search the forums (and maybe Google, too) for your specific card. You can try to use NDISWrapper with your Windows driver. Searching the forums should get you info.

Unfortunately, I can't tell you more without more info.

EDIT: By the way, Windows software usually doesn't work in Linux. In those rare cases where it does (NDISWrapper sometimes, wine sometimes), consider it a bonus.

---

### Post by coyoteboi on 2007-01-22
Sorry i didnt reply sooner, my internet was out all day yesterday.  I did what you said and this is what it says.  

Network:0 DISABLED
Wireless Interface:
BCM4318 [Airforce One 54g] 802.11g Wireless LAN controller
vendor:  Broadcom Corporation

Network:1
Ethernet Interface:
82562ET/EZ/GT/GZ  -  PRO/100  VE  (LOM)  Ethernet Controller Mobile
vendor:  Intel Corporation


Hope this helps!

---

### Post by coyoteboi on 2007-01-24
Anybody have any ideas??  Hope to hear from someone soon!!

---

### Post by spd106 on 2007-01-25
Try starting here [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

