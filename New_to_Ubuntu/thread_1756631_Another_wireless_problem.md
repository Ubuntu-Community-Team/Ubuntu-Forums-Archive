---
title: "Another wireless problem"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by zoftware on 2011-05-12
OK, I tried to HELP a friend install Ubuntu 11.04 on his HP Pavilion zd8000.

That  was three days ago. Most things seem to be working fine except for the  absence of some of the scroll bars... and the wifi ceased working on  install. The wifi is important for him.

Firefox very promptly and clearly tells us that the "Server is not found".

There  are NO wireless networks available under the menu icon, only the Auto  eth0. Same for the Network Connections tool. Manually configuring the  wireless has no result, even with restarts.

I did discover a message, black text on the black pull-down menu, "Firmware missing".

I  have read the Help files, combed the Ubuntu Forums, tried quoted and  unquoted keyword searches on Google, and made two prior posts in the  forums. Nothing.

I have tried updating to 11.04, downgrading to 10.10, then to 10.04, then back to 10.10, and back to 11.04... still the same.

Are we the only people with an HP Pavilion wifi problem on Ubuntu 11.04, 10.10, and 10.04?

Maybe they are less frustrated with 500 new viruses and trojans on Windows every month.

I have looked for additional tools to help me determine which hardware and drivers are being used.

Very  little was user friendly, and many posts to the forums simply threw out  code/commands with no indication of how or where to run it. I thought  that I chose the ABSOLUTE beginners forum?

Bugtracking is an art form. I have been very deliberate and exhaustive with the combinations and permutations.

I found a small  purple message on a black background which I almost didn't see. User friendly?

Apple is expensive, easy to use, and easy to read.

Windows takes your money, doesn't reply to email, AND doesn't care.

Many of us are poor, and are lucky to have Ubuntu.

So what I have is: lspci -nn

jorge@zd8000-PD726AV-ABA:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port [8086:2581] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)
00:1e.2  Multimedia audio controller [0401]: Intel Corporation  82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e]  (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M24 1P [Radeon Mobility X600] [1002:3150]
0b:00.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
0b:00.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
0b:00.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
0b:00.4  SD Host controller [0805]: Texas Instruments  PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller  [104c:8034]
0b:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
0b:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

Followed with  rfkill list:

jorge@zd8000-PD726AV-ABA:~$ rfkill list
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
jorge@zd8000-PD726AV-ABA:~$ 

Any simple instructions in English would be  appreciated.

If you are going to beat us up with NERDspeak to make yourself look good, you are not helping anyone.

---

### Post by josephmills on 2011-05-12
please see post number 44 [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

---

### Post by jonobe on 2011-05-12
I've recently lost wifi connection on my 10.04 - can not find any obvious reason - it has been fine for a year until now!

Could an update have caused the problem?

I am using a Compaq 610 and am having to use the dreaded Windows 7 to connect to the internet, so am in desperate need of help here.

Like in the above post, jargon is not my thing, but can do simple commands.

---

### Post by josephmills on 2011-05-12
dear jonbe please post ```
lspci -nn
``` thanks

---

### Post by zoftware on 2011-05-13
josephmills = Mr. Kitchen Sink

... and it is still clogged (the wifi is still NOT connecting)

josephmills gave me a link to EVERY Broadcom solution made. It is like swimming in the Pacific Ocean without a compass looking for a Bikini atoll.

ABSOLUTE BEGINNER Forum?

And none of it worked anyway!

It is like asking for help, and he throws an 400-page manual at you.

You FINALLY finish reading the manual... and it was the wrong volume:

[http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

DOES NOT WORK for the HP Pavilion zd8000 in Ubuntu 11.04. It uses the BCM4306.

Instructions were included, and they very specificly did not work.

We could still use some beginner help.

Thanks

---

### Post by JP121 on 2011-05-13
[http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/](http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/)

I don't remember if you said you tried activating the restricted driver yet.

The above instructions are for 8.04, but are worth a try if you haven't already tried that yet.

---

### Post by zoftware on 2011-05-13
OK, maybe I was a bit unfair.

josephmills did not give us 400 pages.

He gave us 7 screens of Geek, 4 of which were his.

Let another professional give him 4 pages of instructions in Greek, German, Chinese, neurosurgery, electromagnetic particle physics, or something comparable, and it would be considered condescending and rude..

The point is, I tediously strugled thru the complete post, and it still does not work.

Any responsible assistance would be appreciated.

Please do not hit me with another dump truck of information.

It gives nerds a bad name.

---

### Post by wildmanne39 on 2011-05-13
> **zoftware said:**
> OK, maybe I was a bit unfair.

josephmills did not give us 400 pages.

He gave us 7 screens of Geek, 4 of which were his.

Let another professional give him 4 pages of instructions in Greek, German, Chinese, neurosurgery, electromagnetic particle physics, or something comparable, and it would be considered condescending and rude..

The point is, I tediously strugled thru the complete post, and it still does not work.

Any responsible assistance would be appreciated.

Please do not hit me with another dump truck of information.

It gives nerds a bad name.
Hi, I have that same wireless card and if you plug the laptop into an ethernet connection and go to restricted drivers you should be able to activate the driver you need then restart and you should just have to enter your password.:)

---

### Post by bkratz on 2011-05-14
> **zoftware said:**
> OK, maybe I was a bit unfair.

josephmills did not give us 400 pages.

He gave us 7 screens of Geek, 4 of which were his.

Let another professional give him 4 pages of instructions in Greek, German, Chinese, neurosurgery, electromagnetic particle physics, or something comparable, and it would be considered condescending and rude..

The point is, I tediously strugled thru the complete post, and it still does not work.

Any responsible assistance would be appreciated.


Please do not hit me with another dump truck of information.

It gives nerds a bad name.



Found this interesting thread about how the wireless button works on HP Pavilions and recent distributions, it may be worth investigating further.

[http://ubuntuforums.org/showthread.php?p=10812226#post10812226](http://ubuntuforums.org/showthread.php?p=10812226#post10812226)

---

