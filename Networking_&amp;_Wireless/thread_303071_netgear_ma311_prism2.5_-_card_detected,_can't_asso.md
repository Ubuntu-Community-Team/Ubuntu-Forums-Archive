---
title: "netgear ma311 prism2.5 - card detected, can't associate with AP"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by peletiah on 2006-11-19
Hello!

I've freshly installed efty and have some issues running my Netgear MA311 Prism PCI-Wlancard. The card is detected and seems to be ready for work, but no accesspoint is detected(It stands right next to it and my laptop works flawlessly with it). With Gnome-network-manager the access point is viewed but i can't associate. 
One thing i've noticed is that both orinoco_cs and prism2_pci modules are loaded - i guess this isn't correct? Is this compiled in the kernel or is there some packet i could remove to remove the module? I'm coming from gentoo, so i'm not very firm with Ubuntu yet.

here's some output that might help in debugging(well, it didn't help me yet, maybe you see more):

```

peletiah@AthlonXP:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:""  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.467 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=-68 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

peletiah@AthlonXP:/etc$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:26:54:0E:19:1E  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:54ff:fe0e:191e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1135127 (1.0 MiB)  TX bytes:235959 (230.4 KiB)
          Interrupt:177 Base address:0xe000 

peletiah@AthlonXP:/etc$ ifconfig eth2
eth2      Link encap:Ethernet  HWaddr 00:09:5B:41:B4:7E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Memory:e0000000-e0000fff 

```

```

lspci -vvv
01:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
        Subsystem: Netgear MA311 802.11b wireless adapter
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 201
        Region 0: Memory at e0000000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

```

```

dmesg
[17179591.832000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179591.832000] orinoco_pci 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
<snip>
[17179591.888000] orinoco_pci: Detected device 0000:01:09.0, mem:0xe0000000-0xe0000fff, irq 201
[17179592.832000] eth2: Hardware identity 8013:0000:0001:0000
[17179592.832000] eth2: Station identity  001f:0006:0001:0003
[17179592.832000] eth2: Firmware determined as Intersil 1.3.6
[17179592.832000] eth2: Ad-hoc demo mode supported
[17179592.832000] eth2: IEEE standard IBSS ad-hoc mode supported
[17179592.832000] eth2: WEP supported, 104-bit key
[17179592.832000] eth2: MAC address 00:09:5B:41:B4:7E
[17179592.832000] eth2: Station name "Prism  I"
[17179592.832000] eth2: ready
<snip>
[17179593.256000] prism2pci_init: prism2_pci.o: 0.2.5 Loaded
<snip>
[17179593.312000] hostap_pci: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
<snip>
[17179629.176000] eth2: New link status: Disconnected (0002)
<snip>
[17179629.752000] eth2: New link status: Association Failed (0006)
[17179631.204000] eth2: New link status: Disconnected (0002)
[17179634.464000] eth2: New link status: Association Failed (0006)

```

```

lsmod
hostap_pci             59152  0 
hostap                123012  1 hostap_pci
ieee80211_crypt         7552  1 hostap
prism2_pci             74752  0
<snip>
orinoco_pci             8320  0 
orinoco                45076  1 orinoco_pci
hermes                  9472  2 orinoco_pci,orinoco
<snip>

```

```

peletiah@AthlonXP:~$ iwlist eth2 scanning
eth2      Scan completed :
          Cell 01 - Address: 00:09:5B:73:15:7A
                    ESSID:"FooAP"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Signal level:41/153  Noise level:15/153
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s

peletiah@AthlonXP:~$ 

```

```

iwconfig eth2 essid FooAP
ifconfig eth2 192.168.0.8 netmask 255.255.255.0
ifconfig eth2 up

dmesg
[17180634.652000] NET: Registered protocol family 17
[17180675.208000] ADDRCONF(NETDEV_UP): eth2: link is not ready
[17180675.576000] eth2: New link status: Association Failed (0006)
[17180898.368000] ADDRCONF(NETDEV_UP): eth2: link is not ready
[17180900.256000] eth2: New link status: Association Failed (0006)

```

---

### Post by peletiah on 2006-11-20
huh? too much debug-information in my post?

---

### Post by FrodoB on 2006-11-20
Post is great. Try blacklisting  any module that you get in lsmod that has the name orinoco in it and then reboot and try again.

---

### Post by peletiah on 2006-11-22
thx for the reply!

hmm, how can i disable loading of the orinoco-module in ubuntu? 
in gentoo this was in /etc/modules.autoload.d/kernel-2.6 or a module was loaded by a app, like alsa or pcmcia-cs. However, in my ubuntu-installation i've only found /etc/modules and there's no orinoco-module listed... :-k 

is this actually the right approach? i mean, the card is recognized, it's only that it can't associate with the ap for some strange reason...

---

### Post by FrodoB on 2006-11-22
To blacklist a module you need to add it to the /etc/modprobe.d/blacklist  file:
 [FONT=monospace]
[/FONT]$ sudo gedit /etc/modprobe.d/blacklist 

Add a record at the end of the file that contains:

blacklist orinoco_cs

and any other orinoco names that you get from lsmod.

Reboot and see if things don't improve.

---

