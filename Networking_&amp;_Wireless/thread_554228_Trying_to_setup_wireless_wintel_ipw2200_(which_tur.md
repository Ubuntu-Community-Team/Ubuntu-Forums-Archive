---
title: "Trying to setup wireless w/intel ipw2200 (which turned out to be Broadcom!)"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by Phelan on 2007-09-18
So after messing around some more, I have downloaded ipciw (i think thats what its called, I'm in windows right now otherwise I'd look) to setup my wireless (or try) that way.  It says no wireless networks found.  I'd like to try to install the new ipw2200 drivers, I've downloaded them but am totally lost as to what to do with them (even after looking at luca-linux's walkthrough, I don't know what to do.

He says; "untar them and move them from the current folder to the driver folder".  What would the current folder be, home?  Where is the driver folder?  Is it a driver issue that it's not seeing my network?  I think my network is WPA but I wouldnt swear to it, do I need to do that supplicant how-to?  It's pretty confusing too...need some help.

---

### Post by Phelan on 2007-09-18
About to leave for work, page #2, *bump*

---

### Post by noob12 on 2007-09-18
Hmm.  What release are you running? The ipw2200 driver ships with Ubuntu 7.04 in the base kernel.   Are you building because you had trouble with the version in the distribution?

Are you sure you have an Intel 2200 card?  Can you post the output of 
```

lspci -nn

sudo lshw -C network

```

---

### Post by Phelan on 2007-09-19
I'm on my 1AM lunchbreak right now so I can't post it until I get home at 6, but just to clarify, I type that in the terminal?

---

### Post by noob12 on 2007-09-19
Yes.  The first should produce output describing all of the PCI devices on your box.  The second one will tell us some additional information about the network devices, and what drivers are associated to them currently.

---

### Post by wieman01 on 2007-09-19
You don't have to compile your own driver. IPW2200 comes with the default install of Ubuntu since Breezy at least.

What is the output of this command (terminal):
> sudo iwlist scan
That should tell us whether your card is working or not.

_**EDIT:**_
I have a IP2200 as well and no problems.

---

### Post by Phelan on 2007-09-19
I am home now.  Here is the results of the first one you asked me to post:

> cole@cole-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
06:06.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:09.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
06:09.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
06:09.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
06:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
cole@cole-laptop:~$ 
cole@cole-laptop:~$ sudo lshw -C network


and the second one (for what its worth)

> cole@cole-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

cole@cole-laptop:~$ 


Thanks again for thelp, hopefully one of you guys can get this n00b up and running with wireless!! :lolflag:

---

### Post by Phelan on 2007-09-19
Also, I dont know if it matters but my wireless button doesn't work, it doesnt light up or anything.  I did notice after playing with it and loading windows, that it was disabled and i had to hit it again.  I left it on and loaded up ubuntu and it still doesnt work because I have no idea how to set my network up and get it working :)

---

### Post by kevdog on 2007-09-19
Are you sure this is not your wireless card:

06:06.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

This is a broadcom chipset that needs ndiswrapper and not the ipw driver.

---

### Post by noob12 on 2007-09-19
Yes, as kevdog points out, you haven't got an Intel 2200 at all.  You've got a Broadcom 4318 device.  That explains why the ipw2200 driver that ships with Ubuntu didn't immediately claim it.  Installing your own ipw2200 driver isn't going to do any good either :-)

My recommendation would be to try this thread:  [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by Phelan on 2007-09-19
That's funny, I looked up the specs on the laptop and it says intel 2200, not to mention the sticker on it says "intel wireless 2200G", not saying you guys arent right, i just don't understand why HP would throw any random wireless card in their laptops.  I will try that link thanks.

---

### Post by wieman01 on 2007-09-20
> **Phelan said:**
> That's funny, I looked up the specs on the laptop and it says intel 2200, not to mention the sticker on it says "intel wireless 2200G", not saying you guys arent right, i just don't understand why HP would throw any random wireless card in their laptops.  I will try that link thanks.
I would have a word with the vendors. That's hilarious!

---

### Post by Phelan on 2007-09-20
Thanks.  Worked great got me up and running.

---

