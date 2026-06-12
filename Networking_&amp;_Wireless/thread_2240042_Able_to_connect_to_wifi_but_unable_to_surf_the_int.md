---
title: "Able to connect to wifi but unable to surf the internet ubuntu 14.04 broadcom driver"
date: 2014-08-17
forum: Networking &amp; Wireless
---

### Post by grifon31 on 2014-08-17
Hi,I have installed Ubuntu 14.04.01 today on laptop Lenovo ThinkPad-edge-S430. I'm able to connect to wifi but unable to surf the internet.

iwconfig returns:

```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Torn@do"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 5E:E0:E7:2F:B7:45  
          Tx-Power=19 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```



ifconfig returns

```

eth0      Link encap:Ethernet  HWaddr b8:88:e3:35:a5:b2  
          inet addr:172.30.106.107  Bcast:172.30.107.255  Mask:255.255.252.0
          inet6 addr: fe80::ba88:e3ff:fe35:a5b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102092 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:82875027 (82.8 MB)  TX bytes:6415100 (6.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1105672 (1.1 MB)  TX bytes:1105672 (1.1 MB)

wlan0     Link encap:Ethernet  HWaddr 08:ed:b9:e5:95:f5  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::aed:b9ff:fee5:95f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:62814 (62.8 KB)


```

i have tried this solution:

```


sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
  sudo apt-get install b43-fwcutter firmware-b43-installer


echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf

echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf


```


this one:

```


sudo modprobe -rv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -v brcmsmac



```

```

$ sudo apt-get remove --purge bcmwl-kernel-source

$ sudo apt-get install linux-firmware-nonfree

$ sudo modprobe b43

$ sudo su
cho "b43" >> /etc/modules


```



also i have downloaded drivers from here [http://wireless.kernel.org/](http://wireless.kernel.org/)

Also have tried solutions from here: [https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29](https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29)

Driver details: 
BCM4313 802.11b/g/n/ 

Broadcom 802.11  Linux STA wireless driver source from bcmwl-kernel-source 

but nothing works. Any solution ?

---

### Post by jeremy31 on 2014-08-17
run the wireless script that is linked to from this post

[http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222](http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222)

Have you tried what is recommended here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by grifon31 on 2014-08-17
> Have you tried what is recommended here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)    I have already tried this solution-it didn't help me also.
Sript result is in an attaachment

---

### Post by grifon31 on 2014-08-17
Now i have detected in wireless menu of top bar of unity next message: device not ready (firmware missing) I'm not sure after what step this one appears. 
But in this post were written to undo everything i have done earlier > [tp://ubuntuforums.org/showthread.php?t=2214110]("http://ubuntuforums.org/showthread.php?t=2214110")

Maybe after this instructions

---

### Post by jeremy31 on 2014-08-17
Have you rebooted since following those instructions?  I see b43 and ssb in the blacklist.conf file but they are still listed in the module list

---

### Post by varunendra on 2014-08-17
> **jeremy31 said:**
> I see b43 and ssb in the blacklist.conf file but they are still listed in the module list

Because 'b43' is also in the /etc/modules. It seems the OP has implemented ALL the solutions EVER created for broadcom cards :p

And I am having difficulty in imagining which of the solutions recommended to purge/remove the default "linux-firmware" package, as is evident from these messages -
```
dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
....
[   21.563616] ieee80211 phy0: brcmsmac: fail to load firmware brcm/bcm43xx-0.fw
....
[   21.565815] r8169 0000:04:00.0 eth0: unable to load firmware patch rtl_nic/rtl8168e-3.fw (-2)
```
Both of the above are part of the "linux-firmware" package.

I suggest the following -

1) Remove "b43" from /etc/modules -
```
sudo sed -i '/b43/ d' /etc/modules
```

2) Install (reinstall actually) "linux-firmware" package -
```
sudo apt-get install --reinstall linux-firmware
```
Reboot and report back.

If you don't have a working internet connection on the system, manually download the "linux-firmware" package from here : [http://packages.ubuntu.com/trusty/all/linux-firmware/download](http://packages.ubuntu.com/trusty/all/linux-firmware/download)
(direct download link : [http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.127.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.127.4_all.deb) )

Then copy the downloaded .deb package onto your desktop, and install with -
```
sudo dpkg -i Desktop/linux-firmware*.deb
```

---

### Post by grifon31 on 2014-08-17
I have removed b43 from /etc/modules and reinstalled linux-firmware as you suggested before than rebooted my lap-top. Now It is connected to Wi-Fi again, but nevertheless I'm not able to neihter  surf internet,nor ping external sites

---

### Post by grifon31 on 2014-08-17
And it is strange, cause other devices work good

---

### Post by varunendra on 2014-08-17
Okay, then now is the time to run the script again and post back a fresh report for us.

---

### Post by grifon31 on 2014-08-18
Ok,thank you for your help. Here is an updated sysInfo file.

---

### Post by Hadaka on 2014-08-18
Hi you still have a couple modules that need to be blacklisted.
please do.
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit 0
```
boot
then do and post
```
cat /etc/modules
grep -i 'blacklist' /etc/modprobe.d/blacklist.conf
```
and once again run the wireless script
thanks.

---

### Post by grifon31 on 2014-08-18
thank you all. Here is file with last updates

---

### Post by jeremy31 on 2014-08-18
It looks like you are using hotspot mode

---

### Post by grifon31 on 2014-08-18
> **jeremy31 said:**
> It looks like you are using hotspot mode.  Hmmm..., actually  I don't see such configs in UI settings of connection. Do you have an idea how to change this connection mode via terminal ?
Cause in UI this connection is displayed unusual . I can't share picture,cause now I'm from cell phone

---

### Post by varunendra on 2014-08-18
> **grifon31 said:**
> .  Hmmm..., actually  I don't see such configs in UI settings of connection.

In Network Manager (nm-applet) menu > "Edit Connections.." > "Wireless" tab > double-click your connection (Torn@do) to edit it > "IPv6 Settings" tab > select "Method" as "**Auto (DHCP)**" (if you have DHCP enabled in the router) or "Manual" (in which you will have to manually assign IP, Subnet, Gateway and DNS).

Currently, it is set to "**[COLOR="#FF0000"]Shared to other computers[/COLOR]**", which is used only when you have internet access via any other interface (Ethernet, USB modem etc.) and you want to share it with the other interface (in this case - your wifi).

---

### Post by Hadaka on 2014-08-19
Please set your connection  to look like the attached.

[ATTACH=CONFIG]255626[/ATTACH][ATTACH=CONFIG]255627[/ATTACH][ATTACH=CONFIG]255628[/ATTACH]

---

### Post by grifon31 on 2014-08-19
Hi,I have done as you described in previous instructions.But now connection is to slow .I have tested it on two independent wifi networks. 
Even after instructions provided on screenshots. In the attachment wireless info file of my home network connection. 
.

---

### Post by grifon31 on 2014-08-19
But few seconds later i have changed settings as described in screenshot,connection become fast. I made them to my work network connection. Is this effect of last instructions ?

---

### Post by Hadaka on 2014-08-19
yes, following the screenshots released it from ad-hock  mode
after you booted. It should be working fine now. before you mark
this solved, please run and post the wireless script one more time
so we can verifiy your settings are now correct.
thanks

---

### Post by grifon31 on 2014-08-19
Ok,i will add it from home. And will summarize steps before closing the issue in case if somebody will be faced with the same issue. Thank you :)

---

### Post by grifon31 on 2014-08-19
Bad news. When i was at office approximately 30 minutes connection was good,but after that connection become very very slow. When I have returned at home to test my domestic connection, it was very slow again. Here you can find my wireless info file with latest updates.

---

### Post by Hadaka on 2014-08-19
Hi, this.........
Gateway:         10.0.1.1
Tells me you changed something and it is now back in the "shared" connection
or you are using this as a hot spot.
what do you enter into your browser to log into your router
192.168.1.1 or 192.168.0.1 ???/

---

### Post by grifon31 on 2014-08-19
Acctualy, I'm using Apple router and there is special application to log in into router. And I don't know router's IP address

---

### Post by Hadaka on 2014-08-19
hi, review the screen shots i sent you, verify your settings are the same.
this Apple router thing or whatever it is has to have an IP address and
that address is what your GATEWAY ip address should be. your current
Gateway:  10.0.1.1 is for adhoc network where you use the computer as
a router. without knowing exactly what you are attached to and you not
knowing what the ip address of the router is, there is nothing more i can
do to help you.

&#2357;&#2352;&#2369;&#2339; &#2325;&#2368; &#2350;&#2352;&#2350;&#2381;&#2350;&#2340; &#2325;&#2371;&#2346;&#2351;&#2366;

---

### Post by grifon31 on 2014-08-19
Yes. I have talked with other tech.  person. IP address of router is 10.0.1.1 . And I  have been faced with the same issue at office after 30 or less minutes of normal connection speed , nevertheless I have applied settings from screenshots. Could it be hardware problem?

---

### Post by varunendra on 2014-08-19
> **Hadaka said:**
> &#2357;&#2352;&#2369;&#2339; &#2325;&#2368; &#2350;&#2352;&#2350;&#2381;&#2350;&#2340; &#2325;&#2371;&#2346;&#2351;&#2366;
Err.. that stupid google translate :/ (the above kinda means "fix varun please"). I'm sure this thread is not about fixing me :p

Anyway, I don't see either what else can be done to improve things :(

I'm a little concerned about that last line in dmesg -
```
[   21.572685] brcmsmac bcma0:0: brcms_ops_bss_info_changed: **arp filtering: 1 addresses (implement)**
```
..but not sure if it really means something bad or not, or what can be done about it, if is indeed indication of something wrong.

---

### Post by bclee on 2014-08-19
It looks like you are using same hardware as mine.(Lenovo S430 with BCM4313)

Sadly, my wireless adaptor are not working too ( [http://ubuntuforums.org/showthread.php?t=2240008](http://ubuntuforums.org/showthread.php?t=2240008) ). It is interesting that solutions in each post's reply are not same. I'll try your configuration and post it whether it wotks or not.

---

### Post by grifon31 on 2014-08-20
On Ubuntu 13.10 somehow I managed configured it and everything worked good. But I don't remember how I did it

---

### Post by bclee on 2014-08-20
I think we need to compare each settings since we are using same hardwardware.

It is generated the result by using latest wireless script. My wireless card is not connected to the AP, but the bluetooth module integrated in BCM4313 works perfectly. (So It can be teathered by my smartphone.)
```


########## wireless info START ##########

Report from: 20 Aug 2014 16:54 KST +0900

Script from: 17 Aug 2014 02:46 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0608]
    Kernel driver in use: bcma-pci-bridge

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:21fc]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 003: ID 5986:02d2 Acer, Inc 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 147e:1002 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 004: ID 0a5c:21f4 Broadcom Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              630653  1 brcmsmac
cfg80211              484040  2 brcmsmac,mac80211
bcma                   52096  2 brcmsmac
wmi                    19177  0 

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

bnep0     Link encap:Ethernet  HWaddr <MAC addr bnep0>  
          inet addr:192.168.44.178  Bcast:192.168.44.255  Mask:255.255.255.0
          inet6 addr: fe80::aed:b9ff:fee2:cdb8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:563 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:121172 (121.1 KB)  TX bytes:66123 (66.1 KB)

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

bnep0     no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.44.1    0.0.0.0         UG    0      0        0 bnep0
0.0.0.0         192.168.44.1    0.0.0.0         UG    100    0        0 bnep0
192.168.44.0    0.0.0.0         255.255.255.0   U     11     0        0 bnep0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: <MAC address>  [Nexus 5 Network] ---------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         192.168.44.178
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.44.1

    DNS:             192.168.44.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ollehEgg_000:    Infra, <MAC addr ollehEgg_000>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA
    301:             Infra, <MAC addr 301>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2

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

country KR:
    (2402 - 2482 @ 20), (N/A, 20)
    (5170 - 5250 @ 20), (3, 20)
    (5250 - 5330 @ 20), (3, 20), DFS
    (5490 - 5630 @ 20), (3, 30), DFS
    (5735 - 5815 @ 20), (3, 30)

##### iwlist channels #####

bnep0     no frequency information.

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz

##### iwlist scan #####

Channel occupancy:

     1   WLAPs on   Frequency:2.462 GHz (Channel 11)

bnep0     Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"iptime"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d9ea9817e
                    Extra: Last beacon: 224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos #####

[brcmsmac]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     43D6897F7EB716081DF69BE
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

[bcma]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

##### module parameters #####

##### /etc/modules #####

lp
rtc

##### blacklists #####

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
blacklist b43
blacklist ssb

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    3.697425] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[    3.697451] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[    3.697472] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[    3.697514] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[    3.712088] bcma: bus0: Bus registered
[    3.899450] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[    3.912476] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[    4.093293] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[    4.093299] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[    4.093916] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[    8.828596] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[  156.899925] wlan0: authenticate with <MAC addr 301>
[  156.903530] wlan0: direct probe to <MAC addr 301> (try 1/3)
[  157.104404] wlan0: direct probe to <MAC addr 301> (try 2/3)
[  157.308459] wlan0: direct probe to <MAC addr 301> (try 3/3)
[  157.512508] wlan0: authentication with <MAC addr 301> timed out
[  181.819810] wlan0: authenticate with <MAC addr 301>
[  181.822860] wlan0: direct probe to <MAC addr 301> (try 1/3)
[  182.023049] wlan0: direct probe to <MAC addr 301> (try 2/3)
[  182.051954] wlan0: deauthenticating from <MAC addr 301> by local choice (reason=3)
[  185.076023] wlan0: authenticate with <MAC addr 301>
[  185.076132] wlan0: direct probe to <MAC addr 301> (try 1/3)
[  185.279944] wlan0: direct probe to <MAC addr 301> (try 2/3)
[  185.483947] wlan0: direct probe to <MAC addr 301> (try 3/3)
[  185.688027] wlan0: authentication with <MAC addr 301> timed out
[  259.488279] wlan0: authenticate with <MAC addr 301>
[  259.493023] wlan0: direct probe to <MAC addr 301> (try 1/3)
[  259.696079] wlan0: direct probe to <MAC addr 301> (try 2/3)
[  259.900234] wlan0: direct probe to <MAC addr 301> (try 3/3)
[  260.104394] wlan0: authentication with <MAC addr 301> timed out
[  261.958260] wlan0: authenticate with <MAC addr 301>
[  261.963070] wlan0: direct probe to <MAC addr 301> (try 1/3)
[  262.166020] wlan0: direct probe to <MAC addr 301> (try 2/3)
[  262.370138] wlan0: direct probe to <MAC addr 301> (try 3/3)
[  262.574328] wlan0: authentication with <MAC addr 301> timed out
[  618.604117] wlan0: authenticate with <MAC addr 301>
[  618.607021] wlan0: direct probe to <MAC addr 301> (try 1/3)
[  618.807375] wlan0: direct probe to <MAC addr 301> (try 2/3)
[  619.011529] wlan0: direct probe to <MAC addr 301> (try 3/3)
[  619.215683] wlan0: authentication with <MAC addr 301> timed out
[  623.247396] wlan0: authenticate with <MAC addr 301>
[  623.250516] wlan0: direct probe to <MAC addr 301> (try 1/3)
[  623.451038] wlan0: direct probe to <MAC addr 301> (try 2/3)
[  623.655110] wlan0: direct probe to <MAC addr 301> (try 3/3)
[  623.859251] wlan0: authentication with <MAC addr 301> timed out
[  640.564839] wlan0: authenticate with <MAC addr 301>
[  640.569795] wlan0: direct probe to <MAC addr 301> (try 1/3)
[  640.772278] wlan0: direct probe to <MAC addr 301> (try 2/3)
[  640.976416] wlan0: direct probe to <MAC addr 301> (try 3/3)
[  641.180570] wlan0: authentication with <MAC addr 301> timed out
[  650.444477] wlan0: authenticate with <MAC addr 301>
[  650.444586] wlan0: direct probe to <MAC addr 301> (try 1/3)
[  650.647875] wlan0: direct probe to <MAC addr 301> (try 2/3)
[  650.851962] wlan0: direct probe to <MAC addr 301> (try 3/3)
[  651.056140] wlan0: authentication with <MAC addr 301> timed out
[  673.602225] wlan0: authenticate with <MAC addr 301>
[  673.605702] wlan0: direct probe to <MAC addr 301> (try 1/3)
[  673.809558] wlan0: direct probe to <MAC addr 301> (try 2/3)
[  674.013715] wlan0: direct probe to <MAC addr 301> (try 3/3)
[  674.217901] wlan0: authentication with <MAC addr 301> timed out
[  834.646791] usb 1-1.3: Direct firmware load failed with error -2
[  834.650299] Bluetooth: can't load firmware, may not work correctly
[  982.346960] wlan0: authenticate with <MAC addr 301>
[  982.349837] wlan0: direct probe to <MAC addr 301> (try 1/3)
[  982.550215] wlan0: direct probe to <MAC addr 301> (try 2/3)
[  982.754270] wlan0: direct probe to <MAC addr 301> (try 3/3)
[  982.958322] wlan0: authentication with <MAC addr 301> timed out
[ 1003.671547] wlan0: authenticate with <MAC addr 301>
[ 1003.671659] wlan0: direct probe to <MAC addr 301> (try 1/3)
[ 1003.871919] wlan0: direct probe to <MAC addr 301> (try 2/3)
[ 1004.075957] wlan0: direct probe to <MAC addr 301> (try 3/3)
[ 1004.280011] wlan0: authentication with <MAC addr 301> timed out
[ 1026.818952] wlan0: authenticate with <MAC addr 301>
[ 1026.821874] wlan0: direct probe to <MAC addr 301> (try 1/3)
[ 1027.022074] wlan0: direct probe to <MAC addr 301> (try 2/3)
[ 1027.226123] wlan0: direct probe to <MAC addr 301> (try 3/3)
[ 1027.430162] wlan0: authentication with <MAC addr 301> timed out
[ 1032.512012] wlan0: authenticate with <MAC addr 301>
[ 1032.515137] wlan0: direct probe to <MAC addr 301> (try 1/3)
[ 1032.715597] wlan0: direct probe to <MAC addr 301> (try 2/3)
[ 1032.919649] wlan0: direct probe to <MAC addr 301> (try 3/3)
[ 1033.123703] wlan0: authentication with <MAC addr 301> timed out
[ 1066.357128] wlan0: authenticate with <MAC addr 301>
[ 1066.360482] wlan0: direct probe to <MAC addr 301> (try 1/3)
[ 1066.564624] wlan0: direct probe to <MAC addr 301> (try 2/3)
[ 1066.768653] wlan0: direct probe to <MAC addr 301> (try 3/3)
[ 1066.972731] wlan0: authentication with <MAC addr 301> timed out
########## wireless info END ############

```

---

### Post by grifon31 on 2014-08-31
Hi, sorry for so late answer. I have small update. Firts of all I have installed kernel 3.14.17.  [http://linuxg.net/how-to-install-kernel-3-14-17-on-ubuntu-14-04-linux-mint-17-elementary-os-0-3-pinguy-os-14-04-and-other-ubuntu-14-04-derivative-systems/](http://linuxg.net/how-to-install-kernel-3-14-17-on-ubuntu-14-04-linux-mint-17-elementary-os-0-3-pinguy-os-14-04-and-other-ubuntu-14-04-derivative-systems/)    After installation of this kernel my ubuntu has begun to see all neigbours networks except my one. So i have changed wi-fi channel on my router. And my lap-top has begun to see my network also,but can't connect to it. After this i perform next command 

```
 sudo ubuntu-drivers autoinstall
```

and it installed bcmwl-kernel-source and wl drivers-nothing changed

after that i have uninstalled bcmwl-kernel-source and my lap-top has connected to wi-fi. Even after reboot everyting worked fine,but when i put laptop a sleep- wifi connection was dropped. And even after reboot it doesn't restored.

So i tried commands 

```
s[COLOR=#000000][FONT=Ubuntu Mono]udo modprobe -r brcmsmac
[/FONT][/COLOR]sudo modprobe brcmsmac
```

taken from this post :
[http://ubuntuforums.org/showthread.php?t=2220443](http://ubuntuforums.org/showthread.php?t=2220443)

but they don't help me.

It makes me crazy.

In attathment in the archive called 1 you can find my info with bcmwl-kernel-source driver,and in archive called 2 you can my wireless info without this driver

P.S: When i have made archive called i have forgotton to unplug cable. But i have tested this connection without cable also- and without cable it worked fine

---

### Post by grifon31 on 2014-09-01
Litle update.Since my last post i shutdowned my lap-top approximately for 3 hours. But when i turned it on again after 3 hours,my lap-top wasn't able to connect wifi. And here is wirless-file (3 hours later)

---

### Post by varunendra on 2014-09-01
One of the rather unusual thing I noticed in the last three reports is that in the first two your regdomain code was set to 'US', while in the last one it is defaulted to '00'. Did you change it manually using some (probably 'iw reg set') command?

As far as I know, the regdomain code can be set by one of the four things -
1) by the setting saved in the EEPROM chip of the wireless card itself, or..
2) by the router if it could negotiate with the card successfully, or..
3) by using the "ieee80211_regdom" parameter of the 'cfg80211' driver to (manually) force a setting, or..
4) by using either the 'iw reg set' command or '/etc/default/crda' file to force a desired code.

Now I wonder which of these is/was the cause of changing regdomain code in your reports? The code 'US' is for USA, while your regional language setting suggests you are probably in Ukraine? What is the regional setting of your router?

Assuming the region in the router is set to 'US' (please confirm if it shows the region code/name), because you were able to connect and browse with 'US' regdomain code (2.zip report), I suggest you try the following -

**1)** Explicitly set the Regulatory Domain code 'US' on Ubuntu -
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
sudo iw reg set US
```

**2)** Fix the channel in your router to 1 or 11. Currently it is set to either 'auto' or to channel 2. Usually, 1 and 11 offer better signal quality if they are not already too crowded by neighbouring signals.

---

### Post by grifon31 on 2014-09-10
Actually you help didn't help and I gave up.I have installed harware : Intel Wi-Fi Bluetooth Module

---

### Post by varunendra on 2014-09-10
> **grifon31 said:**
> Actually you help didn't help and I gave up.I have installed harware : Intel Wi-Fi Bluetooth Module

Quite understandable. Hope the new card serves you better.

---

### Post by grifon31 on 2014-09-12
Yes,much more better.Thany you all for help

---

### Post by sheldon-corey on 2014-09-12
have you investigated your /etc/resolv.conf file ??   try these pls:


cat /etc/resolv.conf


DO YOU SEE your localhost in that list



also try from some live media to connect to some website:   if this works   run the following:


sudo mount /dev/sdX (whatever / is)  /mnt
sudo mount --bind /dev /mnt/dev 
sudo mount --bind /dev/pts /mnt/dev/pts
cp /etc/resolv.conf /mnt/etc/resolv.conf 



then either reboot and retry OR prior to that run sudo chroot /mnt  && cat /etc/resolv.conf and confirm valid values in that file then type "exit" twice and reboot and advise back here

---

