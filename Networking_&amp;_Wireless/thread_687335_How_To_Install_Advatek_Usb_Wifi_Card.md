---
title: "How To Install Advatek Usb Wifi Card"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by roverman on 2008-02-04
Well hello to anyone that can help, i install kubuntu on my toshiba satellite 1000 but ai already had a usb wirelles card from advantek network the exact model is AWN-USB-54M, i don´t have any experience installing devices on kubuntu but i´ll be glad if anyone can help, and if you do please give a step by step instructions to do it.......:) cause i have no idea where to start

---

### Post by jan quark on 2008-02-04
pls post the result of the terminal command 

```
lspci
```

thank you

---

### Post by roverman on 2008-02-05
hello jan quark, here it is what you asked me to do 

0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
0000:00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:02:04.0 CardBus bridge: Texas Instruments PCI1420
0000:02:04.1 CardBus bridge: Texas Instruments PCI1420

---

### Post by jan quark on 2008-02-05
pls post the result of 

```
lsusb
```

I am searching right now if your usb wireless card is supported by ubuntu

check please if there are some drivers inactive in 
>system > administration > restricted drivers manager

---

### Post by roverman on 2008-02-05
This is the result for lsusb:

Bus 002 Device 003: ID 054c:0243 Sony Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0d62:a100 Darfon Electronics Corp. Benq Mouse
Bus 001 Device 002: ID 0457:0163 Silicon Integrated Systems Corp.
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000

i guess that the first one is the pen driver that i am using to bring the reports to my pc
the third one obviously my mouse
and the fourth must be the detachable DVDROM Unit the rest i am not sure

---

### Post by jan quark on 2008-02-05
#
Card: Advantek awn-usb-54m

    *
      Chipset: sis163u Silicon Integrated Systems Corp
    *
      USBID: 0457:0163
    *
      Driver: [http://www.mejorenlinea.com/drivers/advantek-awn-usb-54m.tar.gz](http://www.mejorenlinea.com/drivers/advantek-awn-usb-54m.tar.gz) 
    *
      

I guess you have to use the [ndiswrapper method]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") but I cant find the windows drivers right now


I cant find your usb device here
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

