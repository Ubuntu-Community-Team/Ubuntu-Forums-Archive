---
title: "WICD not detecting my wireless network"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by jimjesus on 2008-05-03
So I was having troubles getting wireless and wired to work on ubuntu so I installed the WICD manager. Now I can get wired to work just fine but for some reason, its not detecting my wireless network. All the other laptops in my house that use windows can see the network just fine but wicd just isn't seeing it, it says "no wireless networks found". Perhaps its not detecting my wireless card. How do I get it to see my wireless network?

---

### Post by Whiffle on 2008-05-03
Go to Preferences and make sure that the wireless interface option is set to your wireless interface.  The command "iwconfig" will tell you which it is, it should be like wlan0, or eth1, or ath0, or something similar.

---

### Post by jimjesus on 2008-05-03
Well iwconfig outputs

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"1337"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And my wicd has the wireless interface set to wlan0. It still isn't detecting my wireless network though. could it have anything to do with wireless supplicant driver?

---

### Post by Whiffle on 2008-05-03
Try doing:

sudo iwlist wlan0 scan


Try it several times in fact, I know my wireless tends to be a little slow on the startup.  I generally have to click the "refresh" button in WICD a few times to get a list.

---

### Post by ugm6hr on 2008-05-03
Did you ever get your wifi to work pre-Wicd?

The following info would be useful (NB. capital C):
```
lshw -C network
```

---

### Post by jimjesus on 2008-05-03
Well I tried sudo iwlist wlan0 scan and it said:
```
wlan0     Interface doesn't support scanning : Network is down
```


And no I never got it to work before wicd, actually my wired wouldn't even work pre-wicd. I tried that command and it said I should run it as a super user but it gave me an output anyway, and in that there was something interesting.

 ```
*-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:46:e7:a8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

It appears as though my wireless card is disabled, though I'm not sure if that is the case.

---

### Post by ugm6hr on 2008-05-03
> **jimjesus said:**
> It appears as though my wireless card is disabled, though I'm not sure if that is the case.

This info now (assuming it is a PCI wifi card):
```
lspci
```

---

### Post by Whiffle on 2008-05-03
Just on a hunch, try "ifconfig wlan0 up", then try the iwlist command again.

---

### Post by jimjesus on 2008-05-03
The lspci command output:
```

00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
```

It's a laptop, so I don't know if it is a pci wireless card or not.

When I tried  ifconfig wlan0 up it said:

```
SIOCSIFFLAGS: Permission denied
```

---

### Post by Whiffle on 2008-05-03
Oh I'm sorry, I should have said

sudo ifconfig wlan0 up

---

### Post by jimjesus on 2008-05-03
Oh that  is silly of me. I should have known to do that on my own. I have had ubuntu long enough to know that.

Alright it just says:
```
SIOCSIFFLAGS: No such file or directory
```

---

### Post by Whiffle on 2008-05-03
Looks like the drivers for your broadcom aren't working, or maybe even installed.  If I had any experience with these broadcoms i'd recommend a howto, but I don't know which ones are good...

---

### Post by jimjesus on 2008-05-03
Hmm alright. I really need to get this internet to work. This annoying me, haha.

---

### Post by Whiffle on 2008-05-03
Here give this a shot:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by ugm6hr on 2008-05-03
```
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

```

If you get online with wired - you should be able to enable fwcutter in Hardware / Restricted Drivers.

Which version of Ubuntu are you using?

---

### Post by jimjesus on 2008-05-03
Well I do have the kind of device stated, unfortunately it didn't tell me useful. I still can't get any of this to work.

I am also using ubuntu 8.04 and in hardware drivers it says no propritary drivers are in use and the list is empty.

---

### Post by Ayuthia on 2008-05-04
Since it is now showing up, you can install b43-fwcutter.  It will bring up a screen asking if you want it to have it find the firmware for you.  If you have a working internet connection, say yes and it should take of it for you.

---

### Post by jimjesus on 2008-05-04
Its finally working, thank you to everyone who helped me fix this. I think the fwcutter driver is what finally fixed it.

---

