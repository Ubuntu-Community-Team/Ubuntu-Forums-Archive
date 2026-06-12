---
title: "Alfa AWUS036H"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by rashwan on 2008-08-24
Hello,
i bought Alfa AWUS036H yesterday and it works out of the box on ubuntu 8.04 with kernel 2.6.24-19-generic
then i installed aircrack-ng suit and patched the driver as shown here
[http://aircrack-ng.org/doku.php?id=r8187]("http://aircrack-ng.org/doku.php?id=r8187")
and the device worked well in monitor mode but when try to use the manage mode it sometimes give me NO SIGNAL at all and when i connect it drops connection after 1 minute 

```
lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000
```

```
:~$ lsmod | grep 8187
rtl8187                36096  0 
mac80211              165652  1 rtl8187
eeprom_93cx6            3200  1 rtl8187
usbcore               146028  4 rtl8187,ohci_hcd,ehci_hcd
```

now i want to use the manage mode how ? and how to switch without problems?? 
Thank you

---

### Post by Jackie999 on 2008-08-29
Did you ever get it working good in managed mode? I'm having same problem ...I tried lowering the 500mW txpower, but you can't in managed mode..unless I'm missing something? In WICD the connection is very erratic and often drops to 0%..
For me it's kind of a trade off..if I run ndiswrapper on my belkin usb rt2870 I freeze hourly (I can't get linux driver installed) and if I run the ALFA with native driver it drops ...can't win for loosing - but at least the freezing is gone...sigh....

---

### Post by rashwan on 2008-08-30
only yesterday with clean ubuntu installation it worked but after system updates it drops again , quick reboot and sudo apt-get install wicd .. solved for while but it came back drops connection
anyway its not aircrack-ng issue now its all about "Linux + kernel 2.6.24 + AWUS036H" as i tried 6 distros. till now they all did the same thing .. maybe kubuntu was about to work but as you well know its buggy hell! 
Also this Device working more than excellent on VISTA
any suggests  please

---

