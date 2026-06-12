---
title: "CTRL-EVENT-DISCONNECTED reason=0 with a BCM4331 WIFI card"
date: 2015-04-18
forum: Networking &amp; Wireless
---

### Post by jeff-artik on 2015-04-18
I'm using the default bcmwl-kernel-source version 6.30.223.248 and I have strange disconnexions every 1/2 days. I trace the log with a disconnexion at 15:33 :

```
Apr 10 14:53:47 artik-iMac wpa_supplicant[1038]: wlan0: CTRL-EVENT-SCAN-STARTED Apr 10 15:09:01 artik-iMac CRON[27926]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Apr 10 15:17:01 artik-iMac CRON[28158]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 10 15:33:47 artik-iMac wpa_supplicant[1038]: message repeated 20 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 10 15:33:58 artik-iMac wpa_supplicant[1038]: wlan0: CTRL-EVENT-DISCONNECTED bssid=80:ea:96:ec:59:09 reason=0
Apr 10 15:33:58 artik-iMac kernel: [156254.032112] cfg80211: Calling CRDA for country: FR
Apr 10 15:33:58 artik-iMac NetworkManager[939]: <info> (wlan0): roamed from BSSID 80:EA:96:EC:59:09 (BBM Air 5) to (none) ((none))
Apr 10 15:33:58 artik-iMac NetworkManager[939]: <info> (wlan0): supplicant interface state: completed -> disconnected
Apr 10 15:33:58 artik-iMac wpa_supplicant[1038]: wlan0: Reject scan trigger since one is already pending
Apr 10 15:33:58 artik-iMac wpa_supplicant[1038]: wlan0: Failed to initiate AP scan
Apr 10 15:33:59 artik-iMac wpa_supplicant[1038]: wlan0: Reject scan trigger since one is already pending
Apr 10 15:33:59 artik-iMac wpa_supplicant[1038]: wlan0: Failed to initiate AP scan
Apr 10 15:34:00 artik-iMac wpa_supplicant[1038]: wlan0: Reject scan trigger since one is already pending
Apr 10 15:34:00 artik-iMac wpa_supplicant[1038]: wlan0: Failed to initiate AP scan
Apr 10 15:34:01 artik-iMac wpa_supplicant[1038]: wlan0: Reject scan trigger since one is already pending
Apr 10 15:34:01 artik-iMac wpa_supplicant[1038]: wlan0: Failed to initiate AP scan
Apr 10 15:34:02 artik-iMac wpa_supplicant[1038]: wlan0: Reject scan trigger since one is already pending
Apr 10 15:34:02 artik-iMac wpa_supplicant[1038]: wlan0: Failed to initiate AP scan
Apr 10 15:34:03 artik-iMac wpa_supplicant[1038]: wlan0: Reject scan trigger since one is already pending
Apr 10 15:34:03 artik-iMac wpa_supplicant[1038]: wlan0: Failed to initiate AP scan
Apr 10 15:34:04 artik-iMac wpa_supplicant[1038]: wlan0: Reject scan trigger since one is already pending
Apr 10 15:34:04 artik-iMac wpa_supplicant[1038]: wlan0: Failed to initiate AP scan
Apr 10 15:34:05 artik-iMac wpa_supplicant[1038]: wlan0: Reject scan trigger since one is already pending
Apr 10 15:34:05 artik-iMac wpa_supplicant[1038]: wlan0: Failed to initiate AP scan
Apr 10 15:34:05 artik-iMac wpa_supplicant[1038]: wlan0: Trying to associate with 80:ea:96:ec:59:09 (SSID='BBM Air 5' freq=5180 MHz)
Apr 10 15:34:05 artik-iMac NetworkManager[939]: <info> (wlan0): supplicant interface state: disconnected -> associating
Apr 10 15:34:06 artik-iMac wpa_supplicant[1038]: wlan0: CTRL-EVENT-ASSOC-REJECT bssid=80:ea:96:ec:59:09 status_code=16
Apr 10 15:34:06 artik-iMac NetworkManager[939]: <info> (wlan0): supplicant interface state: associating -> disconnected
Apr 10 15:34:06 artik-iMac wpa_supplicant[1038]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 10 15:34:06 artik-iMac NetworkManager[939]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 10 15:34:13 artik-iMac NetworkManager[939]: <warn> (wlan0): link timed out.
Apr 10 15:34:13 artik-iMac NetworkManager[939]: <info> (wlan0): device state change: activated -> failed (reason 'supplicant-timeout') [100 120 11]
Apr 10 15:34:13 artik-iMac NetworkManager[939]: <info> NetworkManager state is now DISCONNECTED
Apr 10 15:34:13 artik-iMac NetworkManager[939]: <warn> Activation (wlan0) failed for connection 'Auto BBM Air 5'
Apr 10 15:34:13 artik-iMac dbus[498]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 10 15:34:13 artik-iMac NetworkManager[939]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 10 15:34:13 artik-iMac NetworkManager[939]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 10 15:34:13 artik-iMac dbus[498]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 10 15:34:14 artik-iMac NetworkManager[939]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2632
Apr 10 15:34:14 artik-iMac NetworkManager[939]: <warn> DNS: plugin dnsmasq update failed
Apr 10 15:34:14 artik-iMac NetworkManager[939]: <info> Removing DNS information from /sbin/resolvconf
Apr 10 15:34:14 artik-iMac dnsmasq[2635]: configuration des serveurs amonts à partir de DBus
Apr 10 15:34:14 artik-iMac wpa_supplicant[1038]: wlan0: Reject scan trigger since one is already pending
Apr 10 15:34:14 artik-iMac NetworkManager[939]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Auto-activating connection 'Auto BBM Air 5'.
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0) starting connection 'Auto BBM Air 5'
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> NetworkManager state is now CONNECTING
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0/wireless): access point 'Auto BBM Air 5' has security, but secrets are required.
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0/wireless): connection 'Auto BBM Air 5' has security, and secrets exist.  No new secrets needed.
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Config: added 'ssid' value 'BBM Air 5'
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Config: added 'scan_ssid' value '1'
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Config: added 'auth_alg' value 'OPEN'
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Config: added 'psk' value '<omitted>'
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> Config: set interface ap_scan to 1
Apr 10 15:34:16 artik-iMac wpa_supplicant[1038]: wlan0: Trying to associate with 80:ea:96:ec:59:09 (SSID='BBM Air 5' freq=5180 MHz)
Apr 10 15:34:16 artik-iMac NetworkManager[939]: <info> (wlan0): supplicant interface state: scanning -> associating
Apr 10 15:34:17 artik-iMac wpa_supplicant[1038]: wlan0: CTRL-EVENT-ASSOC-REJECT bssid=80:ea:96:ec:59:09 status_code=16
Apr 10 15:34:17 artik-iMac NetworkManager[939]: <info> (wlan0): supplicant interface state: associating -> disconnected
Apr 10 15:34:18 artik-iMac wpa_supplicant[1038]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 10 15:34:18 artik-iMac NetworkManager[939]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 10 15:34:28 artik-iMac wpa_supplicant[1038]: wlan0: Trying to associate with 80:ea:96:ec:59:09 (SSID='BBM Air 5' freq=5180 MHz)
Apr 10 15:34:28 artik-iMac NetworkManager[939]: <info> (wlan0): supplicant interface state: scanning -> associating
Apr 10 15:34:28 artik-iMac wpa_supplicant[1038]: wlan0: CTRL-EVENT-ASSOC-REJECT bssid=80:ea:96:ec:59:09 status_code=16
Apr 10 15:34:28 artik-iMac wpa_supplicant[1038]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="BBM Air 5" auth_failures=1 duration=10
Apr 10 15:34:28 artik-iMac NetworkManager[939]: <info> (wlan0): supplicant interface state: associating -> disconnected
Apr 10 15:34:33 artik-iMac wpa_supplicant[1038]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 10 15:34:33 artik-iMac NetworkManager[939]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 10 15:34:41 artik-iMac NetworkManager[939]: <warn> Activation (wlan0/wireless): association took too long.

```

I tried b43 and b43legacy drivers. Both show me wifi network, but impossible to connect, so back to bcmwl driver. Also I suppose the issue doesn't comes from the driver, but I'm not sure. To help, here is some usefull info :

```
lsusbBus 004 Device 007: ID 05ac:828b Apple, Inc. 
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 003: ID 0424:2412 Standard Microsystems Corp. 
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 05ac:8511 Apple, Inc. 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 056a:00b5 Wacom Co., Ltd Intuos3 6x11 (PTZ-631W)
Bus 001 Device 005: ID 05ac:0250 Apple, Inc. Aluminium Keyboard (ISO)
Bus 001 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
lspci00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GTX 660M Mac Edition] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57766 Gigabit Ethernet PCIe (rev 01)
03:00.1 SD Host controller: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader (rev 01)
04:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
06:00.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Port [Cactus Ridge] (rev 03)
07:00.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Port [Cactus Ridge] (rev 03)
07:03.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Port [Cactus Ridge] (rev 03)
07:04.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Port [Cactus Ridge] (rev 03)
07:05.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Port [Cactus Ridge] (rev 03)
07:06.0 PCI bridge: Intel Corporation DSL3510 Thunderbolt Port [Cactus Ridge] (rev 03)
08:00.0 System peripheral: Intel Corporation DSL3510 Thunderbolt Port [Cactus Ridge] (rev 03)

```

```
lspci -nn | grep -i net03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57766 Gigabit Ethernet PCIe [14e4:1686] (rev 01)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)

```

```
sudo lshw -C network  *-network               
       description: Ethernet interface
       produit: NetXtreme BCM57766 Gigabit Ethernet PCIe
       fabriquant: Broadcom Corporation
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       nom logique: eth0
       version: 01
       numéro de série: 10:dd:b1:9d:4e:a7
       capacité: 1Gbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm vpd msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=57766a-v1.13 latency=0 link=no multicast=yes port=twisted pair
       ressources: irq:18 mémoire:b1800000-b180ffff mémoire:b1810000-b181ffff
  *-network
       description: Interface réseau sans fil
       produit: BCM4331 802.11a/b/g/n
       fabriquant: Broadcom Corporation
       identifiant matériel: 0
       information bus: pci@0000:04:00.0
       nom logique: wlan0
       version: 02
       numéro de série: 8c:2d:aa:53:bb:8f
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.0.107 latency=0 multicast=yes wireless=IEEE 802.11abg
       ressources: irq:19 mémoire:b1900000-b1903fff

```

```
iwconfigeth0      no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"BBM Air 5"  
          Mode:Managed  Frequency:5.5 GHz  Access Point: 80:EA:96:EC:59:09   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


lxcbr0    no wireless extensions.

```

```
ifconfigeth0      Link encap:Ethernet  HWaddr 10:dd:b1:9d:4e:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:18 


lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          Packets reçus:700 erreurs:0 :0 overruns:0 frame:0
          TX packets:700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:55064 (55.0 KB) Octets transmis:55064 (55.0 KB)


lxcbr0    Link encap:Ethernet  HWaddr 8a:02:e5:e6:e2:29  
          inet adr:10.0.3.1  Bcast:10.0.3.255  Masque:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 B) Octets transmis:15814 (15.8 KB)


wlan0     Link encap:Ethernet  HWaddr 8c:2d:aa:53:bb:8f  
          inet adr:192.168.0.107  Bcast:192.168.0.255  Masque:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:46984 erreurs:0 :0 overruns:0 frame:53621
          TX packets:26225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:52922425 (52.9 MB) Octets transmis:2920351 (2.9 MB)
          Interruption:19 

```

```
uname -r -m 3.18.11-031811-generic x86_64

```

```
nm-tool

NetworkManager Tool


State: connected (global)


- Device: wlan0  [Auto BBM Air 5] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        8C:2D:AA:53:BB:8F


  Capabilities:
    Speed:           450 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    BBM Air 2:       Infra, 80:EA:96:EC:59:08, Freq 2472 MHz, Rate 54 Mb/s, Strength 100 WPA2
    MOVISTAR_44DF:   Infra, D8:61:94:64:44:DF, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA
    dlink_wifi:      Infra, E8:DE:27:DD:D9:AB, Freq 2417 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    BBM:             Infra, F8:8E:85:FA:0B:83, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA
    *BBM Air 5:      Infra, 80:EA:96:EC:59:09, Freq 5500 MHz, Rate 54 Mb/s, Strength 87 WPA2
    MOVISTAR_187B:   Infra, F8:8E:85:6C:18:7C, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA
    vodafone9C34:    Infra, 5C:4C:A9:6C:9C:35, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA
    Vodafone14AG:    Infra, D8:61:94:31:14:A1, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA


  IPv4 Settings:
    Address:         192.168.0.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254


    DNS:             80.58.61.250
    DNS:             80.58.61.254




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        10:DD:B1:9D:4E:A7


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off

```

```
sudo rfkill list0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Any help ?

---

### Post by chili555 on 2015-04-18
Man, oh man! Where do I even start? As I am regarded as the resident Broadcom guy, the guys in the back room have urged, with a certain degree of scepticism, that I take on your issue. Monday, I may give up all my beans and start with a new user name!

I feel like the question is really that the native driver isn't working with a mainline kernel, that is, one not made for a standard Ubuntu version, so you tried the proprietary STA driver and it doesn't work either; what to do. 

Let's wade in and see what we can see. First, does the device connect and stay connected to the 2.4 gHz AP; suggesting this is a 5 gHz HT issue? Second, which version of the STA driver is installed?```
sudo dpkg -s bcmwl-kernel-source | grep Version
```If you have 6.30.223.248+bdcom-0ubuntu1, I wonder if you might have better luck with 6.30.223.248+bdcom-0ubuntu2 from here: [http://packages.ubuntu.com/vivid/bcmwl-kernel-source](http://packages.ubuntu.com/vivid/bcmwl-kernel-source)

Next, if you reboot and select a standard Ubuntu linux-image, such as 3.16.0-34-generic, does the problem remain? If you selected that same linux-image and use b43 and firmware, does the problem remain?

Finally, what does this tell us:```
sudo iwlist wlan0 scan
```We only care about BBM Air 5; feel free to remove all others.

---

### Post by jeff-artik on 2015-04-19
Thanks a lot Doc' ! Let's give you some info.

I'm going to try the 2.4 gHz, but because of the excitement and the time it can takes to be tested (1/2 days), I'll test this in last.
My STA driver version was :

```
sudo dpkg -s bcmwl-kernel-source | grep Version
Version: 6.30.223.248+bdcom-0ubuntu0.1

```
So the 0.1 version, even not the 1. I updated with the one you suggested me :

```
sudo dpkg -s bcmwl-kernel-source | grep Version
Version: 6.30.223.248+bdcom-0ubuntu2

```
Then I'm gonna proceed step by step. I'll wait with the 3.18.11-031811-generic x86_64 for the moment, until it disconnects. If yes, back to 3.13.

Finally a scan returns me this :

```
sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 80:EA:96:EC:59:09
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"BBM Air 5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 000942424D204169722035
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 07344652202401172801172C01173001173401173801173C011740011764011E68011E6C011E70011E74011E84011E88011E8C011E00
                    IE: Unknown: 200100
                    IE: Unknown: 23021800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AEF0917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D16640D0400000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: BF0CB259820FEAFF0000EAFF0000
                    IE: Unknown: C005016A000000
                    IE: Unknown: C30402020202
                    IE: Unknown: DD0B0017F20100010100000007
                    IE: Unknown: DD0700039301780320
                    IE: Unknown: DD0E0017F2070001010680EA96EC5909
                    IE: Unknown: DD090010180207001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000

```

If the issue is not solved, I'll try b43 with my outofbox 3.13 kernel.

Now fingers are crossed, but it seems you know how to use scalpel. Total confidence !

---

### Post by chili555 on 2015-04-19
I see nothing to dislike in the scan; you are using WPA2-AES only. I await the results with the later version of bcmwl-kernel-source.

---

### Post by jeff-artik on 2015-04-20
Logs seems to be good Chili! I wait this week to confirm and set this topic as solved. But before getting exited for nothing, I prefer to be patient, because 2 days without diconnection already arrived.

```
artik ~ less /var/log/syslog | grep CTRLApr 19 08:30:21 artik-iMac wpa_supplicant[1026]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 08:32:21 artik-iMac wpa_supplicant[1026]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 09:30:21 artik-iMac wpa_supplicant[1026]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 09:32:21 artik-iMac wpa_supplicant[1026]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 10:30:21 artik-iMac wpa_supplicant[1026]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 10:32:21 artik-iMac wpa_supplicant[1026]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 11:30:21 artik-iMac wpa_supplicant[1026]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 11:32:21 artik-iMac wpa_supplicant[1026]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 11:45:49 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 11:45:52 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-CONNECTED - Connection to 80:ea:96:ec:59:09 completed [id=0 id_str=]
Apr 19 11:46:09 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 12:45:01 artik-iMac wpa_supplicant[1014]: message repeated 33 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 12:47:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 13:15:01 artik-iMac wpa_supplicant[1014]: message repeated 14 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 13:17:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 14:15:01 artik-iMac wpa_supplicant[1014]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 14:17:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 15:07:01 artik-iMac wpa_supplicant[1014]: message repeated 25 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 15:09:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 15:11:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 16:09:01 artik-iMac wpa_supplicant[1014]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 16:11:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 17:09:01 artik-iMac wpa_supplicant[1014]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 17:11:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 18:09:01 artik-iMac wpa_supplicant[1014]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 18:11:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 19:09:01 artik-iMac wpa_supplicant[1014]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 19:11:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 19:59:01 artik-iMac wpa_supplicant[1014]: message repeated 24 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 20:01:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 20:13:01 artik-iMac wpa_supplicant[1014]: message repeated 6 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 20:15:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 21:13:01 artik-iMac wpa_supplicant[1014]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 21:15:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 22:13:01 artik-iMac wpa_supplicant[1014]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 22:15:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 19 23:13:01 artik-iMac wpa_supplicant[1014]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 19 23:15:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 20 00:13:01 artik-iMac wpa_supplicant[1014]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 20 00:15:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 20 01:13:01 artik-iMac wpa_supplicant[1014]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 20 01:15:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 20 02:13:01 artik-iMac wpa_supplicant[1014]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 20 02:15:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 20 08:13:01 artik-iMac wpa_supplicant[1014]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 20 08:15:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 20 09:13:01 artik-iMac wpa_supplicant[1014]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 20 09:15:01 artik-iMac wpa_supplicant[1014]: wlan0: CTRL-EVENT-SCAN-STARTED 
```

---

### Post by jeff-artik on 2015-04-22
Chili, after 3 or 4 days without any disconnection or strange message (the logs always show what I posted before), I consider it as solved. Once again many thanks Doctor, and I reopen it in case of ...

---

### Post by chili555 on 2015-04-22
Awesome! Glad it's working.

---

### Post by jeff-artik on 2015-04-27
Damn, my bug is back, maybe I was lucky last week.... Disconnected at 10:28. Also trying to focus the issue, I saw the Country code could be the reason, so I edited this file :

```
sudo subl /lib/udev/rules.d/*reg*
```

And i commented the line :

```
#KERNEL=="regulatory*", ACTION=="change", SUBSYSTEM=="platform", RUN+="/sbin/crda"
```

But didn't change. I'm also on the good driver :

```
sudo dpkg -s bcmwl-kernel-source | grep VersionVersion: 6.30.223.248+bdcom-0ubuntu2
```

Here's my log. What is strange in it ? Maybe I should back to a previous kernel so ?

```
Apr 27 08:09:01 artik-iMac CRON[11537]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))Apr 27 08:17:01 artik-iMac CRON[11558]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 27 08:30:32 artik-iMac wpa_supplicant[1062]: message repeated 23 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 27 08:32:28 artik-iMac wpa_supplicant[1062]: wlan0: WPA: Group rekeying completed with 80:ea:96:ec:59:09 [GTK=CCMP]
Apr 27 08:32:32 artik-iMac wpa_supplicant[1062]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 27 08:39:01 artik-iMac CRON[11635]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Apr 27 09:09:01 artik-iMac CRON[11736]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Apr 27 09:17:01 artik-iMac CRON[11787]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 27 09:30:32 artik-iMac wpa_supplicant[1062]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 27 09:32:28 artik-iMac wpa_supplicant[1062]: wlan0: WPA: Group rekeying completed with 80:ea:96:ec:59:09 [GTK=CCMP]
Apr 27 09:32:32 artik-iMac wpa_supplicant[1062]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 27 09:39:01 artik-iMac CRON[11873]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Apr 27 10:09:01 artik-iMac CRON[12076]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Apr 27 10:17:01 artik-iMac CRON[12126]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 27 10:20:32 artik-iMac wpa_supplicant[1062]: message repeated 24 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 27 10:21:16 artik-iMac wpa_supplicant[1062]: wlan0: WPA: Group rekeying completed with 80:ea:96:ec:59:09 [GTK=CCMP]
Apr 27 10:22:32 artik-iMac wpa_supplicant[1062]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 27 10:28:32 artik-iMac wpa_supplicant[1062]: message repeated 3 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 27 10:28:42 artik-iMac wpa_supplicant[1062]: wlan0: CTRL-EVENT-DISCONNECTED bssid=80:ea:96:ec:59:09 reason=0
Apr 27 10:28:42 artik-iMac kernel: [63712.651859] cfg80211: Calling CRDA for country: FR
Apr 27 10:28:42 artik-iMac NetworkManager[970]: <info> (wlan0): roamed from BSSID 80:EA:96:EC:59:09 (BBM Air 5) to (none) ((none))
Apr 27 10:28:42 artik-iMac NetworkManager[970]: <info> (wlan0): supplicant interface state: completed -> disconnected
Apr 27 10:28:42 artik-iMac wpa_supplicant[1062]: wlan0: Reject scan trigger since one is already pending
Apr 27 10:28:42 artik-iMac wpa_supplicant[1062]: wlan0: Failed to initiate AP scan
Apr 27 10:28:43 artik-iMac wpa_supplicant[1062]: wlan0: Reject scan trigger since one is already pending
Apr 27 10:28:43 artik-iMac wpa_supplicant[1062]: wlan0: Failed to initiate AP scan
Apr 27 10:28:44 artik-iMac wpa_supplicant[1062]: wlan0: Reject scan trigger since one is already pending
Apr 27 10:28:44 artik-iMac wpa_supplicant[1062]: wlan0: Failed to initiate AP scan
Apr 27 10:28:45 artik-iMac wpa_supplicant[1062]: wlan0: Reject scan trigger since one is already pending
Apr 27 10:28:45 artik-iMac wpa_supplicant[1062]: wlan0: Failed to initiate AP scan
Apr 27 10:28:46 artik-iMac wpa_supplicant[1062]: wlan0: Reject scan trigger since one is already pending
Apr 27 10:28:46 artik-iMac wpa_supplicant[1062]: wlan0: Failed to initiate AP scan
Apr 27 10:28:47 artik-iMac wpa_supplicant[1062]: wlan0: Reject scan trigger since one is already pending
Apr 27 10:28:47 artik-iMac wpa_supplicant[1062]: wlan0: Failed to initiate AP scan
Apr 27 10:28:48 artik-iMac wpa_supplicant[1062]: wlan0: Trying to associate with 80:ea:96:ec:59:09 (SSID='BBM Air 5' freq=5500 MHz)
Apr 27 10:28:48 artik-iMac NetworkManager[970]: <info> (wlan0): supplicant interface state: disconnected -> associating
Apr 27 10:28:48 artik-iMac wpa_supplicant[1062]: wlan0: CTRL-EVENT-ASSOC-REJECT bssid=80:ea:96:ec:59:09 status_code=16
Apr 27 10:28:48 artik-iMac NetworkManager[970]: <info> (wlan0): supplicant interface state: associating -> disconnected
Apr 27 10:28:48 artik-iMac wpa_supplicant[1062]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 27 10:28:48 artik-iMac NetworkManager[970]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 27 10:28:57 artik-iMac wpa_supplicant[1062]: wlan0: Trying to associate with 80:ea:96:ec:59:09 (SSID='BBM Air 5' freq=5500 MHz)
Apr 27 10:28:57 artik-iMac NetworkManager[970]: <info> (wlan0): supplicant interface state: scanning -> associating
Apr 27 10:28:57 artik-iMac wpa_supplicant[1062]: wlan0: CTRL-EVENT-ASSOC-REJECT bssid=80:ea:96:ec:59:09 status_code=16
Apr 27 10:28:57 artik-iMac NetworkManager[970]: <info> (wlan0): supplicant interface state: associating -> disconnected
Apr 27 10:28:57 artik-iMac NetworkManager[970]: <warn> (wlan0): link timed out.
Apr 27 10:28:57 artik-iMac NetworkManager[970]: <info> (wlan0): device state change: activated -> failed (reason 'supplicant-timeout') [100 120 11]
Apr 27 10:28:57 artik-iMac NetworkManager[970]: <info> NetworkManager state is now DISCONNECTED
Apr 27 10:28:57 artik-iMac NetworkManager[970]: <warn> Activation (wlan0) failed for connection 'Auto BBM Air 5'
Apr 27 10:28:57 artik-iMac dbus[519]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 27 10:28:57 artik-iMac NetworkManager[970]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 27 10:28:57 artik-iMac NetworkManager[970]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 27 10:28:57 artik-iMac dbus[519]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 27 10:28:58 artik-iMac NetworkManager[970]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2661
Apr 27 10:28:58 artik-iMac NetworkManager[970]: <warn> DNS: plugin dnsmasq update failed
Apr 27 10:28:58 artik-iMac NetworkManager[970]: <info> Removing DNS information from /sbin/resolvconf
Apr 27 10:28:58 artik-iMac dnsmasq[2664]: configuration des serveurs amonts à partir de DBus
Apr 27 10:28:58 artik-iMac wpa_supplicant[1062]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Auto-activating connection 'Auto BBM Air 5'.
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0) starting connection 'Auto BBM Air 5'
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> NetworkManager state is now CONNECTING
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0/wireless): access point 'Auto BBM Air 5' has security, but secrets are required.
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0/wireless): connection 'Auto BBM Air 5' has security, and secrets exist.  No new secrets needed.
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Config: added 'ssid' value 'BBM Air 5'
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Config: added 'scan_ssid' value '1'
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Config: added 'auth_alg' value 'OPEN'
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Config: added 'psk' value '<omitted>'
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 27 10:29:00 artik-iMac NetworkManager[970]: <info> Config: set interface ap_scan to 1
Apr 27 10:29:06 artik-iMac wpa_supplicant[1062]: wlan0: Trying to associate with 80:ea:96:ec:59:09 (SSID='BBM Air 5' freq=5500 MHz)
Apr 27 10:29:06 artik-iMac NetworkManager[970]: <info> (wlan0): supplicant interface state: disconnected -> associating
Apr 27 10:29:07 artik-iMac wpa_supplicant[1062]: wlan0: CTRL-EVENT-ASSOC-REJECT bssid=80:ea:96:ec:59:09 status_code=16
Apr 27 10:29:07 artik-iMac wpa_supplicant[1062]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="BBM Air 5" auth_failures=1 duration=10
Apr 27 10:29:07 artik-iMac wpa_supplicant[1062]: wlan0: Trying to associate with 80:ea:96:ec:59:09 (SSID='BBM Air 5' freq=5500 MHz)
Apr 27 10:29:07 artik-iMac wpa_supplicant[1062]: wlan0: CTRL-EVENT-ASSOC-REJECT bssid=80:ea:96:ec:59:09 status_code=16
Apr 27 10:29:07 artik-iMac wpa_supplicant[1062]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="BBM Air 5" auth_failures=2 duration=20
Apr 27 10:29:07 artik-iMac NetworkManager[970]: <info> (wlan0): supplicant interface state: associating -> disconnected
Apr 27 10:29:17 artik-iMac wpa_supplicant[1062]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 27 10:29:17 artik-iMac NetworkManager[970]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <warn> Activation (wlan0/wireless): association took too long.
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <warn> Activation (wlan0/wireless): asking for new secrets
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> Activation (wlan0/wireless): connection 'Auto BBM Air 5' has security, and secrets exist.  No new secrets needed.
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> Config: added 'ssid' value 'BBM Air 5'
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> Config: added 'scan_ssid' value '1'
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> Config: added 'auth_alg' value 'OPEN'
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> Config: added 'psk' value '<omitted>'
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Apr 27 10:29:25 artik-iMac NetworkManager[970]: message repeated 2 times: [ <warn> Couldn't disconnect supplicant interface: This interface is not connected.]
Apr 27 10:29:25 artik-iMac NetworkManager[970]: <info> Config: set interface ap_scan to 1

```

---

### Post by chili555 on 2015-04-27
>  I saw the Country code could be the reason, so I edited this file :
```
sudo subl /lib/udev/rules.d/*reg*

```
And i commented the line :```
#KERNEL=="regulatory*", ACTION=="change", SUBSYSTEM=="platform", RUN+="/sbin/crda"
```

But didn't change. I'd change that back as it was. Then, I recommend that your regulatory domain be set explicitly. Check yours:

```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

```
gksudo gedit /etc/default/crda
```

Use nano or kate or leafpad if you don't have the text editor gedit. Change the last line to read:

```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

Reboot and let's see the log again.

---

### Post by jeff-artik on 2015-04-28
I reverted back my /lib/udev/rules.d/*reg* as original. I set my country to FR :

```
sudo iw reg get
    country FR:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR
```

before permanently do it, I tried the temporary one :

```
sudo iw reg set FR
```

But the result was always 00 with a sudo iw reg get. Permanently fixed it, so i'm now in FR. I wait this week and back to you ;)

---

### Post by chili555 on 2015-04-28
> I'll wait with the 3.18.11-031811-generic x86_64 for the moment, until it disconnects. If yes, back to 3.13.
Did you try that? Are the disconnects still present with the default 3.13 linux-image?> If the issue is not solved, I'll try b43 with my outofbox 3.13 kernel.Did you try that, as well? Better, same or worse?

---

### Post by jeff-artik on 2015-04-29
For the moment I'm trying with the 3.18. Because tests are long (almost one week), steps are too. But yes, if it disconnect again with what you suggested me in your last post (country code), I switch back to 3.13 with the new driver, and if still not : b43. For the moment, fixing the country code seems to be good. Answer next week (I know, doctors aren't patients) :)

---

### Post by jeff-artik on 2015-05-07
Chili, seems to be ok for me. Once again, many thanks. I reopen if the issue will back :D

---

