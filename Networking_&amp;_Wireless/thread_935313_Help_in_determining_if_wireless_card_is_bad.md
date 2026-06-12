---
title: "Help in determining if wireless card is bad"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by Dragonbite on 2008-10-01
I have a broadcom wireless card which has worked for a while with the drivers, not ndiswrapper.  It was never perfect but it worked.

Recently it has not been working. In face it doesn't even show up my local router (or the neighbors') like it used to.

When I click on the Network Manager icon it doesn't show any wireless networks in the area at all.

I have tried turning it off and back on, rebooting, reapply the driver and nothing.

I have also booted up to a LiveCD session of Ubuntu and installed the drivers to see if it would show up there.  It didn't.

Are there any other checks I can do to determine if it is genuinely the card that is busted, or can try to troubleshoot/fix the card if it is like "stuck"?  (I know.. technical term here ;) )

Basically I am just hoping for some troubleshooting tips or tips on making sure the card is dead and needs replacement before going out and replacing it.

Oh, and I was able to see mine and the neighbor's network on my work laptop which is running Windows XP.

---

### Post by kestal on 2008-10-01
Need to know a few things. What Laptop? What Broadcom card is it?

What did you do to set it up? (I know you mentioned the drivers, but which ones? - there are a few methods which work with varying degrees).

Are you also on 32 bit or 64 bit?

---

### Post by Dragonbite on 2008-10-02
> **kestal said:**
> Need to know a few things. What Laptop? What Broadcom card is it?

What did you do to set it up? (I know you mentioned the drivers, but which ones? - there are a few methods which work with varying degrees).

Are you also on 32 bit or 64 bit?

Thank you for your response.

I have some of the information here, else I will have to get when I go home.  Is there a script that will give me more detail on the wireless card?

LAPTOP : Dell Latitude D400[LIST]
[*]Pentium M at 1.4GHz
[*]512 MB of Ram
[/LIST]

CARD : (from another site on D400 specs ) Dell TrueMobile 1300 WLAN Mini-PCI Card

UBUNTU : 32 bit Ubuntu 8.04 LTS

DRIVER : [LIST=1]
[*]I went to System > Administration > Hardware Drivers *(not sure if that's the right name)*
[*]It listed the Broadcom wi-fi, clicked to enable
[*]It downloaded the firmware and cutter
[*]Done
[/LIST]

Previously, after following these steps and waiting for a couple minutes I could click on the Network Manager icon on the panel and it lists the networks it detects in the area.

Currently it shows the card existing in hardware listing and Network Manager manual configuration.

When it first happened, I thought the issue could be in one of 3 locations:
[LIST]
[*]Router not sending signals (verified that it was with work's laptop)
[*]The card got misconfigured or otherwise software got changed (except it did not work when I booted to the Live CD and went through the same process)
[*]WiFi card is borked (which I truly hope not since I won't have the money to replace it for a while)
[/LIST]

---

### Post by Ayuthia on 2008-10-02
Does the card show up when you go into the Terminal and type:
```
lspci -nn
```
If it does, please post the results of:
```
lshw -C network
```

---

### Post by Dragonbite on 2008-10-02
for **lspci -nn** I got : 
```
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
01:01.0 CardBus bridge [0607]: Texas Instruments PCI7510 PC card Cardbus Controller [104c:ac47] (rev 01)
01:01.1 CardBus bridge [0607]: Texas Instruments PCI7510,7610 PC card Cardbus Controller [104c:ac4a] (rev 01)
01:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller [104c:802b]
01:01.3 System peripheral [0880]: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function [104c:8204]
**01:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 03)**

```

For **lshw -C network** the results are :

```
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:6e:e3:23
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5705-v3.11 ip=192.168.1.103 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:f5:0a:0e:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

Thank you again for helping me with this.

---

### Post by Ayuthia on 2008-10-02
Let's see what happens when you try the following:
```
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl
sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```
This will help us see what modules are loaded then it will remove any possible conflicting wireless modules, load the b43 module, bring up the card, and scan for wireless access points.

---

### Post by Dragonbite on 2008-10-05
> **Ayuthia said:**
> Let's see what happens when you try the following:


**lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl**
```
b43                   144420  0 
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  1 b43

```

**sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl**
```
*Nothing happened. It took my password and did nothing.*
```

**sudo modprobe b43**
```
*Now it won't even take my sudo password*

When I try it without "sudo" I get the following messages (which I assume is from not being sudo)

WARNING: Error inserting input_polldev (/lib/modules/2.6.24-19-generic/kernel/drivers/input/input-polldev.ko): Operation not permitted
WARNING: Error inserting led_class (/lib/modules/2.6.24-19-generic/kernel/drivers/leds/led-class.ko): Operation not permitted
WARNING: Error inserting cfg80211 (/lib/modules/2.6.24-19-generic/kernel/net/wireless/cfg80211.ko): Operation not permitted
WARNING: Error inserting mac80211 (/lib/modules/2.6.24-19-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted
WARNING: Error inserting ssb (/lib/modules/2.6.24-19-generic/kernel/drivers/ssb/ssb.ko): Operation not permitted
FATAL: Error inserting b43 (/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/b43/b43.ko): Operation not permitted

```

**sudo ifconfig wlan0 up**
```
wlan0: ERROR while getting interface flags: No such device

```

**sudo iwlist scan**
(Dragon is the name of the machine )
```
sudo: unable to resolve host Dragon
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```

---

### Post by Dragonbite on 2009-01-27
bump

---

### Post by Dragonbite on 2009-01-28
Still not resolved! Argh!

I have gotten another wireless card and still nothing is working.
+--------------------------------------------------------+

```
lsmod | grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl
```
Which looks for all modules (listed after the -e).  For this chip it should be b43 and ssb but **not** bcm43xx!
```
wl                   1062164  0 
ieee80211_crypt         7040  1 wl
b43                   144420  0 
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  1 b43
```
+--------------------------------------------------------+

```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
```
This line removes the modules. If done properly, nothing should happen except the prompt returns. Running the "lsmod|grep" likewise should show nothing because you just removed those modules 
+--------------------------------------------------------+

```
sudo modprobe b43
```
This line installs / turns "on" the b43 module/driver. Like above it should not do anything rather than give you another prompt.  Running the "lsmod|grep" code above returns
```
b43                   144420  0 
ssb                    34308  1 b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
rfkill                  8592  3 b43,rfkill_input
``` looks familiar doesn't it ;)
+--------------------------------------------------------+

```
sudo ifconfig wlan1 up
```
This line turns on the network connection wlan1 (usually it is wlan0 but for whatever reason this is showing up as wlan1 for me).  Like above, nothing should happen. When I try to turn on wlan0, this is what I get;
```
wlan0: ERROR while getting interface flags: No such device 
```
+--------------------------------------------------------+

```
sudo iwlist scan
```
This scans and returns all of the access points the card detects. As you can see, nothing is found and I know my router is broadcasting and so is at leat one neighbor's I can usually see.
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan1     No scan results
```
+--------------------------------------------------------+

So now I'm stuck with WHAT THE ________ TO DO!!

---

### Post by Ayuthia on 2009-01-28
> **Dragonbite said:**
> Still not resolved! Argh!

I have gotten another wireless card and still nothing is working.
+--------------------------------------------------------+

```
lsmod | grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl
```
Which looks for all modules (listed after the -e).  For this chip it should be b43 and ssb but **not** bcm43xx!
```
wl                   1062164  0 
ieee80211_crypt         7040  1 wl
b43                   144420  0 
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  1 b43
```
+--------------------------------------------------------+

```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
```
This line removes the modules. If done properly, nothing should happen except the prompt returns. Running the "lsmod|grep" likewise should show nothing because you just removed those modules 
+--------------------------------------------------------+

```
sudo modprobe b43
```
This line installs / turns "on" the b43 module/driver. Like above it should not do anything rather than give you another prompt.  Running the "lsmod|grep" code above returns
```
b43                   144420  0 
ssb                    34308  1 b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
rfkill                  8592  3 b43,rfkill_input
``` looks familiar doesn't it ;)
+--------------------------------------------------------+

```
sudo ifconfig wlan1 up
```
This line turns on the network connection wlan1 (usually it is wlan0 but for whatever reason this is showing up as wlan1 for me).  Like above, nothing should happen. When I try to turn on wlan0, this is what I get;
```
wlan0: ERROR while getting interface flags: No such device 
```
+--------------------------------------------------------+

```
sudo iwlist scan
```
This scans and returns all of the access points the card detects. As you can see, nothing is found and I know my router is broadcasting and so is at leat one neighbor's I can usually see.
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan1     No scan results
```
+--------------------------------------------------------+

So now I'm stuck with WHAT THE ________ TO DO!!

What is the chipset for the other Broadcom card (lspci -nn)?  I am noticing that your information this time includes the wl module.  That one does not support the 4309 card so I am guessing that it is not a 4309 card.

---

### Post by Dragonbite on 2009-01-28
> **Ayuthia said:**
> What is the chipset for the other Broadcom card (lspci -nn)?  I am noticing that your information this time includes the wl module.  That one does not support the 4309 card so I am guessing that it is not a 4309 card.

I'll have to run that when I get home. When I ran it last night I thought it came up with the same "01:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 03)" but I'll verify.

Oh, and I looked at the /etc/modprobe.d/blacklist and see that bcm43xx is blacklisted and the comment says it is replaced by b43 and ssb.

Thank you for responding.

---

### Post by Dragonbite on 2009-01-29
> **Ayuthia said:**
> What is the chipset for the other Broadcom card (lspci -nn)?  I am noticing that your information this time includes the wl module.  That one does not support the 4309 card so I am guessing that it is not a 4309 card.

Ok, here's the result of lspci -nn after no fussing with anything
```
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
01:01.0 CardBus bridge [0607]: Texas Instruments PCI7510 PC card Cardbus Controller [104c:ac47] (rev 01)
01:01.1 CardBus bridge [0607]: Texas Instruments PCI7510,7610 PC card Cardbus Controller [104c:ac4a] (rev 01)
01:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller [104c:802b]
01:01.3 System peripheral [0880]: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function [104c:8204]
01:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 03)

```

Just to take a look at it, I tried  
lsmod | grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl
```
b43                   144548  0 
rfkill                  8596  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  1 b43
```

any ideas?

---

### Post by Ayuthia on 2009-01-29
> **Dragonbite said:**
> Ok, here's the result of lspci -nn after no fussing with anything
```
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
01:01.0 CardBus bridge [0607]: Texas Instruments PCI7510 PC card Cardbus Controller [104c:ac47] (rev 01)
01:01.1 CardBus bridge [0607]: Texas Instruments PCI7510,7610 PC card Cardbus Controller [104c:ac4a] (rev 01)
01:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller [104c:802b]
01:01.3 System peripheral [0880]: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function [104c:8204]
01:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 03)

```

Just to take a look at it, I tried  
lsmod | grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl
```
b43                   144548  0 
rfkill                  8596  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  1 b43
```

any ideas?

The only things that I can think of right now is to check dmesg|grep b43 to see if there are any error messages there.  The other thing that you can try is to install the older firmware to see if it works:
[http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43)

I am not for sure about if you know how to do this or not.

---

### Post by Dragonbite on 2009-01-29
> **Ayuthia said:**
> The only things that I can think of right now is to check dmesg|grep b43 to see if there are any error messages there.  The other thing that you can try is to install the older firmware to see if it works:
[http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43)

I am not for sure about if you know how to do this or not.

Do you think using ndsiwrapper would make any difference?

---

### Post by Ayuthia on 2009-01-29
> **Dragonbite said:**
> Do you think using ndsiwrapper would make any difference?

It is possible that it might make a difference.

If you were using Hardy and was able to get the card to work back then and you still have the live CD for it, can you test it out to see if it works?  I am still trying to figure out if the issue is with the b43 module or if it is with Network Manager.

---

### Post by Dragonbite on 2009-01-29
> **Ayuthia said:**
> It is possible that it might make a difference.

If you were using Hardy and was able to get the card to work back then and you still have the live CD for it, can you test it out to see if it works?  I am still trying to figure out if the issue is with the b43 module or if it is with Network Manager.

I'm planning on doing that with this new card, but when I tried it before it detected it and I turned it on via the Hardware Drivers application but it sitll didn't do anything.  

This is one reason why I thought it was the card in the first place since the LiveCD would not have had any configuration changes that could have occured in the installed system.

Would it be better to try it with the Hardy LiveCD or Intrepid? I hear that Intrepid might have more wireless stuff but Hardy is what I have on the system at this time.

---

### Post by Ayuthia on 2009-01-29
I was thinking that you were on Intrepid.  You can try using the Intrepid CD to see if it makes a difference.  If I recall correctly Network Manager gets upgraded to 0.7 in Intrepid, but it has been having its ups and downs.

---

### Post by Dragonbite on 2009-01-29
> **Ayuthia said:**
> The only things that I can think of right now is to check dmesg|grep b43 to see if there are any error messages there.  The other thing that you can try is to install the older firmware to see if it works:
[http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43)

I am not for sure about if you know how to do this or not.

Running **dmesg|grep b43** I get :
```
[   26.684162] b43-phy0: Broadcom 4306 WLAN found
[   26.704879] b43-phy0 debug: Found PHY: Analog 2, Type 2, Revision 2
[   26.704902] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   37.633216] input: b43-phy0 as /devices/virtual/input/input11
[   66.342349] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   38.920646] b43-phy0 debug: Chip initialized
[   38.921094] b43-phy0 debug: 30-bit DMA initialized
[   38.923137] Registered led device: b43-phy0:tx
[   38.923406] Registered led device: b43-phy0:rx
[   38.923552] Registered led device: b43-phy0:radio
[   38.923582] b43-phy0 debug: Wireless interface started
[   90.925870] b43-phy0 debug: Adding Interface type 2
[   63.935920] b43-phy0 debug: Removing Interface type 2
[   63.993043] b43-phy0 debug: Wireless interface stopped
[   63.993167] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 0/64
[   63.993235] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[   64.000262] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[   64.008014] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[   64.015889] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[   64.023901] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 2/128
[   64.031867] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[    2.859823] b43-phy0: Broadcom 4306 WLAN found
[    2.883726] b43-phy0 debug: Found PHY: Analog 2, Type 2, Revision 2
[    2.883751] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[    3.145721] input: b43-phy0 as /devices/virtual/input/input15
[    3.311705] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[    4.192123] b43-phy0 debug: Chip initialized
[    4.192735] b43-phy0 debug: 30-bit DMA initialized
[    4.195129] Registered led device: b43-phy0:tx
[    4.195380] Registered led device: b43-phy0:rx
[    4.195528] Registered led device: b43-phy0:radio
[    4.195591] b43-phy0 debug: Wireless interface started
[    4.243839] b43-phy0 debug: Adding Interface type 2
[    5.051490] b43-phy0 debug: Removing Interface type 2
[    5.091628] b43-phy0 debug: Wireless interface stopped
[    5.091741] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 0/64
[    5.091800] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[    5.099500] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[    5.107472] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[    5.115477] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[    5.127453] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 0/128
[    5.137503] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[    5.730899] input: b43-phy0 as /devices/virtual/input/input16
[    5.865737] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[    6.715475] b43-phy0 debug: Chip initialized
[    6.716041] b43-phy0 debug: 30-bit DMA initialized
[    6.718220] Registered led device: b43-phy0:tx
[    6.718465] Registered led device: b43-phy0:rx
[    6.718611] Registered led device: b43-phy0:radio
[    6.718641] b43-phy0 debug: Wireless interface started
[    6.755468] b43-phy0 debug: Adding Interface type 2

```

---

### Post by Ayuthia on 2009-01-29
The info in dmesg looks ok. Can you try it in Intrepid?  It is using newer firmware so maybe you will get a different result.  There is still a part of me that feels that it might be Network Manager related just because there are no relevant error messages.

---

### Post by Dragonbite on 2009-01-30
> **Ayuthia said:**
> The info in dmesg looks ok. Can you try it in Intrepid?  It is using newer firmware so maybe you will get a different result.  There is still a part of me that feels that it might be Network Manager related just because there are no relevant error messages.

Are there any alternative applications for Network Manager?  Different DE or otherwise?

I'll try the Intrepid when I am able to and I'll also see about trying the openSUSE LiveCD I have since they may go about it in a different manner or something.

Thank you again for all your help!  At least it's giving me something to try and look at before I find out how well a laptop doubles as a frisbee :)

---

### Post by Ayuthia on 2009-01-30
> **Dragonbite said:**
> Are there any alternative applications for Network Manager?  Different DE or otherwise?

I'll try the Intrepid when I am able to and I'll also see about trying the openSUSE LiveCD I have since they may go about it in a different manner or something.

Thank you again for all your help!  At least it's giving me something to try and look at before I find out how well a laptop doubles as a frisbee :)

You can try [wicd]("http://wicd.sourceforge.net/download.php").  It is a popular alternative to Network Manager.

Please let us know how it works in openSUSE.

---

### Post by ittiam on 2009-01-30
knetworkmanager is also good.

---

### Post by Dragonbite on 2009-01-30
> **ittiam said:**
> knetworkmanager is also good.

**knetworkmanager** isn't just a KDE wrapper for Network Manager?

---

### Post by ittiam on 2009-01-30
Yes, you are right. For some reason that I cannot explain, at least for knetworkmanager connects nicely when networkmanager does not. Just suggesting one more option. Anyway I prefer using wpa_supplicant.

---

### Post by Dragonbite on 2009-01-30
Ok, I'm doing this from 8.10 LiveCD. Here are the results: ```
ubuntu@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
01:01.0 CardBus bridge [0607]: Texas Instruments PCI7510 PC card Cardbus Controller [104c:ac47] (rev 01)
01:01.1 CardBus bridge [0607]: Texas Instruments PCI7510,7610 PC card Cardbus Controller [104c:ac4a] (rev 01)
01:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller [104c:802b]
01:01.3 System peripheral [0880]: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function [104c:8204]
01:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 03)
```
```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:6e:e3:23
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5705-v3.11 ip=192.168.1.103 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:79:b5:14:b3:cd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:f5:0a:0e:4b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```
```
ubuntu@ubuntu:~$ lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl
b43                   131356  0 
rfkill                 17176  3 rfkill_input,b43
mac80211              216820  1 b43
led_class              12164  1 b43
input_polldev          11912  1 b43
ssb                    40580  1 b43

```
After running ```
ubuntu@ubuntu:~$ sudo ifconfig wlan0 up

``` I get ```
ubuntu@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```

So, this doesn't look very good. :(

---

### Post by Dragonbite on 2009-02-02
Alright, alright. I admit it!  I'm DUMB! 

The person who gave me the card was surprised to find I was having a problem and asked a simple question... is it turned on?  

Sure enough, it was disabled in the BIOS and once I turned it on in there it immediately picked up the access point when I rebooted!

Thank you, thank you for your patience and help.  It is not wasted because I am using some of the tool we tried with people in my SIG with wireless issues!

Thank you again!

---

