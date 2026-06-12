---
title: "Usb WiFi"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by sparkybean on 2007-05-02
Hello all,

I have recently taken the plunge, and removed xp from my laptop and replaced it with ubuntu. Im gald i did, except my wifi card and my ethernet port are not working. This means usb wifi is my only option.

Im fine with leaving the ethernet port, as i use wireless alone, but am not sure about what to do a the wifi adapter. I thought about buying one of [these]("http://www.linuxemporium.co.uk/products/wireless/#pid88171") (the one with no antenna) but if anyone has any experience with one of these, or a better suggestion before i shell out £20, just shout.

#Edit: i have ubuntu 6.06LTS, and im an utter n00b at this, so a suggestion of something like "buy this, plug it in" would be great. Thanks!

---

### Post by dannyboy79 on 2007-05-02
ok, please make sure that your wifi card is plugged if it's not internal and tell what this command returns if you enter it into a Terminal (terminal can be found within the pull down menu, in dapper it's under accessories)

lspci -v

also, pleas inform me of your setup, do you have a router? do you have a cable modem? dsl? what's your internal ip address of your router if you haev one?

---

### Post by sparkybean on 2007-05-02
Thanks for the quick reply!

The wifi card is internal, and permantly powered on :)  When i enter that command it gives me:

```
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03 )
        Subsystem: Uniwill Computer Corp: Unknown device 9914
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Grap hics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Uniwill Computer Corp: Unknown device 9914
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at b0040000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <available only to root>

0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Co ntroller (rev 03)
        Subsystem: Uniwill Computer Corp: Unknown device 9914
        Flags: bus master, fast devsel, latency 0
        Memory at b0100000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Uniwill Computer Corp: Unknown device 9084
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at f0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 0000f000-0000ffff
        Memory behind bridge: fac00000-febfffff
        Capabilities: <available only to root>

0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <available only to root>

0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: f7000000-f70fffff
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Uniwill Computer Corp: Unknown device 907b
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at 1820 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Uniwill Computer Corp: Unknown device 907b
        Flags: bus master, medium devsel, latency 0, IRQ 225
        I/O ports at 1840 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Uniwill Computer Corp: Unknown device 907b
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at 1860 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Uniwill Computer Corp: Unknown device 907b
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at 1880 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Co ntroller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Uniwill Computer Corp: Unknown device 907b
        Flags: bus master, medium devsel, latency 0, IRQ 233
        Memory at f0004000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (pro g-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f0200000-f02fffff
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridg e (rev 02)
        Subsystem: Uniwill Computer Corp: Unknown device 907b
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controlle r (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Uniwill Computer Corp: Unknown device 907b
        Flags: bus master, medium devsel, latency 0, IRQ 225
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]

0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02) (prog-if 8f [Master SecP SecO PriP PriO] )
        Subsystem: Uniwill Computer Corp: Unknown device 907b
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 225
        I/O ports at 18d0 [size=8]
        I/O ports at 18c4 [size=4]
        I/O ports at 18c8 [size=8]
        I/O ports at 18c0 [size=4]
        I/O ports at 18b0 [size=16]
        Memory at f0004400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev  02)
        Subsystem: Uniwill Computer Corp: Unknown device 907b
        Flags: medium devsel, IRQ 10
        I/O ports at 18e0 [size=32]

0000:06:04.0 FireWire (IEEE 1394): O2 Micro, Inc.: Unknown device 00f7 (rev 02) (prog-if 10 [OHCI])
        Subsystem: Uniwill Computer Corp: Unknown device 300b
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 185
        Memory at f0200000 (32-bit, non-prefetchable) [size=4K]
        Memory at b0200000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <available only to root>

0000:06:04.2 0805: O2 Micro, Inc.: Unknown device 7120 (rev 01)
        Subsystem: Uniwill Computer Corp: Unknown device 907b
        Flags: slow devsel, IRQ 185
        Memory at b0200800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:06:04.3 Mass storage controller: O2 Micro, Inc.: Unknown device 7130 (rev 0 1)
        Subsystem: Uniwill Computer Corp: Unknown device 907b
        Flags: slow devsel, IRQ 3
        Memory at f0202000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
        Subsystem: Uniwill Computer Corp: Unknown device 9700
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at 2000 [size=256]
        Memory at b0200c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>


```

We have a cable (broadband) modem with router, and its ip address is 192.168.1.1 and the address it usually gave to my laptop (when i was on windows) was 192.168.1.100

---

### Post by Kobalt on 2007-05-02
The chipset upon which is based the card (rt25xx) you intend to buy is supported out of the box by Ubuntu.
Wouza :)

---

### Post by dannyboy79 on 2007-05-02
> **Kobalt said:**
> The chipset upon which is based the card (rt25xx) you intend to buy is supported out of the box by Ubuntu.
Wouza :)


NOPE!!!! I just got one based on that Chipset and although the drivers are installed by default they DO NOT work, you have to follow this ([http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)) to get it to work. Also, he already has a wireless card as he stated, lets see if we can get that to work before he buys one!

ALso, with some instruction I am sure we could get his ethernet to work. can you please attach a file, what I'd like to see is your dmesg output but it's very long so what you should do is this

dmesg > dmesg.txt

and then basically attach the file dmesg.txt which you'll find in your /home/username/ folder if that's what the "pwd" command returns before you did the dmesg command.

---

### Post by sparkybean on 2007-05-02
Just seen dannyboy's post, the file is [here]("http://somervillehalt.awardspace.com/dmesg.txt")

---

### Post by sparkybean on 2007-05-02
Sorry double post

---

### Post by daigorobr on 2007-05-03
Having a Uniwill based laptop, I bet that your "onboard" wifi device is a Realtek's rt73 based USB internal dongle.
You could confirm by checking with the lsusb command. Mine is coded 0db0:6877.
I got it to work using ndiswrapper with the drivers present on this archive: [http://www.newcommunication.fr/flybook/fichiers/Drivers/Flybook/Wifi/RT73.zip](http://www.newcommunication.fr/flybook/fichiers/Drivers/Flybook/Wifi/RT73.zip)

Now, isn't it interesting that your computer doesn't make this 8139-based ethernet hardware work? I think it's the most trivial piece of hardware out there...

Of course, if you check that the wifi dongle you have is the same as mine, I will help you making it work.

---

### Post by dannyboy79 on 2007-05-03
you don't need to use ndiswrapper when there are native linux driver support. If it is in fact that chipset than follow this to get it to work: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

ALSO, your dmesg is showing some VERY VERY scary info relating to your sdb hard drive, particularlly partition 1! Anytime you see stuff like this:

Buffer I/O error on device sdb1, logical block 1940
[17179776.408000] lost page write due to I/O error on sdb1
[17179776.408000] sd 2:0:0:0: rejecting I/O to device being removed
[17179776.408000] Buffer I/O error on device sdb1, logical block 16424
[17179776.408000] lost page write due to I/O error on sdb1
[17179776.408000] Buffer I/O error on device sdb1, logical block 16425

and this:

FAT: Directory bread(block 3831) failed
[17179776.644000]  2:0:0:0: rejecting I/O to dead device
[17179776.644000] FAT: bread failed in fat_clusters_flush
[17179776.644000]  2:0:0:0: rejecting I/O to dead device

and this:

Buffer I/O error on device sdb1, logical block 44
[17179873.680000] lost page write due to I/O error on sdb1
[17179873.680000] sd 3:0:0:0: rejecting I/O to device being removed
[17179873.680000] Buffer I/O error on device sdb1, logical block 1940
[17179873.680000] lost page write due to I/O error on sdb1
[17179873.680000] sd 3:0:0:0: rejecting I/O to device being removed

It's normally a sure sign of the drive dying!! If it's within warrenty I would return it and if not, I would save all important from it immediately  and only use it to store junk that you wouldn't care if you lost it and get a new one asap if you need it. [www.tigerdirect.com](www.tigerdirect.com) has a 500gb Seagate ATA100 16mb buffer Hard Drive for $99.00 after $40 rebate which is a steal even though it is only ATA100. I actually did a test recently to find out if SATA 1.5gb is better in I/O performace versus ATA 100 and my results are pretty unsatisfying to say the least. using sudo ```
hdparm -Tt /dev/YdX 
``` it returns

Maxtor 6L300R0 is a ATA100 = 
 Timing cached reads:   2104 MB in  2.00 seconds = 1051.93 MB/sec
 Timing buffered disk reads:  164 MB in  3.00 seconds =  54.59 MB/sec

WDC WD5000AAKS-0 is a SATA1.5gb (also referred to as SATA I) =
Timing cached reads:   2092 MB in  2.00 seconds = 1045.93 MB/sec
 Timing buffered disk reads:  184 MB in  3.02 seconds =  60.84 MB/sec

Anyway, back on track here. Have you simply tried to use the system, admin, networking gui to enable your ethernet plug? plug in a cable into your laptop and it should work, your dmesg is showing it, it just stated that the link was down, so see if you can bring it up.

```
sudo dhclient eth0
```

or is it

```
sudo ifup eth0
```

---

### Post by daigorobr on 2007-05-03
The open sourced drivers from the rt2x00 project are indeed very good, although they don't work with network-manager. Ndiswrapper with rt73 are, indeed, the best choice for now - as far as you count functionality.

---

### Post by dannyboy79 on 2007-05-03
Ok, well I don't use network-manager. When you refer to network-manager you're not referring to the system, admin, networking dialog box are you? or are you referring to the applet you can install to show you what AP you're connected and what not? 

I've used wifi-radar in the past which worked awesome for Dapper and Xubuntu, do the drivers in questions work with wifi-radar?

Also, last time I tried using ndiswrapper, I had all these errors:
[17361823.436000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17361823.556000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17361823.616000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'

and then when I try to look at the syslog, it merely states the same thing and there is no log for ndiswrapper. 

can you point me in a good tutorial for setting up ndiswrapper?

---

### Post by daigorobr on 2007-05-03
Are you on Feisty?
It works for me, but I have to install ndiswrapper 1.9
I remember Edgy had 2 versions of ndiswrapper - one that worked and other that didn't.

As for the drivers, rt2x00's rt73 cvs driver works with wlassistant. I didn't get it to work neither with wifi-radar or with network-manager (and yeah, it is the applet one - it works with static configurations).

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29) worked for me.

Remembering that ndis will conflict with any other driver that may be connected  with the wifi card.

---

### Post by dannyboy79 on 2007-05-04
> **daigorobr said:**
> Are you on Feisty?
It works for me, but I have to install ndiswrapper 1.9
I remember Edgy had 2 versions of ndiswrapper - one that worked and other that didn't.

As for the drivers, rt2x00's rt73 cvs driver works with wlassistant. I didn't get it to work neither with wifi-radar or with network-manager (and yeah, it is the applet one - it works with static configurations).

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29) worked for me.

Remembering that ndis will conflict with any other driver that may be connected  with the wifi card.

i originally tried the ndiswrapper within Edgy, not Feisty. so you're saying that if I want a gui for my wireless configuration I have to use wlassistant which is a kde package, how many dependencies does it bring with it? As far as ndis conflicting that would be resolved with blacklisting it correct? because I had done that. so I must have been using the wrong ndiswrapper.

---

### Post by daigorobr on 2007-05-04
Err... Yeah, I found annoying having to deal with wlassistant. But static configs work, in the bright side.
Blacklisting works for me (I blacklisted the drivers rt73usb and rt73 for ndis to work). And nm-applet is the best Ubuntu invention since sliced bread (altho I don't think bread is Ubuntu related).

---

### Post by dannyboy79 on 2007-05-04
> **daigorobr said:**
> Err... Yeah, I found annoying having to deal with wlassistant. But static configs work, in the bright side.
Blacklisting works for me (I blacklisted the drivers rt73usb and rt73 for ndis to work). And nm-applet is the best Ubuntu invention since sliced bread (altho I don't think bread is Ubuntu related).

i never used wlassistant I just read somewhere that it works where as if you need to setup a static ip and you need to use vpn or whatnot, that the nm-applet doesn't work, it greys out the vpn stuff. so you're saying that if you leave nm-applet in dhcp mode, that the vpn setttings are usable and what not? thanks for the info about blacklisting rt73 and rt73usb as I have the belkin FDblahblah and will either go the ndiswrapper route or the seamonkey route as I haven't had a need for the nm-applet. i can just configure the wireless using the files instead of a gui. the wpa thread within these forums is awesome as far as configuring wireless just by the files and the wireless tools.

---

### Post by daigorobr on 2007-05-04
nm-applet works for me as I have multiple networks I connect daily. I would die reconfiguring everything every time.
It's a fact that nm-applet is 'dumb-ifying', since it doesn't allow much customization of configurations (it's either completely auto or completely manual, no midpaths). Thank god all my networks are simple, dhcp-based.

* although nm-applet provides a nice interface for manual configs too. and it's very nice for me having some applet telling me how strong is the signal. *

As for wpa, one more reason for using ndis. I don't use it, but it seems rt73 drivers are not "wpasupplicant compliant" or so. I would really have to investigate more to answer exactly.

---

### Post by dannyboy79 on 2007-05-07
alright, thank you so much. one last thing, I sometimes switch back and forth between wifi and ethernet on my old laptop, and all I do is have different interfaces files. one that has -wifi on the end and one that has -eth on the end.. then all I do is rename it so that it's just interfaces and then I do 

sudo /etc/init.d/networking restart

and then my new interface file is used. it only has to be setup once and it's not hard configure the interfaces file. I am merely pointing out the way that I have done it in the past not that it's efficient or the best way or the easiest, just another way. thanks for your help.

---

### Post by daigorobr on 2007-05-07
Your visions were of great importance to me too. Anything, just PM me and I'll try to help.

---

