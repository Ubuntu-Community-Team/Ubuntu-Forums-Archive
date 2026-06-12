---
title: "Ethernet connection not working, Ubuntu 14.04LTS"
date: 2014-08-15
forum: Networking &amp; Wireless
---

### Post by chhitizsubedi on 2014-08-15
When I connect the Ethernet LAN cable I am not able to get internet signal and surf the internet. The same cable when connected to another computer allows direct net surfing. I am using Dell Inspiron 4030 with Ubuntu 14.04LTS.
The wireless-info.txt file reads as follows:
```



########## wireless info START ##########


Report from: 15 Aug 2014 14:17 NPT +0545


Script from: 13 Aug 2014 19:23 UTC +0000


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Ubuntu


##### lspci #####




12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: bcma-pci-bridge


13:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Dell Device [1028:0466]
    Kernel driver in use: atl1c


##### lsusb #####


Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0c45:6482 Microdia 
Bus 001 Device 012: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
Bus 001 Device 007: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 001 Device 006: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####




##### rfkill #####


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


brcmsmac              529837  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
b43                   356470  0 
mac80211              546051  2 b43,brcmsmac
cfg80211              409394  3 b43,brcmsmac,mac80211
ssb                    51854  1 b43
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
bcma                   42043  3 b43,brcmsmac
wmi                    18673  1 dell_wmi


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


eth0      Link encap:Ethernet  HWaddr f0:4d:a2:b7:89:1f  
          inet6 addr: fe80::f24d:a2ff:feb7:891f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1311 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:316122 (316.1 KB)


wlan0     Link encap:Ethernet  HWaddr c0:cb:38:35:7a:1a  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c2cb:38ff:fe35:7a1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26737364 (26.7 MB)  TX bytes:7967390 (7.9 MB)




##### iwconfig #####


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"TP-LINK_906730"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:4A:00:90:67:30   
          Bit Rate:28.9 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:190  Invalid misc:449   Missed beacon:0




##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####




NetworkManager Tool


State: connected (global)


- Device: 00:23:76:91:CE:B7 ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no


  Capabilities:




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        F0:4D:A2:B7:89:1F


  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s


  Wired Properties
    Carrier:         on




- Device: wlan0  [TP-LINK_906730] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        C0:CB:38:35:7A:1A


  Capabilities:
    Speed:           28 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    pokhara Internet_Bandipur3: Infra, 00:27:22:74:40:47, Freq 2447 MHz, Rate 54 Mb/s, Strength 57 WEP
    pokhara Internet_Bandipur1: Infra, 00:27:22:74:EC:31, Freq 2417 MHz, Rate 54 Mb/s, Strength 50 WEP
    pokhara Internet_Bandipur2: Infra, 00:27:22:74:EB:36, Freq 2442 MHz, Rate 54 Mb/s, Strength 40 WEP
    *TP-LINK_906730: Infra, C0:4A:00:90:67:30, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    Broadlink WIFI:  Infra, 00:19:BE:80:86:A1, Freq 2457 MHz, Rate 54 Mb/s, Strength 22


  IPv4 Settings:
    Address:         192.168.1.108
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1






##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iw reg get #####


country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


##### iwlist channels #####


lo        no frequency information.


eth0      no frequency information.


wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.412 GHz (Channel 1)




##### iwlist scan #####


/home/chhitiz/Downloads/wireless_script.txt: line 148: syntax error in conditional expression
/home/chhitiz/Downloads/wireless_script.txt: line 148: syntax error near `]*Frequency:'
/home/chhitiz/Downloads/wireless_script.txt: line 148: `    if [[ $IWLISTSCAN =~ ^[ ]*Frequency: ]]; then'

```

---

### Post by Iowan on 2014-08-15
Does it work if you disable the wireless connection?

---

### Post by chhitizsubedi on 2014-08-15
It does not work even when I disable the wireless connection.

---

### Post by chhitizsubedi on 2014-08-15
When I entered the code it showed:
```

chhitiz@chhitiz-Inspiron-N4030:~$ sudo /etc/init.d/network-manager restart
sudo: /etc/init.d/network-manager: command not found

```

---

### Post by varunendra on 2014-08-15
Please show us the output of -
```
sudo lshw -C network
```

---

### Post by chhitizsubedi on 2014-08-15
output is
```

chhitiz@chhitiz-Inspiron-N4030:~$ sudo lshw -C network
[sudo] password for chhitiz: 
  *-network               
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:fbb00000-fbb03fff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: c1
       serial: f0:4d:a2:b7:89:1f
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:48 memory:fba00000-fba3ffff ioport:e000(size=128)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: c0:cb:38:35:7a:1a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.13.0-32-generic firmware=610.812 ip=192.168.1.108 link=yes multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by varunendra on 2014-08-15
Please try -
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

Does it make the ethernet work? If not, please post back the output of -
```
sudo ethtool eth0
```

**PS:**
Not related to the Ethernet, but there is a potential problem with your wireless interface too. That is - two conflicting drivers (b43 and brcmsmac) loading for the same card. You should blacklist the wrong one to make sure the wifi works without problems -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by chhitizsubedi on 2014-08-15
Even after entering the code the ethernet connection didnt work:

The output is:
```

Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Speed: 10Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x0000003f (63)
			       drv probe link timer ifdown ifup
	Link detected: yes

```

P.S. Thanks for the advise. Wireless network is running better now.

---

### Post by varunendra on 2014-08-15
Did you reboot before posting the above output? Because if you got no errors while running the "ethtool -s...." command, either the router is from Jurrassic age (only supports upto 10Mbps), or you rebooted before posting above, thus resetting the adapter. [s]Although the output is slightly confusing to me. It has indications of both kinds - changes applied (autoneg off) and they didn't (still 10 Mbps)[/s] **Edit :** wrong observation, autoneg is still on, strongly suggesting the "ethtool -s..." command either didn't take effect, or you rebooted so the changes got lost -
> **chhitizsubedi said:**
> ```

Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	**Speed: [COLOR="#FF0000"]10Mb/s[/COLOR]**
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	**Auto-negotiation: [COLOR="#FF0000"]on[/COLOR]**
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x0000003f (63)
			       drv probe link timer ifdown ifup
	Link detected: yes

```

Can you confirm whether your router supports 100 Mbps or not? Have you tried changing the cable with a tested one? Or tested the current one successfully on other computers?

---

### Post by chhitizsubedi on 2014-08-15
I did not reboot after the ethtool -s.... command. Just after I executed that command I executed ethtool eth0. The cable I use works perfectly on other computers running Windows 7 OS but I dont have any Ubuntu PCs to test it on. The router is a new one. It does support speed upto 100 Mb/s when used on wireless. Should I try the command once again or what may be the problem.
Thank you for the help.

---

### Post by varunendra on 2014-08-15
Yes, please try these two commands this time -

First,
```
sudo mii-tool -F 100baseTx-FD eth0
```
If it returns any error messages, please post them here.

Second,
[indent]IF the above command is successful, then -
```
sudo mii-tool
```

IF the first command above failed with error messages, then try the 'ethtool -s' command again -
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```[/indent]

Then post back the output of -
```
sudo ethtool eth0
```
..to confirm the change.

---

### Post by Anders_Makowicz on 2014-12-27
I have that problem too

The outpout of `sudo lshw -C network`
```
canid@canid-G41M-ES2L:~$ sudo lshw -C network
[sudo] password for canid: 
  *-network               
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: f8:d1:11:03:a1:ee
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:d000(size=256) memory:f3000000-f30000ff memory:cff00000-cff1ffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 8a:90:4e:ca:01:53
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.51 link=yes multicast=yes


```

---

### Post by praseodym on 2014-12-27
Hi,

this card normally loads 2 drivers, **8139too** and **8139cp**, check
```

lsmod
```
If so, blacklist the wrong one:
```

echo "blacklist 8139cp" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot.

---

### Post by Anders_Makowicz on 2014-12-28
`lsmod`:
```
Module                  Size  Used by
joydev                 17381  0 
bnep                   19624  0 
rfcomm                 69160  0 
bluetooth             391136  4 bnep,rfcomm
binfmt_misc            17468  1 
rndis_wlan             50281  0 
rndis_host             14503  1 rndis_wlan
cdc_ether              14351  1 rndis_host
usbnet                 43913  3 rndis_host,rndis_wlan,cdc_ether
cfg80211              484040  1 rndis_wlan
radeon               1522640  3 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
snd_hda_intel          56451  10 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
hid_a4tech             12651  0 
hid_generic            12548  0 
snd_hwdep              13602  1 snd_hda_codec
usbhid                 52659  0 
usb_storage            62209  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
hid                   106148  3 hid_a4tech,hid_generic,usbhid
coretemp               13435  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
kvm_intel             143187  0 
gpio_ich               13476  0 
ttm                    85150  1 radeon
snd_seq_midi           13324  0 
kvm                   455835  1 kvm_intel
drm_kms_helper         55071  1 radeon
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
drm                   303102  5 ttm,drm_kms_helper,radeon
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
i2c_algo_bit           13413  1 radeon
snd                    69322  31 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
serio_raw              13462  0 
lpc_ich                21080  0 
ppdev                  17671  0 
parport_pc             32701  1 
lp                     17759  0 
mac_hid                13205  0 
parport                42348  3 lp,ppdev,parport_pc
psmouse               106714  0 
8139too                33544  0 
8139cp                 27953  0 
mii                    13934  3 usbnet,8139cp,8139too


```

`echo "blacklist 8139cp" | sudo tee -a /etc/modprobe.d/blacklist.conf`
```
canid@canid-G41M-ES2L:~$ echo "blacklist 8139cp" | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for canid: 
blacklist 8139cp
canid@canid-G41M-ES2L:~$ 


```

did `lsmod` after reboot again:
```
canid@canid-G41M-ES2L:~$ lsmod
Module                  Size  Used by
joydev                 17381  0 
bnep                   19624  0 
rfcomm                 69160  0 
bluetooth             391136  4 bnep,rfcomm
binfmt_misc            17468  1 
rndis_wlan             50281  0 
rndis_host             14503  1 rndis_wlan
cdc_ether              14351  1 rndis_host
usbnet                 43913  3 rndis_host,rndis_wlan,cdc_ether
cfg80211              484040  1 rndis_wlan
radeon               1522640  3 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
snd_hda_intel          56451  10 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
hid_a4tech             12651  0 
hid_generic            12548  0 
snd_hwdep              13602  1 snd_hda_codec
usbhid                 52659  0 
usb_storage            62209  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
hid                   106148  3 hid_a4tech,hid_generic,usbhid
coretemp               13435  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
kvm_intel             143187  0 
gpio_ich               13476  0 
ttm                    85150  1 radeon
snd_seq_midi           13324  0 
kvm                   455835  1 kvm_intel
drm_kms_helper         55071  1 radeon
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
drm                   303102  5 ttm,drm_kms_helper,radeon
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
i2c_algo_bit           13413  1 radeon
snd                    69322  31 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
serio_raw              13462  0 
lpc_ich                21080  0 
ppdev                  17671  0 
parport_pc             32701  1 
lp                     17759  0 
mac_hid                13205  0 
parport                42348  3 lp,ppdev,parport_pc
psmouse               106714  0 
8139too                33544  0 
8139cp                 27953  0 
mii                    13934  3 usbnet,8139cp,8139too


```

---

### Post by praseodym on 2014-12-28
Ok, try it now:
```

sudo modprobe -rfv 8139cp 8139too
sudo modprobe -v 8139too
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by Anders_Makowicz on 2014-12-28
```
canid@canid-G41M-ES2L:~$ sudo modprobe -rfv 8139cp 8139too
[sudo] password for canid: 
rmmod 8139cp
rmmod 8139too


```

```
canid@canid-G41M-ES2L:~$ sudo modprobe -v 8139too
insmod /lib/modules/3.13.0-43-generic/kernel/drivers/net/ethernet/realtek/8139too.ko 


```

```
canid@canid-G41M-ES2L:~$ sudo depmod -a
canid@canid-G41M-ES2L:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic


```

Also please take a look at the annex

Wired connection 1 is my phone that i use as antenna to have better wireless connection but that`s why i want to connect lan
I see this ethernet connection as in annex but it`s grayed out

Maybe it`s internet card broken?

---

### Post by praseodym on 2014-12-28
Doesn't seem to be broken. Start the applet via
```

gksudo nm-connection-editor
```
Remove any connection profile in "cable" and "DSL" and reboot.

---

### Post by Anders_Makowicz on 2014-12-28
I had to install gksu

Then i don`t know what do you mean, i did that commend and i don`t know how to check if these are ``DSL`` or ``cable``
I understand that ethernet is cable so i have to remove both that connections? 
In screenshot both say ``wired connection``

OK i removed that two connections and here are results without and with smartphone connection.
It doesn`t see second ethernet connection  without smartphone, isn`t it strange?

---

### Post by margazhang on 2015-12-08
The following simply method worked for me:

sudo gedit /etc/NetworkManager/NetworkManager.conf

Change "false" in the file to "true" and then save and reboot. The problem was gone!

---

### Post by koebes on 2016-01-17
Hi, i have the same issue on my HP compaq 8510W with ubuntu 14.04. Ethernet turns on and off all the time but won't connect. When I enter ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo ethtool -s eth0 speed 100 duplex full autoneg off[/FONT][/COLOR]
``` it works fine. But as soon as I restart, problem is back. So I suppose i have to make that ethtool command permanent somehow, but no Idea how to do that. Any help is appreciated.

After entering the ethtool command, the output of 

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo ethtool eth0[/FONT][/COLOR]
```[COLOR=#000000]

[/COLOR]is:

```


Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  Not reported
    Advertised pause frame use: No
    Advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: off
    MDI-X: off (auto)
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes




```

---

### Post by koebes on 2016-01-28
[COLOR=#000000]Received a private message with a solution and it worked fine for me:

You may try adding the command without 'sudo' -[/COLOR]
[COLOR=#000000]Code:
ethtool -s eth0 speed 100 duplex full autoneg off[/COLOR]
[COLOR=#000000]..to your [/COLOR]**/etc/rc.local file. Make sure that the last line in that file remains the "exit 0" line, so you actually have to insert the above line above that one. This is important about that file.**

---

### Post by Aviendha09 on 2016-02-06
> **margazhang said:**
> The following simply method worked for me:

sudo gedit /etc/NetworkManager/NetworkManager.conf

Change "false" in the file to "true" and then save and reboot. The problem was gone!

Yes. Thank you, this is the solution that worked for me. Problem started after I added a bluetooth dongle (a cheap one) . 

phew!

---

### Post by Lightwavers on 2016-06-03
> **praseodym said:**
> Ok, try it now:
```

sudo modprobe -rfv 8139cp 8139too
sudo modprobe -v 8139too
sudo depmod -a
sudo update-initramfs -u
```

I am having this problem, changing the thing to true did not fix it. When I try these commands, I get tons of errors:

lightwavers@Lightwavers:~$ sudo modprobe -rfv 8139cp 8139too
[sudo] password for lightwavers: 
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
lightwavers@Lightwavers:~$

lightwavers@Lightwavers:~$ sudo modprobe -v 8139too
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
insmod /lib/modules/4.2.0-36-generic/kernel/drivers/net/mii.ko 
insmod /lib/modules/4.2.0-36-generic/kernel/drivers/net/ethernet/realtek/8139too.ko 
lightwavers@Lightwavers:~$

lightwavers@Lightwavers:~$ sudo depmod -a
^Z
[1]+  Stopped                 sudo depmod -a
lightwavers@Lightwavers:~$



^ When I try this it just goes to the next line and hangs and I have to do ctrl+z to stop it.

When I try "sudo update-initramfs -u" this happens:
```

libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'
```

---

### Post by jeremy31 on 2016-06-03
Please post the result of ```
cat  /etc/modprobe.d/alsa-base.conf
```

Please use code tags- see my signature when posting terminal results

---

### Post by Lightwavers on 2016-06-04
OK. I got this:
```
lightwavers@Lightwavers:~$ cat  /etc/modprobe.d/alsa-base.conf# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7


# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }


# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
snd-hda-intel model=generic
```

---

### Post by jeremy31 on 2016-06-04
You need to make the last line in the alsa-base.conf file
```
options snd-hda-intel model=generic
```

You should be able to edit it with ```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by Lightwavers on 2016-06-04
That line is already at the end of the config.

```
# autoloader aliasesinstall sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7


# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }


# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
snd-hda-intel model=generic

```

---

### Post by Bashing-om on 2016-06-04
Lightwavers; Hello;

As I pass by ..

Please take note of the format for this type file . the lines begin with " options " .
Follow  jeremy31's advise ->

and
[INDENT][INDENT]make it so
[/INDENT][/INDENT]

---

### Post by Lightwavers on 2016-06-04
Sorry, I was rushed when I looked at it before. Anyways, I changed it to options, but it still just keeps trying to connect, failing, and then retrying when I try to use ethernet. I restarted the computer before trying.
```
# autoloader aliasesinstall sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7


# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }


# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=generic

```

---

### Post by jeremy31 on 2016-06-04
Lightwavers, please post results for ```
lspci -nnk | grep -iA2 net
```

I only connect using a cellular hotspot, so I am not the best support for ethernet in most cases

---

### Post by Lightwavers on 2016-06-04
lightwavers@Lightwavers:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller [1969:e091] (rev 13)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7920]
    Kernel driver in use: alx
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c070]
    Kernel driver in use: iwlwifi

---

### Post by jeremy31 on 2016-06-04
> **Lightwavers said:**
> lightwavers@Lightwavers:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller [1969:e091] (rev 13)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7920]
    Kernel driver in use: alx
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c070]
    Kernel driver in use: iwlwifi

I did say I am not the best with ethernet, but I do remember one issue with the alx module

Go into Network Manager settings for the wired connection and see if setting the MTU to 8192 helps

---

### Post by Lightwavers on 2016-06-04
Thanks for trying! I set it to 8192, but it still does the same thing.

---

### Post by Lightwavers on 2016-06-05
Anything else I can try? I followed advice on another thread that told me to put a line into two files that change something every time the computer boots up, if that matters.

---

### Post by jeremy31 on 2016-06-05
What was the command?  What thread?

---

### Post by Lightwavers on 2016-06-06
[https://askubuntu.com/questions/611781/ethernet-connection-not-working-after-installing-ubuntu-14-04-lts](https://askubuntu.com/questions/611781/ethernet-connection-not-working-after-installing-ubuntu-14-04-lts)

> **Bug Workaround Solution:**
[LIST=1]
[*]Add the line exec rmmod forcedeth at next line of "script" (above grep?) in the file /etc/init/module-init-tools.conf or /etc/init/kmod.conf)

[*]Add the line modprobe forcedeth msi=0 msix=0 to /etc/rc.local

[*]Restart the system to verify
[/LIST]


---

### Post by jeremy31 on 2016-06-06
Please undo those commands as they are for a different card.  Reboot

---

### Post by Lightwavers on 2016-06-07
OK, I did. It still isn't working though. Is there anything else to test?

---

### Post by jeremy31 on 2016-06-07
See the wireless script link in my signature and post the results

---

### Post by Lightwavers on 2016-06-07
I can no longer even use wifi, my computer is completely cut off from Internet, using iPod to post. When I try to connect to wifi, the network no longer shows up. It keeps retrying to connect to everything but nothing will show up. I'd go back to widows but I don't have the iso file and my usb is no longer working after plugging it into the computer.

---

### Post by jeremy31 on 2016-06-07
So what does ```
lspci -nnk | grep -iA2 net; rfkill list all
```
Show now?

Those commands or even reverting them should not have affected wifi

---

### Post by Lightwavers on 2016-06-07
It says:

02:00.0 Ethernet controller [0200]: Qualcomm Atherosclerosis Killer E220x Gigabit Ethernet Controller [1969:e091] (rev 13) Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7920] Kernel driver in use: Alx 03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b) Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c070] Kernel driver in use: iwlwifi 0: hci0: Bluetooth Soft blocked: no Hard blocked: no 1: phy0: Wireless LAN Soft blocked: no Hard blocked: no

And now my thumbs hurt. Is there a way to reset all the settings to default, even if it clears everything on my computer?

---

### Post by jeremy31 on 2016-06-08
You could see if holding the shift key at boot to get the Grub menu, then choose Advanced Options and select an older kernel to boot from allows you to connect

Also check wifi setting in Network Manager to see if the MTU is on auto and not somehow changed

---

### Post by Lightwavers on 2016-06-08
I selected many different versions with no changes. MTU was on auto. I even deleted the networks and re added them. I finally got a Windows 7 boot disk and tried that, but now I'm at the select language part and the keyboard and mouse are not responding.
Edit: fixed keyboard and mouse by messing with random boot settings, but the partitions are still there and I can't install on them because it says they are incompatible. Is there a way to get rid of the partitions or make them compatible? Deleting and formatting them don't work.

---

### Post by jacocal on 2016-10-24
I know its been 2 years since this post, but this helped a lot. Thanks!

---

### Post by rajamondal369 on 2016-11-19
When i install ubuntu 14.04 and 16.04 on my desktop , ethernet network does not shown . After long internet search when i put the command in terminal : 

_***sudo ethtool -s enp2s0 speed 100 duplex full autoneg off  ***_for ubuntu 16.04 and *******_sudo ethtool -s eth0 speed 100 duplex full autoneg off _*** for ubuntu14.04 , it will find ethernet network and connect to internet automatically . After every restart ,i have to do so to find ethernet network . Please help me.

---

