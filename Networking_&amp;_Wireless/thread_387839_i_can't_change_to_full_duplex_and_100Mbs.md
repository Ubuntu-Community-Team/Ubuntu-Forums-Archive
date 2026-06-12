---
title: "i can't change to full duplex and 100Mb/s"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by gronto on 2007-03-18
Hi!
I hav recently change to xubuntu from win xp but I have some problems with my networkcard.
I have tried to change from halfduplex to full duplex and 100Mb/s insead of 10Mb/s but nothing happends.
Here is some information:

> 
admin@garderoben:~$ sudo lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)


admin@garderoben:~$ sudo ethtool -i eth0
driver: 3c59x
version: LK1.1.19
firmware-version:
bus-info: 0000:00:11.0


admin@garderoben:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Full
                                100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: yes


admin@garderoben:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:4F:21:0A:DE
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1738 errors:222 dropped:0 overruns:0 frame:327
          TX packets:1413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1197637 (1.1 MiB)  TX bytes:228519 (223.1 KiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

I have tried using this:
```

sudo ethtool -s eth0 duplex full speed 100 autoneg off

```
but nothing happends
someone who knows what to do?

---

### Post by Mr. C. on 2007-03-18
Are you connected to a hub or is the link partner (other side) a direct cable connect?  Hubs only support half-duplex.  If so, get a 10/100 switch.

The 3c905b is a very well support card.  Your card is configured to autonegotiate; it will automatically negotiate the highest speed possible based on its link-partner.

MrC

---

### Post by gronto on 2007-03-19
ok. but as linkpartner I have a netgear router that supports 100Mb/s and full duplex, it works with my other computer.
Maby it somthing wrong with the card, but it worked well when i used WinXP.

---

### Post by netztier on 2007-03-19
> **gronto said:**
> 
```

admin@garderoben:~$ sudo ethtool eth0
Settings for eth0:
Supported ports: [ TP MII ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
Supports auto-negotiation: Yes
[COLOR="Red"]Advertised link modes: 10baseT/Full[/COLOR]

```


That's where the error must be. **ethtool** says that the card is advertising *10Mbps fullduplex*. Already back in the days of 10Mbps Ethernet, this was quite uncommon, and I'm sure that the link partner in your network will have a bit of a problem correctly detecting this or adapting to it.

The thing is: if you can't configure the devices at ***both*** ends of the link for the same (fixed) mode, you **MUST NOT** configure one end only - unless you configure it for half duplex.

Reason: a device will stop advertising it's settings as soon as you configure it for a fixed mode. The link partner at the other end can't learn what the partner advertises and must then fall-back to half duplex. Therefore, the most common error this one:  a user sets the NIC on his PC to 100Mbps full duplex (because he's read somewhere that this is faster...), while he doesn't (our can't) configure the switch port. Consequence: the switch will set it's port to 100Mbps half duplex and the mismatch is there.

Now, in your case, we'll have to figure out why that card advertises 10mbps fullduplex *only* (or why ethtool believes that this is so), and how we can make it advertise all modes again. The link partners will then automatically pick the best common mode.

Have you tried **mii-diag**, too? What does it say about your card? (also try the -v and  -vv command line options)

Can you give us the output of the last few lines of **dmesg**, after you have unplugged and the re-plugged the NIC?

You say you were using the Card with Windows XP. Was that with the same cable and the same switch port? Can you swap/change them and see if the problem goes away with another cable and/or switch port? You should be able to tell just by looking at dmesg's output, I think it's driver does report well is happening during link negotiation.

best regards

Marc

---

### Post by Mr. C. on 2007-03-19
I missed the advertised modes; good catch netztier.

The 3Com card could be configured via nvram to advertise only certain modes.  There is/was a Windows utility to change this, as well as a dos utility.

I don't recall exactly, but the card may downgrade its capabilities with an iffy cable.

MrC

---

### Post by gronto on 2007-03-19
HI!
I have change cabel and switch port, also tried to plug my internet cabel(100/10Mbits) directley into the computer but it is the same result.
I cant unplug my NIC because its integrated with the motherboard. But i can turn it off in bios.
Here is a few lines from dmesg:
Without NIC enabled:
> [4294701.575000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294702.486000] cdrom: open failed.
[4294706.031000] NET: Registered protocol family 17
[4294712.491000] ACPI: Power Button (FF) [PWRF]
[4294712.862000] ibm_acpi: ec object not found
[4294712.936000] pcc_acpi: loading...
[4294723.787000] ppdev: user-space parallel port driver
[4294724.502000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294724.502000] apm: overridden by ACPI.

With NIC enabled:
> [4294701.230000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294702.137000] cdrom: open failed.
[4294705.121000] NET: Registered protocol family 17
[4294709.352000] eth0: no IPv6 routers present
[4294711.534000] ACPI: Power Button (FF) [PWRF]
[4294711.951000] ibm_acpi: ec object not found
[4294712.025000] pcc_acpi: loading...
[4294723.042000] ppdev: user-space parallel port driver
[4294723.515000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294723.515000] apm: overridden by ACPI.



Here is some information from the mii-diag:
> admin@garderoben:~$ sudo mii-diag eth0
Basic registers of MII PHY #24:  3000 784d 0000 0000 0141 0000 0004 2001.
 Basic mode control register 0x3000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
 Your link partner does not do autonegotiation, and this transceiver type
  does not report the sensed link speed.
   End of basic transceiver information.


admin@garderoben:~$ sudo mii-diag -v eth0
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
  Using the new SIOCGMIIPHY value on PHY 24 (BMCR 0x3000).
 Basic mode control register 0x3000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 Your link partner does not do autonegotiation, and this transceiver type
  does not report the sensed link speed.
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
 MII PHY #24 transceiver registers:
   3000 784d 0000 0000 0141 0000 0004 2001
   0000 0000 0000 0000 0000 0000 0000 0000
   0000 0080 0f50 0000 0000 0005 2001 0000
   0000 2040 07cf 1c11 0011 1000 0000 0000.
 Basic mode control register 0x3000: Auto-negotiation enabled.
 Basic mode status register 0x784d ... 784d.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation not complete.
 This transceiver has no vendor identification.
 I'm advertising 0141: 100baseTx-FD 10baseT-FD
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is 0000:.
   Negotiation did not complete.


Thanks for helping me!

---

### Post by Mr. C. on 2007-03-19
> Your link partner does not do autonegotiation, and this transceiver type
does not report the sensed link speed.

There's your answer.  The other side is not auto negotiating.  What exact device is on the other side ( i know its a "netgear", but that's all).  Have you updated its firmware?

MrC

---

### Post by jrusso2 on 2007-03-19
There is a Floppy Disc boot able Dos disc for those 3com cards that allows you to change the speed to 100mbs/Full Duplex.

I remember when we worked with those cards we would carry around those floppys and set them all manually as they didn't seem to auto negotiate.

I bet you can still get that utility on the 3com site.

---

### Post by netztier on 2007-03-19
> **gronto said:**
> 
I cant unplug my NIC because its integrated with the motherboard. But i can turn it off in bios.


Ouh.. sorry.  I meant that you should unplug *the cable* from the NIC, not remove the NIC from the computer. That's my mistake, I am sorry.

Can you remove the cable from the NIC, re-plug it in and then copy dmesg's output? 

Again - sorry for being unclear

best regards

Marc

---

### Post by gronto on 2007-03-19
Mr.C;
I have a netgear rp614v3. I have uppdated the firmware.
I have also connected my ubunto computer to my xp and I get the same result in miidiag.

netztier:
I get the same last lines as befor when i unplug the cabel:
> [4294700.286000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294701.194000] cdrom: open failed.
[4294704.255000] NET: Registered protocol family 17
[4294708.502000] eth0: no IPv6 routers present
[4294710.708000] ACPI: Power Button (FF) [PWRF]
[4294711.097000] ibm_acpi: ec object not found
[4294711.171000] pcc_acpi: loading...
[4294721.978000] ppdev: user-space parallel port driver
[4294722.451000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294722.452000] apm: overridden by ACPI.


jrusso2:
I think i have found the tool you talked about. let see if that works.

---

### Post by Mr. C. on 2007-03-19
Something funky is going on here.  This router/switch combo will auto negotiate just fine.  

It is still not clear to me that:

a) you've used a different, known working CAT 5 or CAT 6 cable
b) you used a cross-over cable when you plugged directly into your windows box.
c) power cycled your router/switch with all ethernet cables unplugged, and then plug in only Ubuntu

MrC

---

### Post by gronto on 2007-03-19
Now it works!
Thanks a lot guys!
It worked with the bootdisk from 3com that jrusso2 talked about.

sorry Mr.C if I dint say what cabels I used. It was a few cat5e cabels and a crosover cat 5.

I think it was a strange problem, why did i need a dos program, why didnt the autoneg work?

Again thanks a lot!

---

### Post by Mr. C. on 2007-03-19
Several models of the 3com NICs had issues with certain switches.  Their solution was to create a little utility to program the card to force certain configurations.  It was a workaround.  You apparently ran into one of these cards.  I recall the 905B had at least 3 chip mfgs, and several revisions for each chip.

I had mentioned this earlier in the post, but jrusso2 made it clearer.

Glad its all working,
Cheers.

---

### Post by netztier on 2007-03-20
> **gronto said:**
> 
I think it was a strange problem, why did i need a dos program, why didnt the autoneg work?


It might very well be that the switch in the Netgear RP614 was not able to adapt to it's link partner properly. 10Mbps full duplex is not a very common ethernet mode, and there's bound to be plenty of hardware out-there that won't support it.

Now why your NIC advertised this mode only - but worked well under XP - I can just guess: possibly the NIC read some of it's own configuration registers and found that value there. With the DOS tool, you've been able to reconfigure it properly now.

Possibly the XP driver can override that configuration and force the chip to do "full autoneg" up to 100Mbps full duplex, while the Linux kernel module can't?

*mumble* yet another reason for me not to like 3com. Honest. I haven't seen too many of their cards and hardware, but whenever I was called to help with someone's ethernet, half the time some 3com NIC or Hub was part of the problem. Personally, I like the Intel Chips for (wired) Ethernet a lot more.

best regards

Marc

---

### Post by Mr. C. on 2007-03-20
The OPs card is likely an earlier rev of the card, which required driver workarounds to enable full auto-negotiation.  I know specifically of many of those workarounds.  Unfortunately, 3Com did not make these readily available to driver writers (such and Donald Becker, who wrote this and most of the Linux drivers).

NICs were the bread and butter for 3Com for quite some time, and companies like Dell ensured through rigorous QA and regression testing that workarounds for chip problems were in the Windows drivers.  The Linux drivers did not receive all of these.

You likely saw so many problems with 3Com cards, simply because they had the lion's share of the NIC and onboard market for a long time.  Dell sold many machines with 3Com NICs.

They are good cards, and were well designed.  Intel simply did a better job of keeping the open source community up on hardware issues.

MrC

---

### Post by Gus_T_Reer on 2007-07-22
I know I'm being thick here but I've got the same problem (3c905b-tx) and could someone briefly describe what should be downloaded from 3com (link?) and quickly how to use it. All this network jiggerypokery is a bit beyond me.
Thanks.

---

### Post by Mr. C. on 2007-07-23
Gus,

I did a quick scan of the 3com downloads area, but did not see the utility that I recall.  There is a cardfind.exe and a diagnostics utility.  There are also the multi-part 3com drivers and utility software.  It is possible that any of those items contains the software you seek.  They all run under a DOS or Win 98 environment, so you'll have to create a bootable DOS floppy and add the .exe file to that floppy, and boot from there.  

Try cardfind.exe first, then the diag utility.  If those are not correct, you'll have to extract the contents of the multi-part driver set release floppy images, to see what is inside.

MrC

---

### Post by Gus_T_Reer on 2007-07-23
Thank you Mr. C. Only this afternoon did I manage to get things fixed by using the said utility. I've documented my actions in this thread [http://ubuntuforums.org/showthread.php?t=503194&page=2](http://ubuntuforums.org/showthread.php?t=503194&page=2) in the hope that it helps somebody else.

I appreciate your response though.

Cheers

---

### Post by Mr. C. on 2007-07-23
Great, glad you found it.

I suspect these cards were once in a Windows environment, connected to a hub, and then the Ethernet driver's were installed, which noted that the cards should be NVRAM configured for 10/half.

MrC.

---

### Post by Gus_T_Reer on 2007-07-23
Now that you mention it... ;)

I used to have a hub on my home network in the very early days (when these cards were new), I vaguely remember mention by our network gurus at work talking about duplex at the time. Wish I had my notes from then now. Does that make sense?

GTR

---

### Post by Mr. C. on 2007-07-23
Yup, I'm sure that's the case.  As I mentioned earlier, some early rev's of these cards had issues with some switches/hubs, so the driver installs set NVRAM at 10/half to avoid the problems.

MrC

---

