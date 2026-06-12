---
title: "Wireless connection has disappeared! Ubuntu 12.04 LTS on Advent T1600"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by cbthomson on 2014-02-02
Hi, 

I'm running Ubuntu 12.04 on an Advent T1600, all of a sudden today it did not connect to wifi automatically when booted.

When I checked the settings the option for a wireless connection is completely missing, even though if I go into Network Connections it shows that I was connected wirelessly to my home connection this morning!

I've run the usual requests and the outputs are below:

lspci gives:

```
00:00.0 Host bridge:Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev07)00:02.0 VGA compatiblecontroller: Intel Corporation Mobile 4 Series Chipset IntegratedGraphics Controller (rev 07) 
00:02.1 Displaycontroller: Intel Corporation Mobile 4 Series Chipset IntegratedGraphics Controller (rev 07) 
00:1a.0 USB controller:Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev03) 
00:1a.1 USB controller:Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev03) 
00:1a.2 USB controller:Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev03) 
00:1a.7 USB controller:Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev03) 
00:1b.0 Audio device:Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge:Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 
00:1c.3 PCI bridge:Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) 
00:1d.0 USB controller:Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev03) 
00:1d.1 USB controller:Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev03) 
00:1d.2 USB controller:Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev03) 
00:1d.7 USB controller:Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev03) 
00:1e.0 PCI bridge:Intel Corporation 82801 Mobile PCI Bridge (rev 93) 
00:1f.0 ISA bridge:Intel Corporation ICH9M LPC Interface Controller (rev 03) 
00:1f.2 SATAcontroller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 portSATA Controller [AHCI mode] (rev 03) 
00:1f.3 SMBus: IntelCorporation 82801I (ICH9 Family) SMBus Controller (rev 03) 
04:00.0 Ethernetcontroller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCIExpress Fast Ethernet controller (rev 02)  
```

lsusb gives:

```
Bus 001 Device 001: ID1d6b:0002 Linux Foundation 2.0 root hubBus 002 Device 001: ID1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID1d6b:0001 Linux Foundation 1.1 root hub 
Bus 008 Device 001: ID1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader  
```

ifconfig gives:

```
eth0      Linkencap:Ethernet  HWaddr 00:03:0d:ba:b3:fb          inetaddr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr:fe80::203:dff:feba:b3fb/64 Scope:Link 
          UP BROADCASTRUNNING MULTICAST  MTU:1500  Metric:1 
          RXpackets:2993 errors:0 dropped:0 overruns:0 frame:0 
          TXpackets:3046 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0txqueuelen:1000 
          RXbytes:2121509 (2.1 MB)  TX bytes:471532 (471.5 KB) 
          Interrupt:43Base address:0x4000 


lo        Linkencap:Local Loopback  
          inetaddr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr:::1/128 Scope:Host 
          UP LOOPBACKRUNNING  MTU:16436  Metric:1 
          RXpackets:2216 errors:0 dropped:0 overruns:0 frame:0 
          TXpackets:2216 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0txqueuelen:0 
RXbytes:178372 (178.3 KB)  TX bytes:178372 (178.3 KB)  
```

iwconfig gives:

```
o        no wirelessextensions.

eth0      no wirelessextensions.  
```

lsmod gives:

```
Module                 Size  Used bypci_stub              12550  1 
vboxpci               22911  0 
vboxnetadp            25616  0 
vboxnetflt            27240  0 
snd_hda_codec_hdmi    31823  1 
snd_hda_codec_realtek  174313  1 
vboxdrv              285013  3 vboxpci,vboxnetadp,vboxnetflt 
joydev                17393  0 
snd_hda_intel         32719  3 
snd_hda_codec        109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep             13276  1 snd_hda_codec 
snd_pcm               80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi          13132  0 
snd_rawmidi           25424  1 snd_seq_midi 
snd_seq_midi_event    14475  1 snd_seq_midi 
snd_seq               51592  2 snd_seq_midi,snd_seq_midi_event 
rfcomm                38139  0 
psmouse               96744  0 
snd_timer             28931  2 snd_pcm,snd_seq 
bnep                  17830  2 
parport_pc            32114  0 
bluetooth            158447  10 rfcomm,bnep 
snd_seq_device        14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
ppdev                 12849  0 
binfmt_misc           17292  1 
serio_raw             13027  0 
mac_hid               13077  0 
snd                   62218  16snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                 428213  3 
drm_kms_helper        45466  1 i915 
drm                  197641  4 i915,drm_kms_helper 
soundcore             14635  1 snd 
snd_page_alloc        14115  2 snd_hda_intel,snd_pcm 
i2c_algo_bit          13199  1 i915 
video                 19115  1 i915 
lp                    17455  0 
parport               40930  3 parport_pc,ppdev,lp 
ums_realtek           17920  0 
r8169                 56396  0 
usb_storage           39646  1 ums_realtek 
```


sudo lshw -C network

```
*-network
       description:Ethernet interface 
       product:RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: RealtekSemiconductor Co., Ltd. 
       physical id: 0 
       bus info:pci@0000:04:00.0 
       logical name:eth0 
       version: 02 
       serial:00:03:0d:ba:b3:fb 
       size: 100Mbit/s 
       capacity:100Mbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pmmsi pciexpress msix vpd bus_master cap_list rom ethernet physical tpmii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration:autonegotiation=on broadcast=yes driver=r8169driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.64latency=0 link=yes multicast=yes port=MII speed=100Mbit/s 
resources:irq:43 ioport:3000(size=256) memory:f4000000-f4000fffmemory:f2000000-f200ffff memory:f2010000-f201ffff  
```



sudo iwlist wlan0 scan:

```
wlan0     Interfacedoesn't support scanning.  
```



uname -mr uname -mr:

[/CODE] 3.2.0-58-generic i686 [/CODE]


sudo service networkingrestart:

```
 
stop: Unknown instance:
networking stop/waiting 
```

I tried dmesg, but the output was too big for the terminal! I'm not sure that's a good thing. I am not very well versed in ubuntu, so please forgive me if I've missed anything. Even I can see from the outputs that there is something seriously wrong though!

Hope someone can give a hand. 

Thanks, 

C

---

### Post by varunendra on 2014-02-02
Since neither lspci nor lsusb show it, may be check the physical connection and/or try resetting the BIOS. These cards are usually in a user-serviceable area and can be accessed by removing some panel at the bottom with a proper screwdriver. The card itself is often fixed with a screw. Open it, pull out the card, re-seat it properly and check lspci/lsusb again.

**PS:**
Welcome to the forums :)

---

### Post by cbthomson on 2014-02-03
Thanks! I think this may be that most tenacious of problems, an intermittent one. I have returned from work today and the wireless connection has returned, albeit it keeps cycling through requests for the password to my router and won't yet connect. I may have to scan the rest of the forums to see if others have had similar difficulties.

If the same problem appears again I will get out the screwdriver and see what I can do, thanks!

Should I mark this solved? I've not done anything to solve it, but things appear to be working (roughly) again.

Thanks again!

---

### Post by cbthomson on 2014-02-03
Hi, 

Further to my previous, mysterious, issue [http://ubuntuforums.org/showthread.php?t=2203285](http://ubuntuforums.org/showthread.php?t=2203285) I have further problems!

I did nothing to fix the issue (option to connect wirelessly to internet had disappeared), but the wireless connection reappeared this evening; apparently of its own volition. Now, however, the connection is not showing automatically, and when I select it using the "Connect to a hidden wireless network" it cycles through repeated requests for authentication, but never connects.

Here are the usual scripts:

lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader 
```

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:03:0d:ba:b3:fb            inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:feba:b3fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1838 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:898829 (898.8 KB)  TX bytes:322675 (322.6 KB)
          Interrupt:44 Base address:0x4000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:91778 (91.7 KB)  TX bytes:91778 (91.7 KB)


wlan0     Link encap:Ethernet  HWaddr 00:22:5f:48:2a:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f8420000-f8420100 
```

iwconfig:

```
lo        no wireless extensions.


wlan0     802.11b/g  Mode:Managed  Frequency=2.422 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


eth0      no wireless extensions.
```

lsmod:

```
Module                  Size  Used by
vesafb                 13516  0 
pci_stub               12550  1 
vboxpci                22911  0 
vboxnetadp             25616  0 
vboxnetflt             27240  0 
vboxdrv               285013  3 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_hdmi     31823  1 
snd_hda_codec_realtek   174313  1 
joydev                 17393  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
psmouse                96744  0 
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq
r8187se               157152  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6           12687  1 r8187se
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17292  1 
soundcore              14635  1 snd
i915                  428213  3 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
mac_hid                13077  0 
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
r8169                  56396  0 
usb_storage            39646  1 ums_realtek
chris@chris-DIXONSXP:~$ 
```

sudo lshw -C network :

```
*-network               
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 22
       serial: 00:22:5f:48:2a:7c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8180 latency=0 multicast=yes wireless=802.11b/g
       resources: irq:17 ioport:3000(size=256) memory:fa000000-fa003fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:03:0d:ba:b3:fb
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.64 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:4000(size=256) memory:f6000000-f6000fff memory:f4000000-f400ffff memory:f4010000-f401ffff 
```


sudo iwlist wlan0 scan:

```
wlan0     No scan results
```

uname -mr:
 

```
3.2.0-58-generic i686
```


sudo service networkingrestart:


```
stop: Unknown instance:
networking stop/waiting 
```

Hope someone can offer some advice! Currently tied to the router by ethernet!

C

---

### Post by wildmanne39 on 2014-02-03
Please do not post duplicates, it dilutes community effort. Threads merged

I do realize that you may not think this is the same topic but it will be best to continue here since your original issue was never solved and varun is very good with these issues.

---

### Post by cbthomson on 2014-02-03
Ok, noted! I didn't think it was the same topic, but I see the logic. Thanks.

C

---

### Post by cbthomson on 2014-02-04
I should probably add that the wireless network I'm connecting to is not hidden (other devices can see and connect) and that it used to work absolutely no problem until the other day! Hope someone can assist. Thanks.

---

### Post by varunendra on 2014-02-04
So is the card not disappearing anymore?

If it is not a problem for you, I'd strongly recommend to check its physical status once, and it seems loose or you have the slightest bit of doubt, pull it out, clean its contact pins and re-seat it properly. Completely disappearing from system even once makes my highly doubtful about its physical status (pins/antenna contacts or physical defects), and the fact that "iwconfig" is showing signal level, noise level everything zero is further strengthening this doubt.

Antenna contacts are usually two plug-head wires that can be detached by pulling with minor force. It is not very uncommon for them to get loose.

If you are (or can make) sure that the physical status is good, then we may need some more info to troubleshoot the card. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

And if you have a fast Internet connection available, could you download and try 13.10 in live mode? This will give you a chance to try out the newer driver on the Laptop without making changes to the system.

---

### Post by cbthomson on 2014-02-05
Hi Varun, 

Thanks very much for this.

Yeah, the option to connect is now appearing - but the computer is not seeing any available wireless networks. I can select my home network via "Connect to a hidden wireless network", but it appears to search, then ask for the password. I enter this, but it fails to connect and cycles round again, asking for the password and never connecting.

I will be using the laptop (via ethernet) for work this afternoon, but will check the card later on today as per your suggestion. Should I (as a relative philistine in these matters) be able to see which card I should be checking without ruining anything else?

I have a pretty fair connection just now, but I don't know how to try 13.10 in live mode. I assume there will be a guide on here somewhere, and will give that a go after checking the physical connection and running the scripts you have suggested.

Thanks again, 

Chris

---

### Post by cbthomson on 2014-02-05
I got frustrated and opened up the back panel, which I assume is the "user servicable area". I'd have to take the whole device to pieces to get any more access. To be honest I didn't know what I was looking at/for. However, there were a few cards and transistors which I could see and which I checked by hand to see if they were solid. Nothing appeared amiss.

I then ran the wireless script you suggested Varun, and here is the output:

```
*************** info trace ***************


***** uname -a *****


Linux chris-DIXONSXP 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:40:43 UTC 2013 i686 i686 i386 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise


***** lspci *****


04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199]
	Kernel driver in use: r8180
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Elitegroup Computer Systems Device [1019:90b3]
	Kernel driver in use: r8169


***** lsusb *****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     802.11b/g  Mode:Managed  Frequency=2.422 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




***** rfkill *****




***** lsmod *****


r8187se               157152  0 
eeprom_93cx6           12687  1 r8187se


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.66
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8180
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****


wlan0     No scan results




***** resolv.conf *****


nameserver 127.0.0.1
search home


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****


filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/staging/rtl8187se/r8187se.ko
description:    Linux driver for Realtek RTL8180 / RTL8185 WiFi cards
author:         Andrea Merello <andreamrl@tiscali.it>
license:        GPL
license:        GPL
author:         Copyright (C) 2004 Intel Corporation <jketreno@linux.intel.com>
description:    802.11 data/management/control stack
license:        GPL
description:    HostAP crypto
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: TKIP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: CCMP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: WEP
author:         Jouni Malinen
srcversion:     8F6B9881D2F05C4A11E407D
alias:          pci:v000010ECd00008199sv*sd*bc*sc*i*
depends:        eeprom_93cx6
staging:        Y
intree:         Y
vermagic:       3.2.0-58-generic SMP mod_unload modversions 686 
parm:           ifname:string
parm:           devname: Net interface name, wlan%d=default
parm:           hwseqnum: Try to use hardware 802.11 header sequence numbers. Zero=default (int)
parm:           hwwep: Try to use hardware WEP support. Still broken and not available on all cards (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)




***** udev rules *****


# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8199 (r8180)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[   24.718642] r8187se: module is from the staging directory, the quality is unknown, you have been warned.
[   24.739364] r8180: Initializing module
[   24.739366] r8180: Wireless extensions version 22
[   24.739369] r8180: Initializing proc filesystem
[   24.739410] r8180: Configuring chip resources
[   24.739430] r8180 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.739441] r8180 0000:04:00.0: setting latency timer to 64
[   24.744226] r8180: Channel plan is 2
[   24.744236] r8180: MAC controller is a RTL8187SE b/g
[   24.746406] r8180: usValue is 0xf00
[   24.789929] r8180: EEPROM version 104
[   24.794279] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[   24.794832] r8180: IRQ 17
[   24.795721] r8180: Driver probe completed
[   25.558111] r8180: Bringing up iface
[   25.756626] r8180: Card successfully reset
[   26.496992] r8180: WIRELESS_MODE_G
[   26.516552] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.516938] ADDRCONF(NETDEV_UP): wlan0: link is not ready


****************** done ******************
```

---

### Post by varunendra on 2014-02-05
> **cbthomson said:**
> I have a pretty fair connection just now, but I don't know how to try 13.10 in live mode.
Create a bootable DVD or USB from the ISO of 13.10 the same way as you created the one to install Ubuntu. I recommend downloading the ISO via torrents to ensure the integrity of the download : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

Boot from the DVD/USB and when it asks to "Try" or "Install", choose "Try" option. That is what is called a "Live Session" - running Ubuntu directly from the DVD or USB without installing it.

I recommended trying 13.10 because the driver that your wireless card uses is an experimental one and so its newer versions have more chance of working properly. We can install the newer driver on your current installation but it is not guaranteed to perform any better. Besides we are not yet sure whether the problem is in the hardware or the driver.

Detailed guides for creating Live DVD/USB and booting from them are given on the main download page : [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) (see the links below the "Try Ubuntu before you install it" heading).

> **cbthomson said:**
> I got frustrated and opened up the back panel, which I assume is the "user servicable area". I'd have to take the whole device to pieces to get any more access. To be honest I didn't know what I was looking at/for.
Plenty of images of the card here : [http://www.ebay.com/bhp/atheros-ar5b195](http://www.ebay.com/bhp/atheros-ar5b195)

The two holes at the corner of the card are where it is fixed with screws, and the two tiny brass sockets almost adjacent to these two holes are where the antenna wires are attached. The Antenna wire heads are simple plugs that are pushed into these sockets and may be pulled out with minor force.

You need to check these two wires to make sure the plugs are not loose. To be extra sure, you can also pull out the card (after removing the screws) and push it back into its PCI slot after cleaning its contact pins.

This card has been reported to be problematic with Linux but the output of iwconfig is making me suspicious of its physical status. We may try a few things, including newer versions of the driver if everything looks okay with its fitting.

---

### Post by Elfy on 2014-02-05
Please use code tags. Thank you.

If you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by cbthomson on 2014-02-05
Thanks Varun, 

I've opened it up again and definitely cannot see that card; I even took a snapshot and compared it to the images on ebay to be certain. As mentioned above, any further examination would involve me taking the whole back case off - I had all the screws out earlier on, but it felt like I'd need a little elbow grease to remove it. Whilst I am capable of that, I am also concerned that I might break something and so I held off. Should I give it a try?

Currently downloading 13.10 to see what effect this has on it. I'll try that before taking the back off the device and will provide an update asap.

Elfy, I will ensure I use code tags in all future posts. I had used quick reply and - as you have pointed out - the option wasn't there. I'll do it manually next time if I use that function. ```
 Cheers. 
```

---

### Post by cbthomson on 2014-02-05
The universal USB installer isn't recognising the USB drive! This is frustrating. I will have to either get another USB or get a DVD to use tomorrow, as I have to be elsewhere tonight. Thanks for your continued help Varun, I'll provide an update either tomorrow or Friday, as tomorrow is going to be a long, long day for me anyway.

C

---

### Post by varunendra on 2014-02-06
Hmm.. can we see the snapshot of the whole back panel when you have opened it? Just the part that you could open easily. The card may not be exactly same in shape or size (the ones listed on the page were all "half sized" cards), but it must be there somewhere. Also, it is accessible in *most* laptops, but not *all* (like some HCL Emachines). So it is possible that your model does not provides user access to it. A snapshot should tell us everything regarding that.

For creating bootable USB, you may also try [Unetbootin]("http://unetbootin.sourceforge.net/") (most recommended here), or if you are running some version of Ubuntu, you can use its native "Startup Disk Creator" program to create the Live USB. My preferred way is to boot a Virtual Machine (on VMware or VirtualBox) > attach the target USB to it and let it get detected by the VM > use the Live Session in the VM to run its Startup Disk Creator program to create the Live USB. This ensures there are no issues due to version difference.

Another simple method (if you are running Ubuntu) is the dd command. It is a bit risky in the sense that if you used wrong device name as target, it will be permanently overwritten. So be extra careful with this. Assuming your USB drive is "/dev/sd**x**" (confirm by seeing the output of "mount" command) -
```
sudo dd if=*<the path of your iso file>* of=/dev/sd**x**
```
Change the 'x' with whatever letter has been assigned to your USB drive.

**PS:**
I wouldn't advice taking your laptop apart unless you have experience of doing that. A cheap USB wifi dongle can be found for less than $10 on ebay, while replacing a broken case would cost much more than that. ;)

---

### Post by cbthomson on 2014-02-10
Hi Varun, 

I've attached an image of the back of the machine just now. Will try to follow your instructions this afternoon and let you know how I get on, thanks!

C

---

### Post by varunendra on 2014-02-11
No wifi card there. :(

So that essentially means taking the whole case apart just to be able to access the wireless card, which I would never recommend unless you are an expert.

Let's hope the 13.10 automagically fixes everything..

---

### Post by T Bone on 2014-02-11
Hmmmmm, now using 13.10 - and automatically logging in under a user name I used previously: this is "cbthomson" though! 

I bought a new USB (last one was encrypted, and kept turning itself off when the computer restarted) and made a startup disk. Alles gut!

Importantly, I am logging in wirelessly using 13.10 - the change has automagically fixed it! I will need further advice though: should I change to 13.10, or should I seek out the driver and install that with my current distro?

Thanks, 

C

---

### Post by cbthomson on 2014-02-11
In a bizarre twist; I've rebooted in 12.04 - I've been logged on here as cbthomson, and the wifi connection has started up automatically with no issues! In which case, I'll stick with 12.04 for now; although 13.10 was pretty cool.

Is there anything I can check or run that would give those with more ubuntu tuned minds an insight into this for future issues that other users might have?

C

---

### Post by trundlenut on 2014-02-11
Your wifi card may be under the keyboard, if there are no other removable panels on the back.

---

### Post by varunendra on 2014-02-11
> **T Bone said:**
> Importantly, I am logging in wirelessly using 13.10 - the change has automagically fixed it! I will need further advice though: should I change to 13.10, or should I seek out the driver and install that with my current distro?
If you believe it was the newer driver in 13.10, you may install just its driver on the current version (12.04). It can be as simple as installing the backported drivers from withing the repository, or can be a little more work as downloading the backports package > compiling > installing it.

> **cbthomson said:**
> In a bizarre twist; I've rebooted in 12.04 - I've been logged on here as cbthomson, and the wifi connection has started up automatically with no issues! In which case, I'll stick with 12.04 for now; although 13.10 was pretty cool.

Is there anything I can check or run that would give those with more ubuntu tuned minds an insight into this for future issues that other users might have?
Apart from syslog and dmesg (the log files /var/log/syslog and /var/log/dmesg), I don't think anything else can shed more light on success/failure reasons. They are huge, so you may have to analyse them yourself to be able to post only the relevant parts *(or upload them at pastebin.ubuntu.com, and just give their link here, although not many people would be interested in analyzing the whole log unless you ask any of them specifically for help)*.

For usual information, you may use the detailed output options with regular commands, like "lspci -vvnn", followed by stripping out the details of all but the wifi related info. The "sudo lshw -C network" command can also provide some useful info, but probably not more useful than what we already have.

PS:
For the dual user id issue, you may (probably 'Should') post a thread in [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123"), requesting the admins whatever you want with your accounts (like which one you want to keep, which one to discard).

---

### Post by T Bone on 2014-02-12
Thanks again Varun, if it won't be of any use to people I'll not bother with posting any outputs - it was just in case something similar happened to others.

At present I'll just let things run as they are; a little knowledge can be a dangerous thing, and I have so little knowledge it is scary.

From looking at the Resolution pages, it seems the advice to people who have multiple IDs after the changeover to SSO is just to ignore the one they don't want, so I'll check and see which of the two accounts is linked to my Ubuntu One account and use that one.

One final time, thanks for all your help Varun - it is greatly appreciated. :)

---

### Post by cbthomson on 2014-02-12
It looks like I had two email accounts attached to these, that was the problem. Unfortunately when hotmail and outlook merged all my emails get stuck in the same place, so I hadn't differentiated. I'll mark this thread as solved and close this account. Thanks.

---

### Post by varunendra on 2014-02-12
> **T Bone said:**
> One final time, thanks for all your help Varun - it is greatly appreciated. :)

You're welcome, as always ! :)

---

### Post by T Bone on 2014-04-05
In a pretty frustrating twist, the same thing has happened again! Unfortunately this time loading 13.04 isn't helping either, and the ethernet cable isn't connecting - it is going through a cycle of attempting to connect, failing and trying again! Any ideas? I'm fearing that there may be some terminal problem here :(

---

### Post by varunendra on 2014-04-05
I suggest you post a new thread with a suitable title, post the details of problems there, and give me the link (here or via PM).

I am extremely short of time these days, so a new thread will have a much better chance of getting help from other people, who may be able to offer better solution and be more consistent than I can be. I'm a bit free today, but may not be in the coming weeks.

In fact, I am thinking of posting in your new thread only if I found some obvious problem and a (hopefully) definite solution for it. Fortunately for you, there ARE people here who are much-much better than me with these issues. :)

---

### Post by T Bone on 2014-04-05
Will do, thanks!

---

