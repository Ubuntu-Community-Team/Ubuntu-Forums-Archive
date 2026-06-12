---
title: "Problems with wireless connection on HP Pavilion dv6000"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by anpu1 on 2008-05-19
Hi everyone!

I have a problem with my wireless connection. Here is the description:

when i start the computer everything is perfect and ubuntu 7.10 strast quickly and the wireless connection works perfect. but when I'm doing some other things and not using the computer (the comp turns off the screen, HDD is runing) the wireless connection is not working but the light on the wireless button is still blue (that means it is connected). 

I knoe that there is not anything wrong with the router because I can stay online with other computer (IBM ThinkPad, windows OS) till the battery is dead!

Pleas any help would appriciate!
ANPU

(sorry for mistakes in english)

---

### Post by DizzyTech on 2008-05-19
Two things:

1:  You might want to upgrade to Ubuntu Hardy, it's much better for HP hardware support.

2:  The blue light on the HP dv6000 does not mean it's connected.  The light is blue when the wireless driver is loaded (e.g., the computer knows the card is there and is talking with it) and orange all other times.

---

### Post by Ayuthia on 2008-05-19
It sounds like you are using the Nvidia drivers.  There is a bug in the Nvidia drivers that causes the screen to not come back so easily.  The only work-around that I know is to press ctrl-alt-F6 then ctrl-alt-F7 a few times and the screen will return.  

As far as I know there are no fixes for it yet.

---

### Post by Ayuthia on 2008-05-19
> **DizzyTech said:**
> Two things:

1:  You might want to upgrade to Ubuntu Hardy, it's much better for HP hardware support.
The driver is still not fixed in Hardy.

---

### Post by anpu1 on 2008-05-19
I already had Hardy on this computer but the computer was f**** up! Hardy was slow and useless on HP. so I wenr beck to Gutsy! its working faster and its more stable!!

Ayuthia the problem is not in screen! and the drivers are right! the problem is when i want to use internet it doesn't connect back!!

ok about the blue LED sory! i tought that its blue when its connected :)

maybe anyone knows what program to use for wireless?

---

### Post by Ayuthia on 2008-05-19
> **anpu1 said:**
> I already had Hardy on this computer but the computer was f**** up! Hardy was slow and useless on HP. so I wenr beck to Gutsy! its working faster and its more stable!!

Ayuthia the problem is not in screen! and the drivers are right! the problem is when i want to use internet it doesn't connect back!!

ok about the blue LED sory! i tought that its blue when its connected :)

maybe anyone knows what program to use for wireless?
From the Terminal, can you get the results of lspci -nn?  HP has a few different wireless cards.

---

### Post by anpu1 on 2008-05-19
here it is!!!!



00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
05:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
05:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
05:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)
05:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
05:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)

---

### Post by DizzyTech on 2008-05-20
All right, you need to install Hardy **and**, enable the backports repository in "Software Sources, and install the latest kernel backports package.  That's what fixed this same card for me.

---

### Post by anpu1 on 2008-05-21
i don't want to install Hardy because that system works slow on my laptop! i had that system already intstaled but it was sloqer than Gutsy and the system hanged itself time to time! Mozilla worked bad (every page i wanted to open it became gray and it hanged) so thats why i went back to Gutsy! BUT if you have any ideas why it works slower than Gutsy and it can be repaired plz tell!!


TNX

---

### Post by DizzyTech on 2008-05-21
Have you used 32-bit or 64-bit?  Maybe you got a bad CD download.

---

### Post by anpu1 on 2008-05-23
I made upgrade from the 7.10 from the administrative tools! maybe that was the reason that it was not working good! I will try to download CD and to install Hardy!! I will get back to you!!

TNX

---

### Post by anpu1 on 2008-05-23
OK now i installed Hurdy and will see how it works! I hope it will work better than the las time!!

There is one thing about the wireless. The LED should be blue but its yelow, but the wireless connection and internet are working! any ideas why the LED is not blue?

---

### Post by DizzyTech on 2008-05-23
I'm not sure how to describe it... you need to go into "Software Sources" and enable the backports repository, then install the package "linux-backports-hardy-generic" (I think that's it, you'll be better off searching for backports in Synaptic).  That'll install a new version of your WiFi driver.

---

### Post by anpu1 on 2008-05-25
hy everyone i'm back :D sorry for not updating i was studying :)

I did everything what you say DizzyTech! now the blue light started to shine :) when the internet is working!

But there is still a problem when mozilla diesn't want to load the pages. and i was downloading some torents and the torent program was on the internet and the aMSN is on the internet but mozilla doesn't want to load a page!?!?!?

any ideas what is going on? maybe i have to repair something in mozilla?

tnx for help

---

### Post by maybememe on 2008-12-27
The problem is a defect with many Hp laptops. There is an extended warranty to cover it.

hplies.com has more. and hp.com's msg board had hundreds of people all reporting same problem on linux and windows.

---

