---
title: "Samsung 305U1A (with Broadcom 4313) wifi problems!"
date: 2013-12-25
forum: Networking &amp; Wireless
---

### Post by solveig.hansen on 2013-12-25
Hi!

I have a two year old laptop I rarely use because of network problems. Yesterday I decided to try and fix them, after having installed Lubuntu on it and seeing how smuud it runs. I've looked around at this forum quite a bit, and tried several of the suggestions listed for similar problems, but I am a bit of a linux noob and haven't gotten anything to work yet. 

Here's some info:

lscpi gives me this info:
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)

```

ifconfig & iwconfig gave me these two:

```
wlan0     Link encap:Ethernet  HWaddr 90:a4:de:b3:ca:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
lsmod gives me this (among others, I think these has to do with the broadcom driver, but not totally sure, to be honest.)

```
brcmsmac              562767  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
bcma                   46670  2 brcmsmac
mac80211              596969  1 brcmsmac

```

dmesg:

```
[ 3712.010487] wlan0: authenticate with 00:1d:68:75:5c:ff
[ 3712.509542] wlan0: direct probe to 00:1d:68:75:5c:ff (try 1/3)
[ 3714.125676] wlan0: direct probe to 00:1d:68:75:5c:ff (try 2/3)
[ 3714.329564] wlan0: direct probe to 00:1d:68:75:5c:ff (try 3/3)
[ 3714.537570] wlan0: authentication with 00:1d:68:75:5c:ff timed out

```

Network configuration:
```

*-network               
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:16 memory:fea00000-fea03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: e8:11:32:9f:98:6b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=10.0.0.37 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 90:a4:de:b3:ca:7d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.11.0-14-generic firmware=610.812 link=no multicast=yes wireless=IEEE 802.11bgn

```

iwlist scan:
```
wlan0     Scan completed :          Cell 01 - Address: 08:60:6E:BB:6D:C8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Skjaevik"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000504c0b12183
                    Extra: Last beacon: 120ms ago
                    IE: Unknown: 0008536B6A616576696B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFD191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD310050F204104A0001101044000102104700108EF561739B81195A7007DAA0149354AF103C0001031049000600372A000120
                    IE: Unknown: DD090010180200F03C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00



```

I'm on Ubuntu 13.10   (Lubuntu)
kernel version: 3.11.0-14-generic x86_64

I have read about what type of driver I should have here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) but it lists two different that are compatible with my card, and I've tried them both. In the beginning it wouldn't connect at all, for a brief moment during my trial and error I got five seconds of net, whereas now it won't connect anymore.

Any help would be appreciated! =)

---

### Post by Bucky Ball on 2013-12-25
Welcome.

Are you online with a cable? If so, do an update and check additional drivers. Is there any reference there to b43? I'm imagining that is what you're after. If there is no trace of it, you can install b43-fwcutter and firmware-b43-installer from Synaptics or SCentre and give that a try. You may need to blacklist the driver you already have installed as don't think that is the right one.

Also, do you have two wireless cards in, internal and a USB plugged in also, perhaps? Just wondering why your output is referring to two cards and two totally different drivers. Which one do want to get going??? You have:

```
*-network               
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: **driver=bcma-pci-bridge** latency=0
       resources: irq:16 memory:fea00000-fea03fff
```

... and:
 
 ```
 *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 90:a4:de:b3:ca:7d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes **driver=brcmsmac** driverversion=3.11.0-14-generic firmware=610.812 link=no multicast=yes wireless=IEEE 802.11bgn
```

Odd. :-k

---

### Post by solveig.hansen on 2013-12-25
Yeah, I was also wondering why the output mentions two cards.. I have one card inside my computer, and nothing else plugged in. The second one is my wired net? Hmm that is the one using the brcmsmac driver. 

I am not sure what you mean by "[COLOR=#000000]check additional drivers", sorry. Under *Software & updates"  -> Additional Drivers *it lists the Broadcom 802.11 Linux Sta wireless driver source from bcmwl-kernel-source.

The WifiDocs I linked to in the original post says doesn't list my card as compatible with the b43 though



[/COLOR]

---

### Post by Bucky Ball on 2013-12-25
Is the STA driver enabled? If not, give it a try. Some Broadcom work best with that rather than b43, and others rubbish with it, or not at all. Not sure about yours.

If no different, disable it again so we know that is not in the way.

PS: This is the wired connection:

```
*-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: e8:11:32:9f:98:6b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=10.0.0.37 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
```

This is a Realtek device. I am truly confused by your setup at this point. No doubt we will unravel the mystery ...

---

### Post by solveig.hansen on 2013-12-25
> **Bucky Ball said:**
> Is the STA driver enabled? If not, give it a try. Some Broadcom work best with that rather than b43, and others rubbish with it, or not at all. Not sure about yours.

If no different, disable it again so we know that is not in the way.

Yeah, it says I am using that driver, but I'm not sure if I might have ****ed up something in the blacklist.conf file. I've been trying out tips from different forums, so now I am unsure what should be blacklisted and not... 

Here is the (relevant parts of the) file atm: 

blacklist b43
blacklist bcm43xx
blacklist bcma
#blacklist brcmsmac
blacklist ssb

This might be a silly question, but do I need to reboot everytime I make changes to that file or try a different driver? Haven't been doing that 100% of the times.

Anyway, the Sta is being used, it says, but no wifi

---

### Post by Bucky Ball on 2013-12-25
Okay, open the blacklist file and make it look like this (using sudo before the command, e.g. 'sudo nano <path to file>:

```
# blacklist b43
# blacklist bcm43xx
blacklist bcma
blacklist brcmsmac
blacklist ssb
```

Disable the STA driver and install:

b43-fwcutter
firmware-b43-installer

Reboot. Anything? You might need to do an update via a cable and perhaps check additional drivers again.

---

### Post by solveig.hansen on 2013-12-25
Ok, thanks. Trying it out now.

---

### Post by solveig.hansen on 2013-12-25
> **Bucky Ball said:**
> Okay, open the blacklist file and make it look like this (using sudo before the command, e.g. 'sudo nano <path to file>:

```
# blacklist b43
# blacklist bcm43xx
blacklist bcma
blacklist brcmsmac
blacklist ssb
```

Disable the STA driver and install:

b43-fwcutter
firmware-b43-installer

Reboot. Anything? You might need to do an update via a cable and perhaps check additional drivers again.


Nothing changed. I did an update as well, and the Additional Drivers tab only shows the Broadcom Sta as before (only now I've disabled it).

---

