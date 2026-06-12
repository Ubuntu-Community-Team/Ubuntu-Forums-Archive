---
title: "Wired Network Not Working"
date: 2014-06-04
forum: Networking &amp; Wireless
---

### Post by corey14 on 2014-06-04
Hi ive recently installed ubuntu 14.04 desktop on my asus computer. I can access wifi no worries but I can not connect using a lan cable, the option for ethernet network is greyed out and cant click it (not sure if this is standard or something to do with my problem).

I read alot of different posts with others facing similar issues after trying alot of different things ive had no luck. Some people say its the settings in ubuntu but I have a feeling its to do with the drivers. I have no idea where to start looking for these, I tried to find a .tar but could only find zip files.

Heres the output of some commands ive seen asked for in other posts:
```

===================================================
sudo ifconfig -a

eth0      Link encap:Ethernet  HWaddr bc:ae:c5:5f:2f:d4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:837 errors:0 dropped:0 overruns:0 frame:0
          TX packets:837 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83495 (83.4 KB)  TX bytes:83495 (83.4 KB)

wlan0     Link encap:Ethernet  HWaddr 48:5d:60:e2:36:e5  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5d:60ff:fee2:36e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4544 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5843728 (5.8 MB)  TX bytes:675520 (675.5 KB)

=========================================================
lspci

01:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
02:00.0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)

========================================================
ifup eth0

Ignoring unknown interface eth0=eth0.

========================================================
cat /etc/network/interfaces

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0

========================================================
cat /etc/NetworkManager/nm-system-settings.conf

No such file or directory. (Network manager is installed, not sure why its not finding file assuming it may have been removed from ubuntu 14.04?)

========================================================
dmesg | grep -e eth0 -e bcm

[    1.520887] jme 0000:02:00.0 eth0: JMC250 Gigabit Ethernet chiprev:23 pcirev:3 macaddr:bc:ae:c5:5f:2f:d4
[   12.104351] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.107826] jme 0000:02:00.0 eth0: Link is down
[   20.132631] jme 0000:02:00.0 eth0: Link is down
[   20.132770] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.134207] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

========================================================
ifconfig -a

eth0      Link encap:Ethernet  HWaddr bc:ae:c5:5f:2f:d4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:120060 (120.0 KB)  TX bytes:120060 (120.0 KB)

wlan0     Link encap:Ethernet  HWaddr 48:5d:60:e2:36:e5  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5d:60ff:fee2:36e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8294776 (8.2 MB)  TX bytes:1379799 (1.3 MB)
========================================================
```

Thanks

---

### Post by TheFu on 2014-06-04
Have you tried disabling the wifi connection when using the wired ethernet one?
What is the output from **route**?
Are the lights blinking on the switch and on the back of the PC (where the CAT5+ cable connects)?

BTW - it does appear that the system recognizes the ethernet card/chips just fine. A driver is loading - that is good.

If the lights aren't blinking - try making the eth0 part/stanza of the /etc/networking/interfaces file look like:
```
auto eth0
iface eth0 inet dhcp

```

then running  **sudo ifup eth0**

---

### Post by netgooroo on 2014-06-04
Hey corey14,
I recently experienced something very similar to this in my 12.04 install and went through everything **including** checking to see if my router was still working or not. Also, same issue with the wifi working but not the wired network. 

In the end, all that I had to do was go into the Network setting in Ubuntu :System tools/system setting/network: and manually turn my wired network back on.  For some reason it turned itself off. 

Sorry if you have already tried this and good luck.

---

### Post by corey14 on 2014-06-04
Hi netgooroo I had a look it seems wired is turned on but its saying no cable connected, I was also in airplane mode for some reason which i turned off but its still not working, thanks for your suggestions though :) im glad I saw that no cable connected might help me narrow down the solution.

Hi Thefu thanks for your help, I tried turning off the wifi but nothing happens, ethernet options are just unclickable, i tried rebooting aswell while wifi was turned off but that didnt help.
```

===========================================================
route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         MyGateway.Home  0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     *               255.255.255.0   U     9      0        0 wlan0

===========================================================

I made changes to the file not sure if I did it right still pretty new to ubuntu, i ran gksu gedit /etc/network/interfaces
and now file looks like

===========================================================
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

=================================================================
sudo ifup eth0

Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/bc:ae:c5:5f:2f:d4
Sending on   LPF/eth0/bc:ae:c5:5f:2f:d4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 (xid=0x5006c35b)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1 (xid=0x5006c35b)
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

===============================================================
```

Turned of wifi still couldnt get anything to work. Yeh I cant see any lights on the back of my computer which I thought was a bit off, ive plugged it into a laptop just to be sure its working. 
Im gonna try reboot now and hopefully it might work with the new settings (just for the record actually have no idea if rebooting helps at all)

---

### Post by varunendra on 2014-06-05
Hello corey14, Welcome to the forums!

Instead of manually formatting the outputs, use 'Code' tags. It preserves the original formatting of the outputs and makes the post cleaner and more readable.

If you intend to use Network Manager (the GUI program) to manage your Ethernet interface, then the /etc/network/interfaces file should not contain that interface entry. It means your /etc/network/interfaces file should look like this -
```
auto lo
iface lo inet loopback
```
..no additional entries! Delete the additional entries, and see if the Ethernet entry becomes clickable in the Network Manager's menu. NM is designed to 'Ignore' any interface that is being controlled by the 'interfaces' file, so that both of them don't end up managing the same interface causing possible conflicts.

If the problem remains the same, please install 'ethtool' -
```
sudo apt-get install ethtool
```
Then post back the outputs of -
```
sudo lshw -C network
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
[s]cat /var/lib/NetworkManager/NetworkManager.state.[/s]
cat /var/lib/NetworkManager/NetworkManager.state
sudo ethtool eth0
```

And do not forget to use 'Code' tags this time. :) Please follow the 'Use Code Tags' link in my signature below to see a quick guide with screenshots.

---

### Post by corey14 on 2014-06-05
Hi varunendra thanks for your help, sorry it takes me a bit to reply at work. I made those changes but couldnt access ethernet still, im using the button at the top right of the screen not sure if thats network manager. I noticed that error cat /var/lib/NetworkManager/NetworkManager.state. :no such file or directory, just checked and have the latest version of network manager and ethtool installed. Ill see if I can figure out the network manager, here are those outputs, hope this looks better :) Cheers.
[B]
sudo lshw -C network[/B]
```
sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: bc:ae:c5:5f:2f:d4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
        capabilities: pm pciexpress msix msi bus_master cap_list ethernet  physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on  broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0  link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 memory:fbffc000-fbffffff ioport:ec00(size=128) ioport:e800(size=256)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 48:5d:60:e2:36:e5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=ath9k  driverversion=3.13.0-24-generic firmware=N/A ip=192.168.0.5 latency=0  link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbef0000-fbefffff
```

**lsmod**
```
lsmod
Module                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
snd_hda_codec_realtek    61438  1 
coretemp               13435  0 
snd_hda_intel          52355  3 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
uvcvideo               80885  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
psmouse               102222  0 
bnep                   19624  2 
videobuf2_vmalloc      13216  1 uvcvideo
serio_raw              13462  0 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
joydev                 17381  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
arc4                   12608  2 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
ath9k_hw              453856  2 ath9k_common,ath9k
lpc_ich                21080  0 
snd_timer              29482  2 snd_pcm,snd_seq
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              626489  1 ath9k
i915                  783485  3 
snd                    69238  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
video                  19476  2 i915,asus_wmi
drm_kms_helper         52758  1 i915
cfg80211              484040  3 ath,ath9k,mac80211
soundcore              12680  1 snd
drm                   302817  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
asus_atk0110           18657  0 
wmi                    19177  1 asus_wmi
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
usb_storage            62209  0 
ahci                   25819  2 
libahci                32168  1 ahci
jme                    44269  0 
mii                    13934  1 jme

```
[B]
ifconfig -a[/B]
```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:5f:2f:d4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

eth0:avahi Link encap:Ethernet  HWaddr bc:ae:c5:5f:2f:d4  
          inet addr:169.254.9.54  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123315 (123.3 KB)  TX bytes:123315 (123.3 KB)

wlan0     Link encap:Ethernet  HWaddr 48:5d:60:e2:36:e5  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5d:60ff:fee2:36e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2039 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2312050 (2.3 MB)  TX bytes:287243 (287.2 KB)

```

**cat /etc/network/interfaces**
```
cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

**cat /etc/NetworkManager/NetworkManager.conf**
```

cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=BC:AE:C5:5F:2F:D4,

[ifupdown]
managed=false

```

**cat /var/lib/NetworkManager/NetworkManager.state.**
```
cat /var/lib/NetworkManager/NetworkManager.state.
cat: /var/lib/NetworkManager/NetworkManager.state.: No such file or directory

```

**sudo ethtool eth0**
```
sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pg
    Wake-on: g
    Current message level: 0x000020c6 (8390)
                   probe link rx_err tx_err hw
    Link detected: no

```

---

### Post by varunendra on 2014-06-05
> **corey14 said:**
> I noticed that error cat /var/lib/NetworkManager/NetworkManager**.state[COLOR="#FF0000"].[/COLOR]** :no such file or directory

Sorry, that was a typo on my part, there is no dot (.) after 'state'. Please run the corrected command, and post back its output -
```
cat /var/lib/NetworkManager/NetworkManager.state
```

And for now, please try -
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

Then post back the output of 'sudo ethtool eth0' again, along with the output of command corrected above.

---

### Post by corey14 on 2014-06-05
No worries, thanks for such fast responses I feel bad for not being able to do the same.[B]

cat /var/lib/NetworkManager/NetworkManager.state[/B]
```

cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```
[B]
sudo ethtool eth0[/B]
```

sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  Not reported
    Advertised pause frame use: No
    Advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: off
    Supports Wake-on: pg
    Wake-on: g
    Current message level: 0x000020c6 (8390)
                   probe link rx_err tx_err hw
    Link detected: yes

```

---

### Post by varunendra on 2014-06-05
> **corey14 said:**
> 
[/code]
[B]
sudo ethtool eth0[/B]
```
....
....
    **Link detected: [COLOR="#0000CD"]yes[/COLOR]**

```
..So basically it is saying that it has detected a physical connection. If the logical part is also okay (IP configuration, manually or via DHCP), you should have a connection now. Do you?

---

### Post by corey14 on 2014-06-05
I checked but couldnt turn off the wifi as the option was greyed out and unclickable along with the vpn connections menu. I did a reboot and after that all the menu options were back. but when turning wifi off I still couldnt access the ethernet option still greyed out. I then ran that code again and it didnt detect a link. So confused as to what changed hoping you may be able to shed some light, I just checked the ethernet cable again on my laptop and it worked fine. I really appreciate your help so much. :) heres the output of running that code again.

```

sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pg
    Wake-on: g
    Current message level: 0x000020c6 (8390)
                   probe link rx_err tx_err hw
    Link detected: no

```

---

### Post by TheFu on 2014-06-05
The **ethtool** commands are forcing (locking) your 1000base-t NIC to be a 100base-t NIC.  This slows down everything by a factor of 10x on your network - if that is acceptable to you, great.  It may even be best, if the switch/router aren't GigE too then this is 100% fine. All the options for ethtool are explained in the **man page**.   **man ethtool** BTW, manpages exist for almost every command on Linux/UNIX systems.  Nothing is hidden or secret here.

---

### Post by corey14 on 2014-06-05
Thefu thanks ill have a read of those now. I don't understand why it would be beneficial for things to run slower is this to save bandwidth? Im totally guessing. Hopefully I should understand after reading all those things.

Ran this code again thinking maybe it got cancelled out when I rebooted
sudo ethtool -s eth0 speed 100 duplex full autoneg offAfter running it computer connected to my ethernet, I was pretty happy until I tested it and when I try access webpages on the internet its just continuously loading. My wifi is doing the same thing now. Had to swap computers, Hoping after reading up on the code ill understand though.

---

### Post by corey14 on 2014-06-05
My bad, thought I could copy and paste boxes.

```

[COLOR=#000000]sudo ethtool -s eth0 speed 100 duplex full autoneg off

```[/COLOR]

---

### Post by varunendra on 2014-06-06
> **corey14 said:**
> I don't understand why it would be beneficial for things to run slower is this to save bandwidth?
It's not about 'benefit', it's about 'compatibility'. Some router/switch firmware are buggy, sometimes the drivers are buggy, sometimes the cable is problematic.... all in a way that they simply fail to facilitate a working link at Gigabit speeds. In such cases, usually the driver or the router/switch automatically falls back to a lower speed that is easily achievable. If they don't for some reason, the driver allows us to use tools like 'ethtool' to do that manually so that at least we can get a working connection. So it is just a compromise when things refuse to work in their most optimal levels.

> **corey14 said:**
> Ran this code again thinking maybe it got cancelled out when I rebooted
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```After running it computer connected to my ethernet, I was pretty happy until I tested it and when I try access webpages on the internet its just continuously loading. My wifi is doing the same thing now. Had to swap computers, Hoping after reading up on the code ill understand though.

I have an exam tomorrow, and am also overloaded with some urgent office work. Hope someone else would be able to help you out with sufficient information. To help us help you, please provide us the outputs of (with "link=yes" status) -
```
ifconfig -a
route -n
nm-tool
cat /etc/network/interfaces
sudo ethtool eth0
dmesg | egrep -i 'jme|eth|dhclient'
```
..some more information may be needed later.

**PS:**
Yes, the 'ethtool -s...' command is temporary and its effect is lost on reboot. We can make it permanent if is proved to be helping and necessary.

---

### Post by corey14 on 2014-06-06
Cheers for explaining that im eager to learn as much as possible, got really busy today didn't have a chance to read up about much at all, don't stress about me ill continue trying to work this out, id definately appreciate your help when you have time again if I havent:) Goodluck with your exam.[B]

ifconfig -a [/B]
```

ifconfig -a 
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:5f:2f:d4   
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::beae:c5ff:fe5f:2fd4/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:205 errors:0 dropped:5 overruns:0 frame:0 
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:13670 (13.6 KB)  TX bytes:8654 (8.6 KB) 
          Interrupt:45  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:65536  Metric:1 
          RX packets:237 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:237 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:17485 (17.4 KB)  TX bytes:17485 (17.4 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 48:5d:60:e2:36:e5   
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::4a5d:60ff:fee2:36e5/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:959 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:128656 (128.6 KB)  TX bytes:12949 (12.9 KB) 
 
```
 
**route -n **
```
 
route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
0.0.0.0         198.142.131.29  0.0.0.0         UG    0      0        0 eth0 
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0 
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0 
198.142.131.29  0.0.0.0         255.255.255.255 UH    0      0        0 eth0 
 
```

**nm-tool  **
```
 nm-tool 
 
NetworkManager Tool 
 
State: connected (global) 
 
- Device: wlan0  [ISSWA] ------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            ath9k 
  State:             connected 
  Default:           no 
  HW Address:        48:5D:60:E2:36:E5 
 
  Capabilities: 
    Speed:           1 Mb/s 
 
  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 
 
  Wireless Access Points (* = current AP) 
    BUILTONWIFI:     Infra, 00:1D:AA:2B:E2:D8, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2 
    *ISSWA:          Infra, F0:82:61:AE:7D:BF, Freq 2412 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2 
    auto_net:        Infra, 00:04:ED:D4:55:29, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA2 
 
  IPv4 Settings: 
    Address:         192.168.0.5 
    Prefix:          24 (255.255.255.0) 
    Gateway:         192.168.0.1 
 
    DNS:             192.168.0.1 
 
 
- Device: eth0  [Ethernet connection 1] ---------------------------------------- 
  Type:              Wired 
  Driver:            jme 
  State:             connected 
  Default:           yes 
  HW Address:        BC:AE:C5:5F:2F:D4 
 
  Capabilities: 
    Carrier Detect:  yes 
    Speed:           100 Mb/s 
 
  Wired Properties 
    Carrier:         on 
 
  IPv4 Settings: 
    Address:         192.168.0.1 
    Prefix:          24 (255.255.255.0) 
    Gateway:         198.142.131.29 
 
```
[B]
cat /etc/network/interfaces [/B]
```
cat /etc/network/interfaces 
# interfaces(5) file used by ifup(8) and ifdown(8) 
auto lo 
iface lo inet loopback 
 
```
 [B]
 sudo ethtool eth0[/B]
```

sudo ethtool eth0
Settings for eth0: 
    Supported ports: [ TP MII ] 
    Supported link modes:   10baseT/Half 10baseT/Full  
                            100baseT/Half 100baseT/Full  
                            1000baseT/Half 1000baseT/Full  
    Supported pause frame use: No 
    Supports auto-negotiation: Yes 
    Advertised link modes:  Not reported 
    Advertised pause frame use: No 
    Advertised auto-negotiation: No 
    Speed: 100Mb/s 
    Duplex: Full 
    Port: MII 
    PHYAD: 1 
    Transceiver: internal 
    Auto-negotiation: off 
    Supports Wake-on: pg 
    Wake-on: g 
    Current message level: 0x000020c6 (8390) 
                   probe link rx_err tx_err hw 
    Link detected: yes 
 
```
 
 **dmesg | egrep -i 'jme|eth|dhclient **
```
dmesg | egrep -i 'jme|eth|dhclient 
> 

```

I left the last code for over 10 mins when I ran it thinking it might just take awhile nothing happened, tried a second time same thing?

---

### Post by TheFu on 2014-06-06
So it broke after a reboot?
Did you apply the **ethtool** command again - the one with all the options to slow the connection down?
If you add that 1 line to your **/etc/rc.local** file, it will happen at every reboot.  If your router or switch are 10/100 and not gigE, I'd stop there and call this solved.

If you want to go further, swap the cable for a known-good CAT5e cable.
Try a different port on the device (switch/router).
Read up on the other options that ethtool and the driver used support - that reading should lead to different options that might make it work with your specific switch/router - or at least known incompatibilities. 

If it doesn't, I'd start suspecting a failed gate inside the network chip.  1 small failure that can be worked around is a warning that something else will fail.  Time to look for mitigation strategies, like getting a replacement NIC.

Does this make sense?  BTW, I don't have school pressures (haven't in years), just life gets in the way sometimes. ;)

---

### Post by varunendra on 2014-06-06
> **corey14 said:**
>  **dmesg | egrep -i 'jme|eth|dhclient **
```
dmesg | egrep -i **[COLOR="#FF0000"]'[/COLOR]jme|eth|dhclient** *[COLOR="#FF0000"]<---- closing quote (**'**) missing[/COLOR]*
> 

```

I left the last code for over 10 mins when I ran it thinking it might just take awhile nothing happened, tried a second time same thing?
Because you didn't type the closing single quote mark in the command, leaving the terminal thinking that you are going to type more, then close it with closing quote mark. :)

The outputs look solid, did you have a working connection? If not, I'd blame that weird gateway.
Why do you have a gateway that is different than your network subnet? Is that intentional or a mistake?
Is the IP automatically acquired from dhcp or is manually configured in Network Manager?

> **TheFu said:**
> BTW, I don't have school pressures (haven't in years)
:lolflag: However it goes, at least the exam made me feel younger :p

---

### Post by corey14 on 2014-06-09
Sorry its taken me so long to reply guys, got way to busy to work on this over the weekend.

> **TheFu said:**
> So it broke after a reboot?
Did you apply the **ethtool** command again - the one with all the options to slow the connection down?
If you add that 1 line to your **/etc/rc.local** file, it will happen at every reboot.  If your router or switch are 10/100 and not gigE, I'd stop there and call this solved.

If you want to go further, swap the cable for a known-good CAT5e cable.
Try a different port on the device (switch/router).
Read up on the other options that ethtool and the driver used support -  that reading should lead to different options that might make it work  with your specific switch/router - or at least known incompatibilities. 

If it doesn't, I'd start suspecting a failed gate inside the network  chip.  1 small failure that can be worked around is a warning that  something else will fail.  Time to look for mitigation strategies, like  getting a replacement NIC.

Does this make sense?  BTW, I don't have school pressures (haven't in years), just life gets in the way sometimes. :wink:

Yeh after I apply the command again ethernet connects, just never loads anything. Ill have a read now, actually got time for once aha. Yeh that makes sense.

> **varunendra said:**
> 
The outputs look solid, did you have a working connection? If not, I'd blame that weird gateway.
Why do you have a gateway that is different than your network subnet? Is that intentional or a mistake?
Is the IP automatically acquired from dhcp or is manually configured in Network Manager?


IP address should be automatically aquired, I made some changes based on what id read in other posts before I made my post, I thought id reversed all changes but I might have missed something. It says ethernet is connected but I cant load anything, doesnt time out though which I thought would normally happen if I had no connection. Ill have a look see if I can fix that gateway thing but any tips would be helpful:)

Also here is the output of that command corrected.
[B]
egrep -i 'jme|eth|dhclient' [/B]
```
dmesg | egrep -i 'jme|eth|dhclient' 
[    1.481209] jme: JMicron JMC2XX ethernet driver version 1.0.8 
[    1.481267] jme 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control 
[    1.531594] jme 0000:02:00.0 eth0: JMC250 Gigabit Ethernet chiprev:23 pcirev:3 macaddr:bc:ae:c5:5f:2f:d4 
[   12.384374] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   14.165838] type=1400 audit(1402048951.391:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=355 comm="apparmor_parser" 
[   14.165888] type=1400 audit(1402048951.391:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=355 comm="apparmor_parser" 
[   14.168072] type=1400 audit(1402048951.395:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=355 comm="apparmor_parser" 
[   14.173275] type=1400 audit(1402048951.399:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=355 comm="apparmor_parser" 
[   15.543365] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   16.645747] ACPI Error: Method parse/execution failed [\OWLS] (Node ffff88007bf73aa0), AE_NOT_EXIST (20131115/psparse-536) 
[   16.645771] ACPI Error: Method parse/execution failed [\AMW0.DEVS] (Node ffff88007bf455c8), AE_NOT_EXIST (20131115/psparse-536) 
[   16.645797] ACPI Error: Method parse/execution failed [\AMW0.WMBC] (Node ffff88007bf45348), AE_NOT_EXIST (20131115/psparse-536) 
[   19.752849] jme 0000:02:00.0: irq 45 for MSI/MSI-X 
[   19.752979] jme 0000:02:00.0 eth0: Link is down 
[   19.776661] jme 0000:02:00.0 eth0: Link is down 
[   19.776762] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   19.778730] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   20.762923] type=1400 audit(1402048957.987:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=796 comm="apparmor_parser" 
[   20.762977] type=1400 audit(1402048957.987:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=796 comm="apparmor_parser" 
[232457.959817] jme 0000:02:00.0 eth0: Link is up at Forced: 100 Mbps, Full-Duplex, MDI 
[232457.961000] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
 
 
```

---

### Post by varunendra on 2014-06-11
Please let us know if you're still stuck with it. You can set the gateway in the Network Manager settings (nm-applet menu > "Edit Connections..." > edit your connection > "IPv4 Settings" > method "Manual" > fill in the desired settings > Save > Close), or, if using automatic settings, must fix it in the router or whichever device/computer is answering the DHCP requests on the network. For a detailed help, please explain your network in detail. :)

---

