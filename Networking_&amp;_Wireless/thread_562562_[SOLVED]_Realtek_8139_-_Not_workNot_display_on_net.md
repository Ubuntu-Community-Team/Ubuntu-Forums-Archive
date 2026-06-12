---
title: "[SOLVED] Realtek 8139 - Not work/Not display on network manager"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by shakaran on 2007-09-28
I have install Gutsy Gibon Tribe 5 and my network manager NOT display eth0.

I have Realtek 8139 but not is displayed.

the command

$lspci

```

golkers@robotin:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
00:10.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
00:11.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

```

I attach a image with my network manager.

I need solve this problem. Thanks

Edit: I find this:

```

golkers@robotin:~$ dmesg | grep 8139
[   39.618345] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    8.912000] 8139cp 0000:00:0f.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    8.912000] 8139cp 0000:00:0f.0: Try the "8139too" driver instead.
[    8.916000] 8139too Fast Ethernet driver 0.9.28
[    8.920000] 8139too 0000:00:0f.0: Chip not responding, ignoring board
[    8.920000] 8139too: probe of 0000:00:0f.0 failed with error -5

```

Because not working??

---

### Post by SpiritIsReality on 2007-09-29
howdy

do you dual boot with micsoft?edit :with a realteck and or chip(s) like those mentioned here?[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
if so check (edit:)[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
[http://ubuntuforums.org/showthread.php?t=559895&page=3](http://ubuntuforums.org/showthread.php?t=559895&page=3)
edit :what I should have said, was see this and that and the otherand linked to here?
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

please post back.
trails


don't look here unless you have time to read about 30 some posts. It was a rough ride for miki85, but miki85 stuck it out like a real trooper and is InTheSaddle by God.
[http://ubuntuforums.org/showthread.php?t=559895&page=3](http://ubuntuforums.org/showthread.php?t=559895&page=3)

edit : see post #2 >
[http://ubuntuforums.org/showthread.php?t=562479](http://ubuntuforums.org/showthread.php?t=562479)

---

### Post by SpiritIsReality on 2007-09-29
oops.
I wanted to say

if you look at your lspci your NetworkInterfaceCard is
00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
dmesg
[    8.920000] 8139too 0000:00:0f.0: Chip not responding, ignoring board
might be sleeping.

---

### Post by dilidon on 2007-09-29
> **fmat said:**
> howdy

do you dual boot with micsoft?
if so check post # 26 at 
[http://ubuntuforums.org/showthread.php?t=559895&page=3](http://ubuntuforums.org/showthread.php?t=559895&page=3)

please post back.
trails 

This does indeed point to a working solution posted by Fmat (one needs to enable "wake on lan after shutdown" in the Realtek card section in the device manager.) I confirm. Thanks.

---

### Post by shakaran on 2007-09-29
I dont understand.

I have ONLY Ubuntu Gutsy in this PC. NO XP installation. Because not wake up??

Today, i surprised because in found in network-manager a Wired Connection (see image), but not working.

```
golkers@robotin:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:2E:0B:DD:A7  
          inet6 addr: fe80::20e:2eff:fe0b:dda7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:94 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x6000 

eth0:avah Link encap:Ethernet  HWaddr 00:0E:2E:0B:DD:A7  
          inet addr:169.254.7.67  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28023 (27.3 KB)  TX bytes:28023 (27.3 KB)
```

Some solution? Thanks

---

### Post by noob12 on 2007-09-29
The "Chip not responding" message could be a result of a PCI routing issue during boot or it could mean that you need physically to re-seat the card in the slot.  I'm assuming the card is not actually faulty.

Does the eth0 interface now show up in **ifconfig -a** reliably? or is it the case that it shows up on some boots on other boots it does not appear in the output of **ifconfig -a** ?  If it only shows up sometimes, check the seating and also post the output of **dmesg**

Are you booting with the device connected to an active ethernet connection?  The driver for this card requires that.

Can you see if ```
sudo ethtool eth0
``` shows "Link detected: no" ?

Are there any errors in ```
tail /var/log/kern.log
``` ?

---

### Post by SpiritIsReality on 2007-09-29
howdy ... thankyou all. This is good
buds

---

### Post by shakaran on 2007-09-29
Hi again, i re-seat physically in slot the card. And it is working ;) Thanks for the support.

Although, it is strange that before run.

The mod can mark this thread as [SOLVED] ;)

---

### Post by SpiritIsReality on 2007-09-29
howdy pard
as far as I know, you are the one who can mark this thread solved.
at top of page, click on Thread Tools
click on Mark This Thread Solved.
buds

---

### Post by SpiritIsReality on 2007-09-29
it's not at the top of page ... my bad
it is at the top edge of your #1 post
buds

---

### Post by shakaran on 2007-09-30
ok, thanks

---

