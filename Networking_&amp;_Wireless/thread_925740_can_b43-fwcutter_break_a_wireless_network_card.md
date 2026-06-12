---
title: "can b43-fwcutter break a wireless network card?"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by Taollan on 2008-09-21
It appears that b43-fwcutter has broken not one, but two of my bcm 4306 wireless cards in two Gateway 7405GX laptops. 
Here is what leads me to say this:
The day before last I suddenly was unable to "see" my normal wireless networks.  I have been using b43 in Kubuntu for a couple of weeks now without incident(I am a recent migrant from PCLOS, where I used ndiswrapper for the past couple years in this laptop).  By all other accounts the wireless card seems to be fine.  lspci still gives me correct information and dmesg doesn't return anything out of the ordinary (as far as I can tell).  Ok, so far seems like a software problem but here is where is gets odd.
I have a windows and pclos (using ndiswrapper) on the same computer.  Both of them have the same basic problem.  Wireless card seems fine, but will not "see" my wireless networks.  Ok, at this point I think my wireless card has just given up the ghost.
On an identical laptop (another Gateway 7504GX, bcm4306 wireless), that already had windows and pclos on it, I installed kubuntu.  Before I installed I verified that the wireless was working fine (which it was in both windows and pclos).  After I installed kubuntu, I was unable to get wireless working (using b43), but also windows and pclos wireless stopped working as well.   So this leads me to believe that the b43 firmware is somehow screwing up the card.
Does anyone know anything about this, or how to solve it.  I am a bit of a newb with linux.. and especially with k/ubuntu.  Any help at all would be tremendously helpful.  Thanks

---

### Post by Ayuthia on 2008-09-21
> **Taollan said:**
> It appears that b43-fwcutter has broken not one, but two of my bcm 4306 wireless cards in two Gateway 7405GX laptops. 
Here is what leads me to say this:
The day before last I suddenly was unable to "see" my normal wireless networks.  I have been using b43 in Kubuntu for a couple of weeks now without incident(I am a recent migrant from PCLOS, where I used ndiswrapper for the past couple years in this laptop).  By all other accounts the wireless card seems to be fine.  lspci still gives me correct information and dmesg doesn't return anything out of the ordinary (as far as I can tell).  Ok, so far seems like a software problem but here is where is gets odd.
I have a windows and pclos (using ndiswrapper) on the same computer.  Both of them have the same basic problem.  Wireless card seems fine, but will not "see" my wireless networks.  Ok, at this point I think my wireless card has just given up the ghost.
On an identical laptop (another Gateway 7504GX, bcm4306 wireless), that already had windows and pclos on it, I installed kubuntu.  Before I installed I verified that the wireless was working fine (which it was in both windows and pclos).  After I installed kubuntu, I was unable to get wireless working (using b43), but also windows and pclos wireless stopped working as well.   So this leads me to believe that the b43 firmware is somehow screwing up the card.
Does anyone know anything about this, or how to solve it.  I am a bit of a newb with linux.. and especially with k/ubuntu.  Any help at all would be tremendously helpful.  Thanks

The b43 driver is just software that runs your wireless card.  The firmware is just needed for the driver but it does not install anything on your wireless card.  It is just used by the driver to make it work.  There has never been any posts or e-mails that have shown that the b43 driver has killed a wireless card so my thought is that something else is causing the problem with the wireless card.

If you want, you can post the results (from the Terminal/Konsole)of:
```
lshw -C network
ifconfig
iwconfig
```

---

### Post by Taollan on 2008-09-23
Sorry for the long time to repost.  I only have internet in my office.  Losing my wireless is really screwing me up.
Ok, output of lshw -C network
```
 *-network:0
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:13:f4:b3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=134.121.33.109 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:8f:27:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```
the relavent parts of ifconfig:
```

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:8f:27:1b
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-8F-27-1B-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
and the relavent parts of iwconfig:
```

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I didn't think software could break my hardware, but that seemed like the simplest explanation since separate OS has the same problem at the same time.  Then I remembered something:  I have seen on this forum and myself experienced, if a wireless is disabled in WinXP, then I reboot into PCLOS or Kubuntu, my wireless will occasionally be useless, and I will have to reboot into windows, turn back on the wireless for it to work.  Is there some settings on the card that are persevered when using different OSes?

Anyhow, any help will be greatly appreciated.  Being without wireless is killing me.

---

### Post by Ayuthia on 2008-09-23
> **Taollan said:**
> Sorry for the long time to repost.  I only have internet in my office.  Losing my wireless is really screwing me up.
Ok, output of lshw -C network
```
 *-network:0
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:13:f4:b3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=134.121.33.109 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:8f:27:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```
the relavent parts of ifconfig:
```

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:8f:27:1b
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-8F-27-1B-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
and the relavent parts of iwconfig:
```

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I didn't think software could break my hardware, but that seemed like the simplest explanation since separate OS has the same problem at the same time.  Then I remembered something:  I have seen on this forum and myself experienced, if a wireless is disabled in WinXP, then I reboot into PCLOS or Kubuntu, my wireless will occasionally be useless, and I will have to reboot into windows, turn back on the wireless for it to work.  Is there some settings on the card that are persevered when using different OSes?

Anyhow, any help will be greatly appreciated.  Being without wireless is killing me.

Are you able to see any wireless sites:
```
sudo iwlist scan
```Also, have you tried changing the channel on your router?

As for settings on the card being preserved, I have seen this happen on other cards, but I have not seen this happen on any Broadcom cards.  It is not to say that it cannot happen though.

---

### Post by Taollan on 2008-09-23
I could try that when I get home, but I doubt that is the problem.  This card all of a sudden see now wireless anywhere any time.  I have tried it at three different networks I normally connect to.  

So assuming that doesn't work...would the next step be to try a different driver?  bcm43xx or ndiswrapper?

---

### Post by Ayuthia on 2008-09-23
> **Taollan said:**
> I could try that when I get home, but I doubt that is the problem.  This card all of a sudden see now wireless anywhere any time.  I have tried it at three different networks I normally connect to.  

So assuming that doesn't work...would the next step be to try a different driver?  bcm43xx or ndiswrapper?

I think that you should try ndiswrapper.  I don't think that the bcm43xx will work any better for the 4306 rev 03 card.  If it was the rev 02, it might have been worth trying because the b43legacy users sometimes can get bcm43xx to work better.

---

### Post by Taollan on 2008-09-24
OK, I installed ndiswrapper by the instructions presented at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff).  

My lshw -C network now reads
```

  *-network:0
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wlan0
       version: 03
       serial: 00:90:4b:8f:27:1b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+ASUS,03/22/2004, 3.60.7.0 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```
so it seems like I got it installed ok.
I checked to make sure my wifi card was on.  It wasn't so I flipped it on.
Alas, still I do no see any wireless networks.  
If you or anyone has anymore thoughts at all on what I should try next, I would really like to hear them.  This is really messing me up not having wireless.

---

### Post by HangMan101 on 2008-09-24
I don't see any think about you checking your kill switch state..

"dmesg" could clear this as the broadcom driver will log it there telling you that the kill switch is on. 

and in case you don't know what the kill switch is:
it the button that is connected to a card to disable the card on hardware level. basically cuts off your antenna power.

after it is put back on (kill off) it takes time for the card to recognize networks. (mostly there is a light that indicates if the card is turned on/off by this switch )

EDIT: 
ndiswrapper is not a real solution for broadcom cards. 
they only work if you are realy lucky..
form the 10 i configured 1 worked with ndiswrapper the others had to use b43
and the 1 with ndiswrapper is really buggy loses connections after some time even if they report full network strength.

---

### Post by Taollan on 2008-09-24
Hangman, thanks for the input about the kill switch, I know that turns out to be what is keeping a wifi card from working quite often..  I have had that problem in the past. That was what I was referring to when I mentioned "I checked to make sure my wifi card was on. It wasn't so I flipped it on.", not the software enable/disable state, so the confusion was on my part.  

Ok, here is the strange thing.  I restart my computer after the ndiswrapper attempt. Since the bug with Hardy causes the ndiswrapper module not to load right, the b43 loaded.  Out of thin air the stinking thing is just working now.  It makes me curious if installing ndiswrapper changed something....
I may never know.  I am just VERY relieved to have it working again.

If anyone has any ideas what might have happened and methods to diagnose, I would still like to hear them, in case this happens again.

---

### Post by HangMan101 on 2008-09-24
well if the driver(b43) loaded it means you did not blacklist it. and in the first (not updated version of hardy) there was a problem that the driver was started at a point the kernel is loading and ignoring the blacklist (a real pain in the ***). so a up-to-date hardy would not have the problem just update and add the restricted driver b43 (will download the firmware) then restart and in most of my cases it works great.
and next time you have problems with the broadcom card this will help us:

```

dmesg | grep b43

```

---

### Post by Taollan on 2008-09-24
Thanks for the help. Everything seems to be working well.  I will remember to post the dmesg next time.  Thanks again, its a relief to have my wireless working again.

---

