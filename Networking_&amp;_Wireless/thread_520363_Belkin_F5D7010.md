---
title: "Belkin F5D7010"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by yashoda on 2007-08-08
Hi,

I'm new to Ubuntu.

I have a Belkin F5D7010.

I got into Administration, and Network.

If I click "Enable Roaming" then my Belkin card goes off, if I configure it to my network - with the wireless network name, and the WEP key, then both lights on the belkin wireless card come on, and it shows that it's receiving a signal.

However, when I try to go online, it's not actually going on.  and the network icon next to POWER icon just says Manual Network.

How to get it to go online?  I've read the documentation, and tried stuff on my own before trying the forum.

Please help.

---

### Post by noob12 on 2007-08-08
Can you post the results of these
```

sudo lshw -C network

cat /etc/network/interfaces

iwconfig

iwlist scan

```

---

### Post by yashoda on 2007-08-09
lshw -C network shows:

*-network
desecription: Ethernet interface
product:RTL-8139/8139C/8139C+
VENDOR: Realtek Semiconductor Co., Ltd.
physical id: 12
bus info: pci@00:12.0
logical name: eth0
version:10
serial: 08.00:46:c0:cf:9d
width: 32 bits
clock:33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 max latency=64 mingnt=32 multicast=yes
resources; ioport: 9c00-9cff iomemory:e0404dff irq:11


*-network
description: Wireless interface
product: RT2500 802.11g Cardbus/mini-PCI
vendor: RaLink
physical id: 0
bus info: pci@02:00.0
logical name: ra0
version: 01
serial: 00:11:50:66:a8:52
width: 32bits
clock: 33MHz
capabilities bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=RT2500 DRIVERVERSION=1.1.0 beta4 LATENCY=64 MULTICAST=YES WIRELESS=rt2500 Wireless
resources:iomemory: 24000000-24001fff irq:11


iwlist scan shows:

lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

ra0 Scan completed

(then lists various cells til it comes to my network)

Cell 06 Address 00:11:50:42:5F:1E
Mode: Managed
ESSID:"belkin54g"
Encryption key: on
Channel: 11
Quality: 68/100 Signal level-53dBm Noise level: 193dBm



/etc/network/interfaces: Permission denied.




here's the ifconfig

eth0
Link encap: ethernet HWaddr 08:00:46:c0:cf:9d
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX PACKETS, ERRROS, DROPPED, OVERRUNS, FRAME, TXPACKETS, ERRORS, DROPPED, OVER RUNS, CARRIER, COLLISIONS ALL zero
TXQUEUELEN:1000
RX bytes: 0 TX bytes: 0
Interrupt:11 base address 0xec00

eth0:avah Link encap: Ethernet HWaddr 08:00:46:c0:CF:9D
INET ADDR:169.254.9.26 bCAST:169.254.255.255 mASK:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interupt:11 Base address: 0xec00


lo
link encap:local loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric: 1
RX PACKETS:112 errors:0 dropped:0 overruns:0 frame:0
TX packets:112 ERROS:0 DROPPED:0 OVERRUNS:0 CARRIER:0
COLLISIONS:0 TXQUEUELEN:0
RX bytes:8488 (8.2 KiB) TX bytes: 8488 (8.2 kib)

ra0
Link encap: Ethernet HWaddr 00:11:50:66:A8:52
inet6 addr: fe80: :211:50ff:fe66:a852/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:569 erors:0 dropped: 0 overruns:0 frame:0
TX packets:123754 errors:0 dropped:0 overruns:0 carrier:0
collisions:6 txqueuelen:1000
RX bytes:67241 (65.6 KiB) TX bytes: 5613782 (5.3 MiB)
Interrupt:11 Base address:0xc000
__________________


The iwconfig shows:

lo   no wireless extensions

eth0 no wireless extensions

ra0   RT2500 Wireless ESSID:""
Mode:Managed  Frequency=2.412GHz Bit Rate:54 Mb/s  Tx-Power:0 dBm
RTS thr:off Fragment thr:off
Link Quality=70/100  Signal level=-50 dBm  Noise level:-193 dbn
Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
TX excessive retries:0   Invalid misc:0   Missed beacon:0

---

### Post by noob12 on 2007-08-09
It sounds like you almost have it working.  When you put it in roaming mode, the NetworkManager will try to manage it based on its settings; you say it turns off.   That is probably because you don't have it enabled in the NetworkManager.  If you right-click on the NetworkManager icon (the little dual computer in the notification area --usually in the top right area of the desktop), you should see an Enable Wireless option.  Select it to make sure the checkbox is on.  Then left-click on the NetworkManager icon.  You'll then see a list of nearby radio signals.  Select the bar representing yours so that it appears selected.  You should then get prompted to enter your WEP key.

You may get prompted to choose a keyring password.  The keyring holds all of your network keys and is protected by a single password.  This isn't the WEP key.  Choose a password you'll remember.  Most people use the same password as for their login.

Try this and let me know what happens.

Note: the command to show /etc/network/interfaces failed because you didn't type **cat** in front of the filename.  I may need to see that if you have problems.

---

### Post by Austin_KW on 2007-08-09
Alternativey, You may want to configure your card using /etc/network/interfaces (you will have to, if your upgrade your security to WPA) as the rt2500 legacy drivers do not work well with networkmanager.

To configure for WPA; Change the ra0 entry in /etc/network/interfaces as follows
```
auto ra0
iface ra0 inet dhcp
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid belkin54g
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwconfig ra0 essid belkin54g
    pre-up iwpriv ra0 set  WPAPSK="YourWPAkeyHere"

```

To configure for WEP; Change the ra0 entry in /etc/network/interfaces  as follows
```
auto ra0
iface ra0 inet dhcp
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid belkin54g
    pre-up iwconfig ra0 key YourWEPkeyHere

```


After making the change "sudo ifup --f ra0" should bring your wireless network up, It should then automatically come up on boot

---

### Post by yashoda on 2007-08-09
Dear Noob12 and Austin_KW, thank you so very, very much!!!

I've been trying Ubuntu for a few years now, and I'd always hit a wall, and quit.  reverting to windows.

Thanks to the two of you, those days are OVER!!! 

the biggest hurdle has been configuring this wireless network.

I was doing what noob12 had been saying, but Austin - you took it to the finish line!

Honestly, I am in your debt!

THANKS AGAIN!!!

This spirit of Ubuntu is awesome!

---

### Post by yashoda on 2007-08-09
Guys, I'm sending this message from my laptop running Ubuntu!!

btw, 1 last question (for now):

do i take it for granted that the connection established through these guidelines is an encrypted connection?

thanks!

---

### Post by Austin_KW on 2007-08-09
> **yashoda said:**
> Guys, I'm sending this message from my laptop running Ubuntu!!

btw, 1 last question (for now):

do i take it for granted that the connection established through these guidelines is an encrypted connection?

thanks!
Glad you are up and running,

"iwlist scan" should tell you if the access point has encryption turned on.
Or you could enter a wrong key and it should fail to connect. Use "sudo ifup --f ra0" to re0init the connection after ant change to the interfaces file. 

btw, you should be using WPA-PSK encryption with a password of at least 20 characters; Most WEP can be hacked in 2 minutes.

---

### Post by noob12 on 2007-08-10
Great to hear you have it working.  If you tend to be in one place (one wireless net) almost all of the time, manual configuration works just fine.  If you use it multiple places, home, school, work, in coffee shops and the like, maintaining things manually can be a pain, and you will want to use something like NetworkManager or wicd.

I agree with Austin_KW about WPA. If you use it, you'll need to install wpasupplicant.  I'd recommend doing this anyway if you want to be able to connect to other people's networks that do use WPA.

---

### Post by yashoda on 2007-08-10
Thanks you-all!

see, I'm not an IT person... obviously...

when I use windows, and wanna connect to the wireless network, it scans, and I enter the WEP key, and then a password.

now, when I just configure for WEP, as outlined above, it all works great! (i presume that, say if I'm at a hotel, I can access the hotel's wifi signal by changing to ENABLE ROAMING, and selecting the network?)

However, if I try to configure for WPA, it doesn't work.

so, I guess I have to just stick to the WEP configuration?

i'm starting to feel liberated - no more Evil Empire - and you 2 r the facilitators of this!!!!
Thanks!

---

### Post by noob12 on 2007-08-10
The following will install the wpasupplicant package.  This should allow you to use WPA as long as the driver/device does.   The NetworkManager will automatically prompt and configure this for you if you are associating with a WPA provider.
```

sudo aptitude install wpasupplicant

```

If you have trouble with the wireless, you may find that using the current drivers from rt2x00.serialmonkey.com improves things.  People on the forum can help with that if you need it.

---

### Post by Austin_KW on 2007-08-10
> **noob12 said:**
> The following will install the wpasupplicant package.  This should allow you to use WPA as long as the driver/device does.   The NetworkManager will automatically prompt and configure this for you if you are associating with a WPA provider.
```

sudo aptitude install wpasupplicant

```

If you have trouble with the wireless, you may find that using the current drivers from rt2x00.serialmonkey.com improves things.  People on the forum can help with that if you need it.

The legacy driver rt2500 uses it own built in wpa supliciant, not the general wpasupplicant. The newer beta drivers (rt2500pci et al) use the wpasupplicant but these do not work on ubuntu. You should be able to use WPA with the rt2500 driver (for wpa with TKIP or AES but nnot WPA2).

---

### Post by noob12 on 2007-08-10
Oh.  Thanks for that info.

---

### Post by imdano on 2007-08-10
Both the standard rt drivers and enhanced legacy rt drivers from serialmonkey use a series of iwpriv commands to connect to WPA networks.  Supposedly the new rt2x00 drivers (also from serialmonkey) will work with wpa_supplicant.  Not sure if they do or not.

See [this thread](http://ubuntuforums.org/showthread.php?t=400236) for more info on the process of connecting with the legacy drivers.

---

### Post by amitab09 on 2007-08-14
I just wanted to thank the people who contributed to this post. It really helped me to get my belkin card going.

Thank you thank you thank you. I can use Ubuntu properly now.

:)

---

### Post by nickmcg on 2007-08-15
> **imdano said:**
> Both the standard rt drivers and enhanced legacy rt drivers from serialmonkey use a series of iwpriv commands to connect to WPA networks.  Supposedly the new rt2x00 drivers (also from serialmonkey) will work with wpa_supplicant.  Not sure if they do or not.

See [this thread](http://ubuntuforums.org/showthread.php?t=400236) for more info on the process of connecting with the legacy drivers.

The rt2x00 do work - they are in gutsy, which I am now using. I couldn't get them to build in feisty as (I think) I would have had to build a new kernel.

Nick

---

### Post by yashoda on 2007-10-30
Hi You-all,

I just want to thank all those who contributed to this thread.

just fyi:  the belkin card works out of the box with gutsy, and easily configures to my wireless network!

so... if you're still stuck, do a fresh install with gutsy!

(not only that, but the ATI card of my laptop works, with special effects, 3d, etc, etc!)

---

### Post by Austin_KW on 2007-10-30
> **yashoda said:**
> Hi You-all,

I just want to thank all those who contributed to this thread.

just fyi:  the belkin card works out of the box with gutsy, and easily configures to my wireless network!

so... if you're still stuck, do a fresh install with gutsy!

(not only that, but the ATI card of my laptop works, with special effects, 3d, etc, etc!)

Check the performance of your driver (rt2500pci)on gutsy. After a short time my throughput is limited to 1/2Mbs and never recovers. I have gone back to the legacy driver.  Your performance may vary but check it.

---

