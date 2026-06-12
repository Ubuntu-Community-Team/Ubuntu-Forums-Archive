---
title: "Broadcom 4324 on Dell D810 wlan0 issues"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by esquiador on 2008-09-05
I'm having trouble getting my wireless to work, and I was wondering if anyone could help me out. I feel like I'm missing something pretty simple, but I'm still pretty new at this.

I had it working for a couple of days when I upgraded to Hardy, but then it stopped all of a sudden and I haven't been able to get it back working again.

iwconfig gives me this:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And sudo ifdown wlan0 gives this:
```
ifdown: interface wlan0 not configured

```

Does anybody have any ideas how to solve this conundrum?

---

### Post by Ayuthia on 2008-09-05
> **esquiador said:**
> I'm having trouble getting my wireless to work, and I was wondering if anyone could help me out. I feel like I'm missing something pretty simple, but I'm still pretty new at this.

I had it working for a couple of days when I upgraded to Hardy, but then it stopped all of a sudden and I haven't been able to get it back working again.

iwconfig gives me this:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And sudo ifdown wlan0 gives this:
```
ifdown: interface wlan0 not configured

```

Does anybody have any ideas how to solve this conundrum?

Let's start by checking what driver your wireless is trying to use.  Can you post the results of:
```
lshw -C network
```

Since you mentioned that you upgraded to Hardy you might have a driver conflict.  Can you also post the results of:
```
lsmod|grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
cat /etc/modules |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
cat /etc/modprobe.d/blacklist|grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
```
The first command will help see what wireless modules are currently loaded, the second will see what it is trying to load maunally, and the third is checking to see what you have blacklisted.

---

### Post by esquiador on 2008-09-05
Okay, the output of lshw -C network is
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:d8:95:52
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5751-v3.29a ip=192.168.2.11 latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:06:68:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```
So I guess it's a bcm4318, not the 4324 that I thought it was before.

Here's lsmod|grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
```
b43                   144420  0 
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  1 b43

```
The next line of code didn't return anything, and the last one returned 
```
# replaced by b43 and ssb.
blacklist bcm43xx

```

---

### Post by Ayuthia on 2008-09-05
I have seen that the 4318 card has been having some problems with Hardy.  If you upgraded instead of doing a fresh install, you could try using the old bcm43xx module:
```
sudo modprobe -r b43 ssb
sudo modprobe bcm43xx
sudo ifconfig wlan0 up

```
If this connects, then we will need to blacklist the b43 module and load the bcm43xx module.

If it does not, you might need to try ndiswrapper.

---

### Post by esquiador on 2008-09-05
Thanks for all the help. I didn't upgrade, I did a fresh install about a month ago, so I don't think I'll be able to use the old module.

I guess I'll give ndiswrapper a try, unless anyone else has any ideas.

---

