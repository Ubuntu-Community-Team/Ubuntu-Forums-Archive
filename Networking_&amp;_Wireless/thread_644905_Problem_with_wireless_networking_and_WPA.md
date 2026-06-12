---
title: "Problem with wireless networking and WPA"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by skipjack on 2007-12-19
Ok,

I'm running Gutsy with an Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61) card. My eth0 is working fine, that's what I am using right now....

I'm having trouble getting WPA to work....

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1A:80:49:2F:10  
          inet addr:192.168.5.105  Bcast:192.168.5.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2849 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2509959 (2.3 MB)  TX bytes:255389 (249.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41106 (40.1 KB)  TX bytes:41106 (40.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:E8:8A:95:0D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3955 (3.8 KB)  TX bytes:6277 (6.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-8A-95-0D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

/etc/network/intefaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
	address 192.168.5.8
	netmask 255.255.0.0
	network 192.168.5.0
	broadcast 192.168.5.255
	gateway 192.168.5.1

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -w -dd
post-down killall -q wpa_supplicant
wireless-essid WirelessG

/etc/wpa_supplicant.conf:

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

network={
	ssid="WirelessG"
	#scan_ssid=1
	proto=WPA
	key_mgmt=WPA-PSK
	psk=<HEX STRING>
	pairwise=TKIP
	group=TKIP
}

sudo wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -w
Trying to associate with SSID 'WirelessG'
Association request to the driver failed
CTRL-EVENT-TERMINATING - signal 2 received
Failed to disable WPA in the driver.

Also, for some reason under System->Administration->Network there are no more connections under the Connections Box.

If anyone could help I would appreciate it...Thanks

---

### Post by skipjack on 2007-12-19
Forgot to add:

ndiswrapper -l
netw4x32 : driver installed
        device (8086:4229) present (alternate driver: iwl4965)

---

