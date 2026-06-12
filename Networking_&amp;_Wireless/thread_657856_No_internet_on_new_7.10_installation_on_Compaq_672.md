---
title: "No internet on new 7.10 installation on Compaq 6720s"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by monkeytalk on 2008-01-04
I have a new Compaq 6720s laptop ([purchased from Ebuyer]("http://www.ebuyer.com/product/133523")) but I'm struggling to get wireless working.

I installed Ubuntu 7.10 from a live CD. It seemed to go well but it does not automatically detect wireless networks. Neither does it work when I try to "Connect to other wireless networks".

I have tried adding [FONT="Courier New"]pci=noacpi[/FONT] to [FONT="Courier New"]/boot/grub/menu.lst[/FONT] ([as suggested here]("http://marcin.af.gliwice.pl/if-then-else-20071022085850")) but this has no effect.

I don't know if the drivers have been installed properly.

Can anyone help me please?

Many thanks in advance.

---

### Post by jan quark on 2008-01-04
1: Go to the restricted dirvers manager. do you see your network card mentioned here?
2. pls post the results of the following commands, they gather information about your network status
```
lspci -v | less
```
```
iwconfig
```
```
ifconfig
```
```
sudo iwlist scan
```

---

### Post by NoHoSe on 2008-01-25
same problem here.

lspci -v

10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1375
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at e4000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

iwconfig

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig

eth1      Link encap:Ethernet  HWaddr 00:00:00:1A:73:B6  
          UP DIFUSIÓN MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:4914 (4.7 KB)
          Interrupt:10 

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

---

