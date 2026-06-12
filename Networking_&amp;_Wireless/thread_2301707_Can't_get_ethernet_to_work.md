---
title: "Can't get ethernet to work"
date: 2015-11-04
forum: Networking &amp; Wireless
---

### Post by Cliff0884 on 2015-11-04
I am very new to ubuntu. It seems to be way over my head but I am giving it a go anyways. I have installed 14.04 and it seems to be working fine. But it does not recognize my network when I plug in the network cable. Ifconfig sees my network adaptor but when I plug the cable in I get nothing. It just says cable not connected. I am using a Dell optiplex pc. Any suggestions and or advice will be appreciated.

---

### Post by eddiefiggie on 2015-11-04
Hey, I've been noodling around with Ubuntu now for a month or so.  If you're patient and willing to learn it, it's quite fun.  Full of "wow" moments at every turn.

That being said, you should close this thread (mark as solved) and post over in the "Wireless & Netowrking" forum.  Here's a link you should start with that helped me a ton!

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Don't feel bad though, I did what you did and someone told me the same.  =P  Glad they did though because this helped me out!

Hope this get's you rolling along!

---

### Post by ajgreeny on 2015-11-04
Don't worry about moving this thread; I have now moved it to the correct sub-forum area where it may get much better attention from those who know about networking.

To give more help to others who may assist you, can you please show us the output of terminal command ```
lspci | grep Ethernet
```
Do you have a working wifi network connection; I assume you do, but I would like clarification of exactly where we stand.

---

### Post by Cliff0884 on 2015-11-05
lspci gave this. grep Ethernet did nothing so far as i could tell. 
```
ubuntu@ubuntu-OptiPlex-360:~$ lspci00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 0a)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 0a)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 0a)
00:02.1 Display controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 0a)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
ubuntu@ubuntu-OptiPlex-360:~$ grep Ethernet


      



```

I know the ethernet port has worked in the past but i have not used the computer in awhile. I am trying to connect an ethernet cable to the pc from a wifi extender. The wireless and wired connection works from extender to a windows pc just fine. I do not have a wireless adapter on the ubuntu machine due to driver issues. I was hoping that would not be an issue with the cable to extender but it seems it may be an issue as well.

p.s. thanks for moving me to the correct forum area. not only am i new to linux i am also new to using forums. windows plug and play made everything so simple i never needed to do much research. which makes me feel i have not learned as much about computers as i wish i had from the get go.

ok so i feel dumb. now that i look closer i see why grep ethernet did not work. so here is what you was asking for.
```
ubuntu@ubuntu-OptiPlex-360:~$  lspci | grep Ethernet02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)

```

---

### Post by Cliff0884 on 2015-11-05
To test this further i moved the pc to the room with my router and hard lined straight to it and still have no connection. This leads me to believe my NIC is not working. It is strange to me though that the operating system sees the NIC with no problems but it does not work.

---

### Post by tgalati4 on 2015-11-05
Welcome to the forums.

How old is this Optiplex?  Did the network work under Windows?  

The module that is used is *tg3* and generally works well. I have similar one in my laptop:

> 02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

 Try some of these tips:  [http://www.cyberciti.biz/faq/linux-broadcom-ethernet-card-driver-installation/](http://www.cyberciti.biz/faq/linux-broadcom-ethernet-card-driver-installation/)

There is a debug switch:

> parm:           tg3_debug:Tigon3 bitmapped debugging message enable value (int)

Everything is fixable; it takes patience.

---

### Post by Cliff0884 on 2015-11-05
The pc is 6 years old. I got it for free from my school when they did some upgrades. It came without HDD. I have not ran it with windows. I ran ubuntu on it from an external back when i first got it earlier this year and the ethernet port worked then. But then i put it up for awhile and decided not to use it. Now i want to use it so i put HDD in it and installed ubuntu on it and ethernet is not working. I will check the link out and see what i can come up with. Thanks for the quick replies.

---

### Post by gordintoronto on 2015-11-07
Could you try it with a different cable?

---

### Post by Cliff0884 on 2015-11-14
Sorry about the delay in response. Life lol. Yes i did try a couple of other cables just in case. But that is a good suggestion. Fortunately I found a cheap alternative recently. I came across a plug and play Linux wireless adapter online for like 3 bucks. it came in the mail a couple days later and i am connected to my network straight out of the box. Thanks for all the suggestions though.

---

### Post by tgalati4 on 2015-11-14
Check the motherboard for any bulging or leaking capacitors, especially around the network port.  A 6-year-old motherboard that has seen a previous life in a school is bound to have some problems.  At least you found a work-around.

---

