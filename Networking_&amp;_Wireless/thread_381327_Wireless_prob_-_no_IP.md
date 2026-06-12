---
title: "Wireless prob - no IP"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by timebomb on 2007-03-10
Hello all-

I posted this earlier in the beginner forum (as I am one) but thought it would help to seek advice here as well.

[http://ubuntuforums.org/showthread.php?p=2277647#post2277647](http://ubuntuforums.org/showthread.php?p=2277647#post2277647)

Thanks in advance for the assists and inspiration.

---

### Post by handaxe on 2007-03-10
(WOOPS! Embarrassing, Sorry, I never saw the stuff in the thread above your last post you linked in:-o)

So, you can see the networks  but not connect to them.

Encryption comes to mind - what encryption  are they using?

First off, please type at command prompt and post the respective outputs

```
sudo lshw -C network
sudo iwconfig

```HA

---

### Post by chili555 on 2007-03-10
WEP is tricky to get just right. Here is a post that may help: [http://www.ubuntuforums.org/showthread.php?t=172810&page=2](http://www.ubuntuforums.org/showthread.php?t=172810&page=2)

---

### Post by handaxe on 2007-03-10
One thing I do note is that your output of iwconfig has nothing about encryption between the "retry limit.." and "Power management." lines. Strange...or did you edit those out?

HA

---

### Post by chili555 on 2007-03-10
The WEP key will show up with sudo iwconfig, but not iwconfig. Might be very helpful to double-check it.

---

### Post by handaxe on 2007-03-11
Thanks for the pointer chili555.  Never occurred to me he might not have sudo'ed the command (doh!)

HA

---

### Post by timebomb on 2007-03-11
Output of sudo lshw -C network:
>   *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:c8:a2:b6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.59.1 duplex=full firmware=5705-v3.16 ip=192.168.2.6 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:faff0000-faffffff irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:74:94:96
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.1.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:fafef000-fafeffff irq:5

Output of sudo iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"WIRELESS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:09:5B:27:28:8C   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:WIRELESSKEY   Security mode:restricted
          Power Management:off
          Link Quality=60/100  Signal level=-29 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:17213  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I've also played with the router a bit, changing the setting from AUTO to SHARED key, as the other thread on WEP suggests.  No luck.

---

### Post by chili555 on 2007-03-11
May we also see sudo iwlist eth1 scan?

---

### Post by handaxe on 2007-03-11
```
 eth1      IEEE 802.11b  ESSID:"WIRELESS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:09:5B:27:28:8C   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:WIRELESSKEY   Security mode:restricted
          Power Management:off
          Link Quality=60/100  Signal level=-29 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx [COLOR=Red]**invalid crypt:17213**[/COLOR]  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```chili555 is probably a better bet than me here, but I think the highlighted above shows a problem

---

### Post by chili555 on 2007-03-11
Yessir! It shows many attempts have been made and none have the correct key. 

Is your wireless-key actually WIRELESSKEY? Did you check and double-check in the router to see what the key shows in there? It should look something like: 93c8530b2df51711bad5596f91

In my experience, WEP is exacting. 128-bit WEP wants a 26-character alphanumeric key, not 25 or 12 or 6. If you transpose a letter or mistype a number, WEP's job is to keep you out, not say, "Oh, well, I knew what you meant, come on in."

I talked to a guy that knows a guy that heard a guy actually got WEP working with a passphrase, but I've never seen it myself.

---

### Post by timebomb on 2007-03-11
Okay - I managed to get this working.  Thanks to all for giving me the proper push.  

Here's what I did:  My router (an old NetGear) has four key slots with generated keys, and for some odd reason I had selected the second key.  I removed them all, except the first, and changed the setting to the first key.  Once I saved the settings on the router and restarted networking in Ubuntu - voila!  

This seems incredibly touchy, considering every other wireless device in my house handled the WEP settings with no problem - so much so that I never noticed it until now.  I can see why the wireless features in Ubuntu and, I presume, linux in general, are one part that could use a bit more robustness.

Linux is great though a clearly different environment in the eyes of this longtime DOS/Windows user.  I'm on my way to converting.  All I need to do is figure out a way to get AbiWord or OpenOffice to have a "Normal View" that approximates Word and I'll be happy.

---

### Post by handaxe on 2007-03-11
(Late edit) ah well, nevermind....congrats!!

@chili555,

one other thing, his output of ifconfig shows inet6. My output shows an xxx.xxx.x.x style address (ipv4 I think it is termed) but I have disabled inet6 on my lappie. Is that an issue here?

```
  eth1      Link encap:Ethernet  HWaddr 00:0E:35:74:94:96  
          inet6 addr: fe80::20e:35ff:fe74:9496/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:516 errors:297 dropped:297 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:6144 (6.0 KiB)
          Interrupt:5 Base address:0xc000 Memory:fafef000-fafeffff 
```

---

### Post by timebomb on 2007-03-11
> **chili555 said:**
> 
Is your wireless-key actually WIRELESSKEY? Did you check and double-check in the router to see what the key shows in there? It should look something like: 93c8530b2df51711bad5596f91


Yes - I was obscuring my key on purpose.  I was substituting both my router name and key.

---

