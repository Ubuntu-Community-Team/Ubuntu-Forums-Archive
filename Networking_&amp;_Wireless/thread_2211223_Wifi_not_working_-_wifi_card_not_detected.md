---
title: "Wifi not working - wifi card not detected"
date: 2014-03-14
forum: Networking &amp; Wireless
---

### Post by sebastien_vigneau on 2014-03-14
Hi,

I have Ubuntu and Windows in double boot, and the wifi stopped working on both. On Ubuntu, I get the following:
 > $ sudo lshw -C network
 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: e0:db:55:d7:ee:24
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=10.0.0.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff

My understanding is that I should see another device for wifi in addition to the Ethernet interface. Because it is not there, the wireless card may be broken and I may have to replace it - or is there another possibility?

Thank you in advance for your help!

Sébastien

---

### Post by wildmanne39 on 2014-03-14
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by sebastien_vigneau on 2014-03-14
Thanks for your quick reply! Here is the wireless-info.txt file:

[ATTACH]251160[/ATTACH]

---

### Post by wildmanne39 on 2014-03-14
Your wireless card does not show up you were correct.

1. It could have failed.
2. It may have came unsetted.
3. Sometimes it will help to reset your bios and take your battery out and leave it unplugged for about 30 minutes.

If you have the EUFI bios, do not try to reset it.

---

### Post by sebastien_vigneau on 2014-03-15
Thanks for your reply!

I do have UEFI bio, so I will not try to reset it. But I will check the connection and, if this doesn't help, get a new card...

---

### Post by sebastien_vigneau on 2014-03-15
So it seems it was the connection to the wireless card. I unplugged and replugged the antenna cables, as shown in this [video]("http://www.youtube.com/watch?v=TXXxFD07Yyc&feature=share&list=PLRYYiiavCslJHJuypdIkbHQ4C58UIE8m2&index=10"), and it works again.

Thanks again for your help!

---

### Post by wildmanne39 on 2014-03-15
Glad it is working!!!

---

### Post by raulcb on 2014-04-28
Hello,
I have the same problem, how can I know if the card is broken? It is not recognized even in a usb boot... but it was working until yesterday, suddenly after a update and reboot recognized but non working, and after another reboot not present. Thanks in advance!!
 [ATTACH]252596[/ATTACH]

---

