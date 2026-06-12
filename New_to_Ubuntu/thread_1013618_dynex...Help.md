---
title: "dynex...Help"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by chicity on 2008-12-17
i am new to ubuntu i just installed it on my pc 4 days ago  
 so i recently purchased a dynex dx-bgdtc g wireless card (chip broadcom  bcm4318 ) wich i just cant get to work. i tried using ndiswrapper and installing the windows driver from the manufactuer cd-rom but had no luck.  any help will be greatly apreciated 
thank you in advanced

---

### Post by Tatty on 2008-12-17
Did you check to see if there are any drivers under System->Administration->Hardware Drivers?

---

### Post by chicity on 2008-12-17
yea i just checked and the driver that i "installed" using ndiswrapper is not shown there. am i missing something???
and i just noticed that when i click on the networkmanager the one at the top left the ath0 and wireless seem to be disabled or sumthing but that had to of just occured today.

---

### Post by xjcannonx on 2008-12-17
can you post the output of ```
sudo iwlist scanning
```

EDIT: and```
lspci
```

---

### Post by chicity on 2008-12-18
sergio@sdlpc:~$ sudo iwlist scanning
lo    Interface doesn't support scanning.


eth0    Interface doesn't support scanning.


wmaster0  Interface doesn't support scanning.


wlan0   Interface doesn't support scanning:Network is down


pan0    Interface doesn't support scanning.


sergio@sdlpc:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge:ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface:ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller 
(rev82)
00:14.1 IDE interface: ATI technologies Inc  IXP SB400 Ide Controller (
rev80)
00:14.2 Audio Device ATI technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge:ATI technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge:ATI technologies Inc
IXP SB4 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller:ATI technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet Controller:Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 Network Controller: Broadcom Corporation BCM4318 [Airforce One 54g]80.11g Wireless LAN Controler (rev 02)
02:04.0 Communication controller: Conexant System,Inc. HSF 56k Data/Fax Modem

sergio@sdlpc:~$

---

### Post by jrusso2 on 2008-12-18
Looks like its the famous broadcom brand chip

Broadcom Corporation BCM4318


[http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+Corporation+BCM4318](http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+Corporation+BCM4318)

---

### Post by chicity on 2008-12-19
Thank you very much for the link, i finally got it working!\\:D/

---

