---
title: "WiFi Detecting but not Connecting"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Gwasanaethau on 2009-01-05
I have an Atheros AR5009 WiFi chip built-in to a Compaq Presario CQ60 laptop. It wasn't working out-of-the-box, so  naturally searched the fora for answers. I've downloaded the drivers from [here]("http://wireless.kernel.org/en/users/Drivers/ath9k"), and compiled them. The WiFi chip detects all the surrounding networks correctly (and their ecryptions schemes) but it doesn't want to actually connect to them (whether I turn the encryption on or off).

I've also spent the past few days (painfully) trying to compile the 2.6.28 kernel as I know that the ath9k drivers can be built-in to it. Once I finally got the new kernel to stop panicking on boot, it gave me the same result as the compiling the drivers alone. Any ideas what I could do to try and force a connection?

I also tried turning DHCP on the router off and assigning an IP address manually - no luck.

The output of ifconfig is:
```
eth0…
lo…
wlan0      Link encap:Ethernet HWaddr <<HIDDEN>>
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)

wmaster0   Link encap:UNSPEC HWaddr <<HIDDEN>>
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)
```

The output of iwconfig is:
```
lo         no wireless extensions.

eth0       no wireless extensions.

wmaster0   no wireless extensions.

wlan0      IEEE 802.11abgn  ESSID:""
           Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
           Tx-Power=23 dBm
           Retry min limit:7   RTS thr:off  Fragment thr=2352 B
           Power Management:off
           Link Quality:0  Signal level:0  Noise level:0
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0  Missed beacon:0
```

---

### Post by Michael.Godawski on 2009-01-05
hi, 
can you post the output of these commands too
```

sudo lshw -C network
cat /etc/network/interfaces
```

---

### Post by Gwasanaethau on 2009-01-11
Hi Michael, thanks for replying - sorry it's taken me so long to post back!

Here are the results of the commands you asked me to input:

sudo lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: <<HIDDEN>>
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.31 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: <<HIDDEN>>
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn
```

cat /etc/network/interfaces:
```
auto lo
iface lo inet loopback
```

---

### Post by tasuki on 2009-02-23
I'm having **exactly** the same problem on my ThinkPad with Atheros AR5008 (under out-of-the-box ath9k drivers).

tcpdump doesn't catch anything, I can't interact with the network at all - but with iwlist I can see the available networks, strength of signal, etc.

---

### Post by stchman on 2009-02-23
Post an lspci output here in this thread.

---

### Post by tasuki on 2009-02-24
Thanks for a quick reply, here's all the relevant info I could think about:

```
root@gandalf:~# lspci -vs 03:00
03:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
	Subsystem: Atheros Communications Inc. Device 0033
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at df3f0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

root@gandalf:~# lshw -class network
  [snip ethernet]
  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1c:26:15:85:7e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn
  [snip other uninteresting stuff]

root@gandalf:~# iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"D-Link Wireless"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=23 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@gandalf:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:E4:95:4E
                    ESSID:"D-Link Wireless"
                    Mode:Master
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=12/100  Signal level:-87 dBm  Noise level=-95 dBm
                    Encryption key:off
                    IE: Unknown: 2D1A1E181AFFFF000000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000001087a4c8186
                    Extra: Last beacon: 992ms ago

root@gandalf:~# tcpdump -nti wlan0
tcpdump: WARNING: wlan0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 96 bytes
^C
0 packets captured
0 packets received by filter
0 packets dropped by kernel
root@gandalf:~# 
```

[EDIT:] I forgot to mention, I was on 2.6.27-11, upgraded to 2.6.27-12 from intrepid-proposed and situation is still the same.

---

### Post by tasuki on 2009-02-24
I tried madwifi driver (driver=ath_pci) with the very same result - can see networks but can't connect or catch a single packet. :-k

Also, bump to get more action. O:)

---

### Post by binbash on 2009-02-24
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

### Post by tasuki on 2009-03-03
> **binbash said:**
> [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

I tried that, but I seem to have some problems - specifically, when I disable ath9k module (which came as default), the ath5k module gets loaded but not associated with the card.

lshw output:
```
  *-network UNCLAIMED
       description: Network controller
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
```

also,

```
root@gandalf:~# lsmod | grep ath5k
ath5k                 116228  0 
mac80211              213552  1 ath5k
cfg80211               43416  2 ath5k,mac80211
led_class              12164  2 ath5k,thinkpad_acpi
```

How do I tell the system to use ath5k driver for the card?

---

### Post by ussndmac on 2009-03-03
I have had this same issue with the intel chipset in my Dell.

Short getting the witch doctor from down the street to come over and drive out the demons I have tried a lot of the threads on these forums to no avail.

One person said his started working after he got a new router, his old WAP (and my current WAP) were 802.11b only.

---

### Post by Patricrawley on 2009-03-03
I had a very similar issue with a D-Link wifi card I installed a few months ago. It worked right out of the box but it took like 5 nminutes to connect and then had a really horrible connection. I switched to ndiswrapper to see if I had any better results and so far the results I have seen are far better. So that's always an option. It's available in the repositories with a GUI as well for installing the correct drivers. It just requires a little extra work.

---

