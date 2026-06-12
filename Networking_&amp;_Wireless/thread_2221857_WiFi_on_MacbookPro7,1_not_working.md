---
title: "WiFi on MacbookPro7,1 not working"
date: 2014-05-04
forum: Networking &amp; Wireless
---

### Post by waulok2 on 2014-05-04
Howdy!

I've spent the last two days trying to get this working so thought I'd give it a shot here.
Drivers I've tested: wl, b43, sta. I've installed and used b43-fwcutter and the Broadcomm driver from their site.
Possibly others. It's on Ubuntu 12.10

Troubleshooting:

```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)        Subsystem: Apple Inc. Device [106b:008d]
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d3200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information: Len=78 <?>
        Capabilities: [e8] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel
        Capabilities: [160] Device Serial Number 4e-1e-5e-ff-ff-8c-d8-a2
        Capabilities: [16c] Power Budgeting <?>
        Kernel driver in use: wl
        Kernel modules: wl, ssb


03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
        Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at d3100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [48] Power Management version 3
        Capabilities: [40] Vital Product Data
        Capabilities: [60] Vendor Specific Information: Len=6c <?>
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [cc] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel
        Capabilities: [160] Device Serial Number 58-b0-35-ff-fe-fa-fa-2e
        Capabilities: [16c] Power Budgeting <?>
        Kernel driver in use: tg3
        Kernel modules: tg3

```

```
 lshw -C network
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: d8:a2:5e:8c:4e:1e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.112 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:21 memory:d3200000-d3203fff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 58:b0:35:fa:fa:2e
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=5764m-v3.38 ip=192.168.137.2 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:45 memory:d3100000-d310ffff

```

```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 58:b0:35:fa:fa:2e
          inet addr:192.168.137.2  Bcast:192.168.137.255  Mask:255.255.255.0
          inet6 addr: fe80::5ab0:35ff:fefa:fa2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1053 errors:0 dropped:0 overruns:0 frame:0
          TX packets:706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:865445 (865.4 KB)  TX bytes:88153 (88.1 KB)
          Interrupt:23


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5796 (5.7 KB)  TX bytes:5796 (5.7 KB)


wlan0     Link encap:Ethernet  HWaddr d8:a2:5e:8c:4e:1e
          inet6 addr: fe80::daa2:5eff:fe8c:4e1e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:1384
          TX packets:0 errors:46 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21

```

```
 uname -r
3.5.0-49-generic

```

```
 iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:144 Mb/s   Tx-Power:24 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

At various times, I've had it scanning and finding networks but not logging on. At the moment it gives:

```
 iwlist scan
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Failed to read scan data : Invalid argument

```

```
 lspci | grep Network
02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```

```
 lsmod | grep wl
wl                   2573608  0
lib80211               14382  2 lib80211_crypt_tkip,wl

```

I've had various configurations here but have removed them:
```
 cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

I tried wpa_supplicant, too:
```
 # cat /etc/wpa_supplicant/wpa_supplicant.conf
# reading passphrase from stdin
network={
        ssid="EvilHouse"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="thepasswordforourplace"
        #psk=53849584095840985409809458094
        pairwise=CCMP
        group=TKIP
}

```

With different options for pairwise and group.

```
# dmesg | grep wl
[   12.221782] wl: module license 'MIXED/Proprietary' taints kernel.
# dmesg | grep oadcom
[   12.494838] eth1: Broadcom BCM432b 802.11 Hybrid Wireless Controller 5.100.82.112

```

```
 ifup wlan0
Ignoring unknown interface wlan0=wlan0.
```

```
# rfkill list all0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: brcmwl-0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

Thanks in advance! :)

---

### Post by varunendra on 2014-05-04
Have you tried the native "b43" alone? If not, or not sure, please try (while being connected to internet via Ethernet) -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```
..then reboot and try to scan/connect to available networks. Any better or worse?

Oh, and Welcome to the forums! :)

---

### Post by waulok2 on 2014-05-04
Thank you! I must have been here before years ago as this username it gave me is waulok2 lol. Oh well. Could not figure what email address I used years ago XD

```

root@MacBuntu:~# apt-get purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms fakeroot
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 157528 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-49-generic
root@MacBuntu:~# apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-firmware-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  dkms fakeroot
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```

root@MacBuntu:~# ifup wlan0
Ignoring unknown interface wlan0=wlan0.

```

---

### Post by waulok2 on 2014-05-04
[COLOR=#000000]Added to /etc/network/interfaces:
[/COLOR][COLOR=#000000]```

auto wlan0
iface wlan0 inet dhcp
```[/COLOR]
[COLOR=#000000]

Now I have: 
[/COLOR]```
root@MacBuntu:~# ifdown wlan0
RTNETLINK answers: No such process
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Listening on LPF/wlan0/d8:a2:5e:8c:4e:1e
Sending on   LPF/wlan0/d8:a2:5e:8c:4e:1e
Sending on   Socket/fallback
root@MacBuntu:~# ifup wlan0
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Listening on LPF/wlan0/d8:a2:5e:8c:4e:1e
Sending on   LPF/wlan0/d8:a2:5e:8c:4e:1e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21

```

---

### Post by waulok2 on 2014-05-04
Some more mucking around got this, but no IP yet:

```

wlan0     Scan completed :
          Cell 01 - Address: 00:04:ED:73:DB:21
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=67/70  Signal level=-43 dBm
                    Encryption key:on
                    ESSID:"EvilHouse"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f69b6ee152
                    Extra: Last beacon: 1152ms ago
                    IE: Unknown: 00094576696C486F757365
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05060055127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706415520010E10

```
That's our SSID.

---

### Post by varunendra on 2014-05-04
Can you try manual IP assignment in Network Manager?

And WPA+CCMP is a non-standard combination. WPA encryption essentially requires TKIP, which we usually recommend to avoid due to being an inefficient algorithm. I'd recommend to change the encryption type in the router to WPA2 with AES (CCMP). Remember - pure WPA2, not WPA/WPA2 mixed mode! Reboot the router after saving the change.

I'm assuming you are trying this all with Network Manager (recommended), not with WPA supplicant.

---

### Post by waulok2 on 2014-05-04
Ah okay.
I'm trying to do all this on the commandline as the GUI is very unstable and locks up for no reason after about 10 minutes.
I have tried TKIP but that didn't work so tried CCMP as that's what was returned in a scan as supported.
Unfortunately I can't change the router as there's 2 other people with many devices already configured living in this house.
The scan reported supporting AES but I'm not sure how to configure that here. Can I set my wpa_supplicant to CCMP + WPA2 somehow?

---

### Post by bapoumba on 2014-05-04
> **waulok2 said:**
> Thank you! I must have been here before years ago as this username it gave me is waulok2 lol. Oh well. Could not figure what email address I used years ago XD
If you want to get it back, you can start a thread in the Resolution Center and have an admin help you with that. At least you need to remember your previous username.
[http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

---

### Post by waulok2 on 2014-05-04
> **bapoumba said:**
> If you want to get it back, you can start a thread in the Resolution Center and have an admin help you with that. At least you need to remember your previous username.
[http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

Thanks! Done! :)

---

### Post by varunendra on 2014-05-04
> **waulok2 said:**
> Can I set my wpa_supplicant to CCMP + WPA2 somehow?

Nope, that is something to be done in the router only. The settings in your configuration files in Ubuntu must mimic the settings on the router.

While such non-standard combinations work for most people, they certainly add complexity to a problem, if not a problem themselves. And the "b43" driver we are currently testing does not support your card very well. So.. if it turns out to be a no go, we may try reverting back to the STA driver again, although this is probably just a different way to say - "I give up" :|

By the way, you can try temporarily assigning an IP address with following commands -
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 **192.168.137.[COLOR="#FF0000"]200[/COLOR]**
```
where the **192.168.137.[COLOR="#FF0000"]200[/COLOR]** is just an example IP address. Replace it with whatever IP is available and not already in use on your network. An IP address assigned this way is temporary and is lost on next boot (or after the next interface down/up cycle).

---

### Post by waulok2 on 2014-05-04
Thanks.
Actually, 192.168.137.* is my desktop PC sharing out my internet access. The home router is a 10.1.1.* network.
As the router is downstairs and my desktop gets WiFi, I'm using Windows 8.1 Internet Connection Sharing to share access to the internet via eth0 just for installing and updating packages.
I did set a static ip temporarily and unplug eth0, but could not ping anything on the home network or outside it.

---

### Post by waulok2 on 2014-05-05
Well, I decided to try something else. I downloaded and installed the latest version of Debian and the WiFi worked perfectly once I installed b43-cutter firmware. So, I'm not sure what is wrong with Ubuntu. 
The fact that the Ubuntu website says the latest version definitely does not work with my MacBook at all concerns me somewhat. But, I'm glad I got a nice Linux distribution to work on it anyway.

Thanks for all the help!

---

### Post by varunendra on 2014-05-05
Maybe it was the latest firmware that did the magic? I would have recommended to try the latest LTS (14.04) in live mode, installing the "linux-firmware-nonfree" package on it to get the latest firmware, but if the 'Ubuntu website' itself says it is not going to work with your macbook, I don't know if that would be a good suggestion.

Maybe if you have extra time to kill, and extra bandwidth to waste, try it (Ubuntu 14.04 Live DVD/USB) despite what the website says? ;)

Anyway, glad you got it working on Linux and are satisfied with it. It doesn't necessarily have to be Ubuntu, although it would have made me happier. :)

---

