---
title: "Which Wireless card to buy for 14:04 64bit?"
date: 2014-05-01
forum: Networking &amp; Wireless
---

### Post by Langney on 2014-05-01
Hi there. I have a new machine which I got recently but the trouble I'm having Is deciding which Wireless card to get as the one I am currently using for Windows has some major flaws like saying It's connected but Isn't. I have tried various different cards and USB devices (Wireless) to which nothing seems to be working so my question Is which one to buy. Highest compatability and so on. I will post my computer details down to give you an Idea of what i haver to work with, Any support would be great. 

Cheers 

```
System Manufacturer: Gigabyte Technology Co., Ltd.
       System Model: GA-770TA-UD3
               BIOS: Award Modular BIOS v6.00PG
          Processor: AMD Phenom(tm) II X4 925 Processor (4 CPUs), ~2.8GHz
             Memory: 8192MB RAM
Available OS Memory: 8190MB RAM
          Page File: 1762MB used, 14616MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 11
DX Setup Parameters: Not found
   User DPI Setting: Using System DPI
 System DPI Setting: 96 DPI (100 percent)
    DWM DPI Scaling: Disabled
     DxDiag Version: 6.01.7601.17514 32bit Unicode

```

---

### Post by squakie on 2014-05-01
I have had great luck with Tenda W322U ver 2. USB wireless adapters.  They will do 300mbs and they work "out of the box" with Ubuntu.  Since you've tried several,  I have to ask if you've clicked on the network manager icon and checked if wireless is enabled.  If needs to be checked to enable any wireless.  Any available wireless networks would then show there.

For your existing system we would need to know the actual wireless device, not the specs you posted.  If it's an internal wireless card:

lspci | grep Network

If it's a USB device (any you could post this for each USB device you've tried):

lsusb

Post the output(s) back in a reply here and enclode them in code tags.

---

