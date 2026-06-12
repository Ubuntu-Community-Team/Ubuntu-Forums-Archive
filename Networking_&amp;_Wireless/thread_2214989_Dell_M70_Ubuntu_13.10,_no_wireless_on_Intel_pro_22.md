---
title: "Dell M70 Ubuntu 13.10, no wireless on Intel pro 2200bg card?"
date: 2014-04-04
forum: Networking &amp; Wireless
---

### Post by Slatez on 2014-04-04
Hi All,

Newbie to Ubuntu, loving it so far coming from Mac background! Dug out an old Dell Precision M70 laptop running old XP, did a clean install of Ubuntu 13.10, run updates, etc, etc. I have internet via Ethernet, but cannot get wireless to work? Read hours of forums posts, but yet to find anything that can help get wireless going again so far?

**Computer spec:**

Intel Pentium M 2.13Ghz
2Gb RAM
60Gb HDD
Intel Pro/Wireless 2200bg Card
Nvidia Quadro FX1400 Graphics Card

**I have found various info for the wireless issue, but not sure how to resolve it? Info found so far:**

Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


*-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:f9:6a:87
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 
       multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:dceff000-dcefffff

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

It would be great to try and get this working and I see Chilli55 seems to be pretty handy with helping other non-wireless sufferers out. Any help  with this matter would be truly appreciated.

Slatez

---

### Post by Hadaka on 2014-04-04
hi, here is a good link
[http://ubuntuforums.org/showthread.php?t=2079211](http://ubuntuforums.org/showthread.php?t=2079211)
you also have a hard block going on there...not good
please do and post..
```
rfkill list all
sudo rfkill unblock all
```
press the fn key (function) and the f2 key together...one time
*that is the keyboard toggle switch for the wireless card...
then do..
```
sudo modprobe -rf ipw2200
sudo modprobe ipw2200
```

---

### Post by Slatez on 2014-04-04
Hi Hadaka,
Thanks for the repsonse, much appreciated. I have tried your above suggestions to no avail and I tried various things as mentioned on the link, but again no luck.

This is what I received with:  **dmesg | grep ipw**

[   18.926952] libipw: 802.11 data/management/control stack, git-1.1.13
[   18.926958] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.037999] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   19.038004] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.100686] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   19.365735] ipw2200: Radio Frequency Kill Switch is On:
[   19.422478] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[   28.884572] ipw2200: Failed to send POWER_MODE: Command timed out.

The last line looks suspect, but I'm not sure what steps to take next?

Thanks again and other help would be appreciated?

---

### Post by chili555 on 2014-04-04
Please press Fn+F2 and run and post:```
rfkill list all
```Press the key combination again; run and post:```
rfkill list all
```Also please post:```
lsmod | grep wmi
```Thanks.

---

### Post by Slatez on 2014-04-04
Hi Chili555,

Fn+F2 on this laptop turns bluetooth on and off, but here the settings from the first part:

 rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

and 

snd_rawmidi            25094  1 snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    60790  12 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi

Thanks for responding it is appreciated. Have to go to a meeting soon, but I'll check back again later....

---

### Post by chili555 on 2014-04-04
Evidently Fn+F2 *also* controls wireless:> rfkill list all
0: phy0: [COLOR="#FF0000"]Wireless LAN[/COLOR]
Soft blocked: no
[COLOR="#FF0000"]Hard blocked: no[/COLOR]
1: hci0: Bluetooth
Soft blocked: no
Hard blocked: no

rfkill list all
0: phy0: [COLOR="#FF0000"]Wireless LAN[/COLOR]
Soft blocked: no
[COLOR="#FF0000"]Hard blocked: yes[/COLOR]
So once you switch the wireless on with Fn+F2, do you see networks when you click the Network Manager icon? ```
sudo iwlist eth1 scan
```

---

### Post by Slatez on 2014-04-04
Hi Chili555,

So once you switch the wireless on with Fn+F2, do you see networks when you click the Network Manager icon?

Just tried this and I no have wifi, brilliant, led lit up, dicsonnected ethernet, all good. 

Brilliant and thank you so much chili555.....

---

### Post by Slatez on 2014-04-04
Next is to get Google skethup running under Wine, black screens and all but I'll post in relevant forum.....

---

### Post by Hadaka on 2014-04-04
Hi, glad you are up and running!

Please mark this thread SOLVED

How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

start a NEW thread for your google/wine situation should you require help

**Thanks chili555 for the assist.

---

