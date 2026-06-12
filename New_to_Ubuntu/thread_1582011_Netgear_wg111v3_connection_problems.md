---
title: "Netgear wg111v3 connection problems"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by BumberBot3K on 2010-09-25
**UPDATE 12/31**
Must be a router compatibility issue. Connected the WG111v3 to my Android-powered phone via Mobile AP and it works fine. So not exactly solved, but it's unsolvable with my current hardware so...


I just removed a PCI NIC from my dual boot (Lynx/Win7) machine because it was failing and Windows was having major issues with it (ironically, Kubuntu was handling it just fine). I replaced it with a USB device, the Netgear WG111v3. This is supposed to be a "plug and play" device with all newer releases of linux, but I'm still having issues. And because I'm too far from the router for a cable, I can't use the internet to solve my issue... it's a real chicken and egg dilemma.

Basically, the adapter is recognized by the machine and is capable of scanning for networks. However, once I choose the network and enter the password, I get stuck in and endless loop of "Configuring Interface" and re-entering the password. The password is good of course (I check it every time) and my Win7 install has zero problems accessing the exact same connection through the same exact device. Here are some readouts from lsusb and iwconfig. Nothing looks amiss to me, but of course, I don't really know what I'm looking for...

lsusb:

```
Bus 001 Device 003: ID 0846:4260 NetGear, Inc. WG111(v3) 54 Mbps Wireless [RealTek RTL8187B]
```

iwconfig:
```


wlan1     IEEE 802.11bg  ESSID:"Ann's network"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


```


TIA
bb3k

---

### Post by jtarin on 2010-09-25
[Are you running 64-bit?]("http://linux.goeszen.com/netgear-wg111-v3-on-ubuntulinux-amd64.html")

---

### Post by BumberBot3K on 2010-09-25
> **jtarin said:**
> [Are you running 64-bit?]("http://linux.goeszen.com/netgear-wg111-v3-on-ubuntulinux-amd64.html")

Bummer.

---

### Post by BumberBot3K on 2010-09-26
So here's my new problem. I re-installed the PCI NIC so only Kubuntu can use it. This is easy on the Win7 side: I just disable the device in the device manager. However, when I boot up in to Kubuntu, it names both devices identically "Wireless 802.11bg" and so I have no way of knowing which one I'm trying to connect with. Trial and error found me the right one, however, the network manager fails to connect when I specify a particular adapter for a connection. So even if I guessed which "Wireless 802.11bg" was the PCI adapter, I can't force Kubuntu to use that to connect.

I've seen this question asked before but haven't yet seen an up-to-date answer: is there something similar to device manager that allows me to manually disable certain hardware, so the system can't see or use it? Doesn't have to be GUI, but would like the changes to be permanent.

---

### Post by BumberBot3K on 2010-09-26
> **BumberBot3K said:**
> So here's my new problem. I re-installed the PCI NIC so only Kubuntu can use it. This is easy on the Win7 side: I just disable the device in the device manager. However, when I boot up in to Kubuntu, it names both devices identically "Wireless 802.11bg" and so I have no way of knowing which one I'm trying to connect with. Trial and error found me the right one, however, the network manager fails to connect when I specify a particular adapter for a connection. So even if I guessed which "Wireless 802.11bg" was the PCI adapter, I can't force Kubuntu to use that to connect.

I've seen this question asked before but haven't yet seen an up-to-date answer: is there something similar to device manager that allows me to manually disable certain hardware, so the system can't see or use it? Doesn't have to be GUI, but would like the changes to be permanent.

Ok, well I've solved my problem using [this thread]("http://ubuntuforums.org/showthread.php?t=1286130"). I tried using the first method (adding and ifconfig "down" command to a startup script) but had no luck. I ended up just adding the module (rtl8187) to the modprobe blacklist as described in the second the last post in that thread. Seems to be working!

---

