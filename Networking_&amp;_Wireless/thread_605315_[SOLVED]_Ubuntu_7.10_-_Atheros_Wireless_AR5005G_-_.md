---
title: "[SOLVED] Ubuntu 7.10 - Atheros Wireless AR5005G - HELP PLEASE"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by DennisMonague on 2007-11-06
Hi Everyone, 

I'm currently running an Acer Aspire 5040 laptop with an Atheros AR5005G wireless card (came with the laptop).  I'm using Ubuntu 7.10, with windows running on a FAT32 formatted parition (so I'm dual booting).  I've been reading the threads for some time now and haven't been able to find a workaround or solution that will get that darned wireless to connect to my home wirelss system.  I have a PCX 2600 Toshiba wirelss router in the house.  

Some specifics:  My wireless works in Windows XP, however, I should note I did a fresh install a couple times and the wireless wouldn't work if I just try to install listed drivers, however when I used the recovery discs (like good little boy I created recovery discs right away after it finished that first time when I opened the box and unpacked my brand new laptop), the wireless worked fine.    I downloaded madwifi and couldn't get it to even see that darn card.  I read about ndiswrapper and tried that and hit pay dirt.  Ubuntu now sees the card.  It just doesn't see the network (it did however see fit to change my wireless card's name to AR2413 which appears to be the same card with a different name according to acer anyway).  My network is set open (i.e. no encryption or security passwords to access the wireless router, I don't mind sharing costs the same anyway).  I have a radio button on the front of my computer that will light up indicating the wireless card is on (you can push it to turn it off and on).  I should mention that in Ubuntu the radio button will not light up no matter what I have tried so far.

Here are some outputs from my system: 
dennis@dennis-laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:163:43:64:E2 
inet addr:192.168.1.101 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::216:d3ff:fe43:64e2/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1492 Metric:1
RX packets:3545 errors:0 dropped:0 overruns:0 frame:0
TX packets:3427 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:2870525 (2.7 MB) TX bytes:623846 (609.2 KB)
Interrupt:11 Base address:0xa000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

wlan0 Link encap:Ethernet HWaddr 00:16:CE:6B:C0:0D 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:10 Memory:d0200000-d0210000 

dennis@dennis-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11g ESSIDff/any 
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated 
Bit Rate:54 Mb/s 
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

dennis@dennis-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for dennis:
wlan0 No scan results

dennis@dennis-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename: /lib/modules/2.6.22-14-generic/misc/ndiswrapper.ko
version: 1.49
vermagic: 2.6.22-14-generic SMP mod_unload 

dennis@dennis-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 82)
00:14.1 IDE interface [0101]: ATI Technologies Inc Standard Dual Channel PCI IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975]
06:05.0 Ethernet controller [0200]: Atheros Communications, Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
06:06.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)

---

### Post by DennisMonague on 2007-11-06
Hi,

It's me again.  Some more outputs from my system (not sure if you fine ladies and gentlemen need it but some times you just can't have enough information right?):
dennis@dennis-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network:0 
description: Wireless interface
product: AR2413 802.11bg NIC
vendor: Atheros Communications, Inc.
physical id: 5
bus info: pci@0000:06:05.0
logical name: wlan0
version: 01
serial: 00:16:ce:6b:c0:0d
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.49+,06/21/2007,5.3.0.56 latency=128 maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
*-network:1
description: Ethernet interface
product: RTL-8169 Gigabit Ethernet
vendor: Realtek Semiconductor Co., Ltd.
physical id: 7
bus info: pci@0000:06:07.0
logical name: eth0
version: 10
serial: 00:16:d3:43:64:e2
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.101 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

I should also add that I am a brand new user of Ubuntu and Linux generally and love it.  If this darn wireless will work I will probably wipe my hard drive again and only use Ubuntu from here on out (at home anyway).

Thanks in advance ...

---

### Post by DennisMonague on 2007-11-06
One last footnote before I leave it to the pro's. Like I mentioned earlier I did successfully install ndiswrapper and the Gnome associated with same and now under System>Administration>Network a wireless connection is listed and is noted as roaming mode enabled. As well, System>Administration>Network Tools I can change to Wireless Interface (wlan0). Finally, in the little network icon on the desktop, if clicked will say i can do a bunch of stuff like connect and create wireless networks.

---

### Post by aavikkosorsa on 2007-11-13
Hey!!

Use Synaptic package manager to install "acer-acpi" and "acerwificontroller" packagets!!!
After installing reboot your system and your radio button should now light up. Try your wireless connection, if it's not working try rebooting once more.

I have same problem in same Acer aspire 5044wlmi ("5040")  laptop and i get it work installing those acer packagets. My wifi is working now but i have to boot my computer twice every time to get wireless connection!

Sorry my bad english, hope this helps you:)

---

### Post by DennisMonague on 2007-11-14
I tried your suggestion and it didn't work.  Are you running 7.10?  I have been playing around with all the suggestions in the forums, perhaps I need a clean install?  By the way thanks for responding I'll try a clean install and let you know what happens.

---

### Post by aavikkosorsa on 2007-11-14
yes, i'm runnig 7.10. I upgrade from clean installed 7.04.

---

### Post by aavikkosorsa on 2007-11-14
Here's what i get from command "lshw -C network"

it's a bit different.

lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: wifi0
       version: 01
       serial: 00:16:cf:29:0e:17
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes [COLOR="red"]driver=ath_pci [/COLOR]ip=xxx.xxx.x.xxx latency=168 maxlatency=28 mingnt=10 [COLOR="red"]module=ath_pci[/COLOR] multicast=yes wireless=IEEE 802.11g

I hope that clean install helps you.

---

### Post by DennisMonague on 2007-11-27
Thank you very much for your help on this.  I did a fresh install (actually I completely wipped my dual boot xp and ubuntu) of ubuntu with a hard drive reformat just to make sure I was starting with a clean slate.  I then followed your directions and it worked!

Well almost.  I can now see all the wireless networks around me, my light is on.  The problem is that I can't seem to make it connect to anything.  Have you had this problem before?

---

### Post by aavikkosorsa on 2007-12-04
Sounds very strange, i dont rememper  to ever had that connection problem. Have you tried to connect different networks??? 

Only problem i have is this same reboot problem:
[HTML] http://ubuntuforums.org/showthread.php?p=3888793#post3888793 [/HTML]

I think you are now close to get solution for your wifi problems, keep up the work. :)

---

### Post by DennisMonague on 2007-12-04
I solved it!!!!! YAY!!!! Well actually what you said about turning on then having to restart solved it.  And I think I found out why we (me and you, that is if you still have to do a this) have to do that restart to make the wireless work.  

It seems that when I turn the laptop on "fresh" the wireless card has to do a start up.  This start up happens after Ubuntu tries to do a wireless network sensor sweep.  So Ubuntu figures that there are no wireless networks and defaults to the wired configuration.  Now when a restart is done the wireless card doesn't actually shut down, so now it's on when Ubuntu does the wireless sensor sweep and finds wireless networks in range, so it _doesn't_ default to the wired connection configuration.  I actually found a post (have since lost it and can't find again) that tells you how to make Ubuntu do a new sweep (maybe it just resets the configuration to make wireless work again .... not to sure, I'm just learning the new Linux language and processes) without having to restart.  

I'll pass that on if I find it again.  

Thank you very much with your help through all this.

---

### Post by aavikkosorsa on 2007-12-09
I solve it too :)

[http://ubuntuforums.org/showthread.php?p=3922467#post3922467](http://ubuntuforums.org/showthread.php?p=3922467#post3922467)

 I would like to hear how you solve it Dennis if find that post??

---

### Post by charmint on 2007-12-09
where did u find this wrapper? i need one but only for mint

---

### Post by aavikkosorsa on 2007-12-10
I have newer used Mint but in Ubuntu i use Synaptic to install.

here's some links which could help you

NDISwrapper home:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/)

[http://www.linuxmint.com/wiki/index.php/MintWifi#3_Load_ndiswrapper](http://www.linuxmint.com/wiki/index.php/MintWifi#3_Load_ndiswrapper)

[http://linuxmint.com/forum/](http://linuxmint.com/forum/)

---

### Post by charmint on 2007-12-10
well mint has a built in warrper (just found it) but now i cant find drivers!

---

### Post by aavikkosorsa on 2007-12-11
i find my driver from acer's site 
[http://support.acer-euro.com/drivers/notebook/as_5040.html](http://support.acer-euro.com/drivers/notebook/as_5040.html)

If your have same atheros Wireless card that i have you can use this link.

---

### Post by sporkubus on 2007-12-12
I did everything as you said, but when I go to load this driver (I have the AR5005G with the Aspire 5100laptop) ndiswrapper tells me that it's an Invalid driver and the wireless is still not enabled. Is there any way to get past this?

---

### Post by aavikkosorsa on 2007-12-13
It seems that the driver is wrong!!

> i find my driver from acer's site
[http://support.acer-euro.com/drivers...k/as_5040.html](http://support.acer-euro.com/drivers...k/as_5040.html)
Did you use this link to get driver??? If did, it's wrong for your system, this is the right one for Acer 5100: [http://support.acer-euro.com/drivers/notebook/as_5100.html](http://support.acer-euro.com/drivers/notebook/as_5100.html)  ---->  MS Windows XP ------> Wireless Atheros_V5.3.0.67......!

If that driver wont work try  MS Windows XP ------> Wireless Lan Driver 802bg Broadcom Ver.4.10......!

---

### Post by sporkubus on 2007-12-13
Wow, this kind of worked! I thought it was the AR5005G card because that's what Windows Device Manager says I have, but I loaded this driver up in ndiswrapper and it says "Hardware present: Yes" But now how do I actually configure it and get it to detect connections?

---

### Post by aavikkosorsa on 2007-12-14
I dont think you need to configure it. I didn`t, i just use gnome networks manager to choose wireless network to connect. You may need to turn wired connection off to make wireless work. You can use network manager also to do this!

If you dont have gnome network manager, u can install it or some other networking manager  using synaptic.

About gnome network manager:
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

alternative network manager
[http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

---

### Post by sporkubus on 2007-12-14
How do I turn the wired connection off? It stil doesn't seem to be working...

---

### Post by sporkubus on 2007-12-15
So I got the driver to install, and now when I go to Network Settings I see "Wireless connection" but I don't know what to do with that. In Windows, it just automatically picks up a bunch of connections and lists them, but its not doing that here, so I'm not sure what I have to do to get it to connect to a wireless network...

---

### Post by sporkubus on 2007-12-15
And now I rebooted and the Wireless connection is gone from the network manager... can someone please PLEASE explain to me what I'm doing wrong???

---

### Post by aavikkosorsa on 2007-12-18
> And now I rebooted and the Wireless connection is gone from the network manager... can someone please PLEASE explain to me what I'm doing wrong???

To load nDiswrapper everytime system starts

```
sudo gedit /etc/modules
```

add ndiswrapper

Like this

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
acer_acpi
ndiswrapper
```

---

