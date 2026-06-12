---
title: "Yet Another ndiswrapper Thread"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by dintiradan on 2008-01-04
I've been following [these](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) docs to get my wireless to work. As far as I can tell, I've done everything right. But I'm unable to connect to my router, and thus unable to access the internet.

I'm using Ubuntu 7.10 (Gutsy) and a Linksys/Broadcom PCI Adapter (model number WMP54GS). I'm using the ndiswrapper module from my install CD - I'd have to check which version, but it should be recent. The driver came from the CD that came with the adapter - its the same driver I'm using right now with Vista. I'm pretty sure it should work with ndiswrapper as well - the driver is meant for Windows XP, and the PCI IDs from 'lspci -n' and 'ndiswrapper -l' match. The router I'm trying to connect to uses DHCP, WEP-Open authentication, and a 10-digit network key (as per specific instructions).

Anyway, the following is the output of a typical session. I've already installed ndiswrapper and set the .inf files before doing the following.

```
root@motrax:~# cat /etc/modprobe.d/blacklist-bcm43xx
blacklist bcm43xx
```

As you can see, I've blacklisted the default driver. I'd have to double-check, but I'm pretty sure 'lsmod | grep bcm43xx' doesn't return anything.

```
root@motrax:~# modprobe ndiswrapper

root@motrax:~# lsmod | grep ndiswrapper
ndiswrapper           185240  0 
usbcore               138632  7 ndiswrapper,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd

root@motrax:~# ndiswrapper -l
wmp54gs : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
```

The "(alternate driver: bcm43xx)" worries me; I thought that'd go away after I blacklisted it. In any case, I think the card works, because iwlist does.

```
root@motrax:~# lshw -C network
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth1
       version: 02
       serial: 00:18:f8:2e:9a:aa
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wmp54gs driverversion=1.45+Linksys,12/22/2004, 3.100.4 latency=32 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
<snip... Ethernet interface>
```

```
root@motrax:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:xxxx-xxxx-xx   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
root@motrax:~# iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:19:E4:06:86:C9
                    ESSID:"2WIRE629"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
<snip... neighbours>
```

Good so far, right? I'm picking up the router upstairs, so my adapter obviously work, despite the fact that the light on the back doesn't turn on as it does when I'm running Windows. When I try connecting via the GUI, I see "2WIRE629" off the drop-down menu. I select it, type in my network key. A progress bar appears, then disappears, without stating success or failure. I'm unable to connect to anything. A similar thing happens from the command line:

```
root@motrax:~# iwconfig eth1 essid "2WIRE629" ap 00:19:E4:06:86:C9 key xxxx-xxxx-xx mode Managed commit
```

No output, and when I run iwconfig again, the output is identical. Unless I'm mistaken, I can't connect to the router, otherwise the ESSID value from iwconfig would change.

A few notes:

- First and foremost, while I am familiar with using Linux at my university, this is my first time setting up my own system, and I've never done anything touching wireless before. If I haven't mentioned it above, assume I didn't do it and don't know about it.

- A few sites I've looked at mentioned the need to edit "/etc/network/interfaces". They never really explained themselves, and none of them were talking about Ubuntu. I didn't touch it.

- I haven't tried adding "pci=noacpi" to grub yet; I'll do that tomorrow morning.

- I've tried setting the network key with and without the dashes.

It's pretty late (well, early), so I may be forgetting something. Anyway, hope this is lucid enough, and thanks in advance for any help.

---

### Post by bvmou on 2008-01-04
If you run ```
dmesg | grep ndis
``` (ie pipe output of kernel buffer into grep and show lines with string 'ndis'), do you get a message about "bad magic" or any other information?

I mention this because in my ndiswrapper case the default driver provided by the manufacturer was 64 bit and ndiswrapper wanted a 32 bit driver.  There is a script here for your card [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102") that I used with a different bcm card a while back, described [here.]("http://ubuntuforums.org/showthread.php?t=322761")  It may be worth trying different windows firmware, even if you have what seems like the correct one from the Windows OEM.  It looks like there are links to some options in that first post, I ended up finding the one that worked (not from the laptop manufacturer) by tracking it down on the ndiswrapper site.

Good luck, and hold off on the /etc/network/interfaces and pci stuff if you can avoid it; the first I think in the context you are mentioning would be if you needed to set specific WPA parameters in the pre-network-manager days.  You will get it to work.

---

### Post by dintiradan on 2008-01-04
> (ie pipe output of kernel buffer into grep and show lines with string 'ndis'), do you get a message about "bad magic" or any other information?I didn't save the output, but there was nothing like that.

Anyway, I just did a fresh install, ran the script described [here](http://ubuntuforums.org/showthread.php?t=197102), and it works. Personally, I'd prefer knowing how to set things up myself, but I suppose I can just read the script and figure out where I went wrong.

I think the problem was that I was using the wrong Windows drivers, like you said. Right now, I have:```
root@motrax:~# ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
```Different than before. Also, when I use the wireless gui, it's also different.

In any case, thanks for the help.

---

### Post by Al42 on 2008-01-04
> **dintiradan said:**
> I think the problem was that I was using the wrong Windows drivers, like you said. Right now, I have:[code]root@motrax:~# ndiswrapper -l
bcmwl5 : driver installed
bcmw15 is the correct driver for the card, so you your previous problem **was** having the wrong driver, as you surmised.  (We set up the same card about a week ago at my sister-in-law's house, and I remember that we used the bcmw15 driver, although I couldn't get any diagnostics from the computer right now - it's in transit to Fort Bragg at the moment.)

---

