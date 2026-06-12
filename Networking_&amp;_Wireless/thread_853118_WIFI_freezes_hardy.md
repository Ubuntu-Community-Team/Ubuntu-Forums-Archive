---
title: "WIFI freezes hardy"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by pjcvdpol on 2008-07-08
SOLVED!!! Thanks to a fresh install (...) and this excellent guide: [http://ubuntuforums.org/showthread.php?p=5390603&posted=1#post5390603](http://ubuntuforums.org/showthread.php?p=5390603&posted=1#post5390603)


I have been trying random forumsolutions (mad wifi, all kind of atheros drivers etc. etc. ) for two months now, and I am fed up: I can't get the atheros card in my compaq presario A900 laptop to function properly with Hardy. 

I just reinstalled the net5211 driver in in ndiswrapper: it worked fine but when I wanted to connect to a wireless network my system froze, and only a hard power-off would kill the system (and my harddisk probably) Now all wireless networks have disappeared in Network Manager, Everything functiones fine with Vista. Argh!!!! I am desperate. Anyone? :confused:

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and: 

ndiswrapper -l
net5211 : driver installed
    device (168C:001C) present (alternate driver: ath_pci)   

I removed the ath_pci driver.1

sudo wpa_supplicant -iwlan0 -Dwext -c/etc/wpa_supplicant/config -w

ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
etc.

lspci:
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

/var/log/syslog at boot:

Jul  6 11:08:06 valiant kernel: [   41.971714] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  6 11:08:06 valiant NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'.
Jul  6 11:08:06 valiant NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00).
Jul  6 11:08:06 valiant NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
Jul  6 11:08:06 valiant NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
Jul  6 11:08:06 valiant NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'.
Jul  6 11:08:06 valiant NetworkManager: <info>  Deactivating device wlan0.
Jul  6 11:08:06 valiant NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument

/var/log messages says: 

Jul  6 11:08:03 valiant kernel: [   31.615412] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Jul  6 11:08:03 valiant kernel: [   31.771587] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul  6 11:08:03 valiant kernel: [   32.319948] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
Jul  6 11:08:03 valiant kernel: [   32.320246] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
Jul  6 11:08:03 valiant kernel: [   32.320318] ndiswrapper (ZwClose:2227): closing handle 0xdf84e028 not implemented
Jul  6 11:08:03 valiant kernel: [   32.733291] ndiswrapper: using IRQ 21
Jul  6 11:08:03 valiant kernel: [   32.937239] wlan0: ethernet device 00:1f:3a:9c:67:db using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
Jul  6 11:08:03 valiant kernel: [   32.944174] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jul  6 11:08:03 valiant kernel: [   32.976938] usbcore: registered new interface driver ndiswrapper

---

### Post by pjcvdpol on 2008-07-10
*bump* Anyone - please?

---

### Post by racie on 2008-07-10
In your Network Settings, is wireless an option?  I don't mean if it works or not, I just mean if it even shows up.  I've tried tons of things and I can't even get mine to show up.

---

### Post by pjcvdpol on 2008-07-10
> **racie said:**
> In your Network Settings, is wireless an option?  I don't mean if it works or not, I just mean if it even shows up.  I've tried tons of things and I can't even get mine to show up.

yes it does, but I can't see any networks. When I do "sudo iwlist scan" in a terminal it freezes/crashes the laptop after showing a list of available networks....

---

### Post by racie on 2008-07-10
Wow, yeah I have no clue, but this makes me wonder about my own laptop.  No one else seems to have the problem of wireless not showing up.  Best of luck to you and your wireless.  =P

---

### Post by pjcvdpol on 2008-07-11
Please???? I am pretty desperate....

---

### Post by pjcvdpol on 2008-07-12
Come on!!! Anyone??? this is so disappointing, I have been using Linux since 1996, but have NEVER been as stuck as this. What a disappointing experience.

---

