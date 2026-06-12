---
title: "Problem with Ndiswrapper (and SMC 2802 v2)"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by c.dric on 2006-12-13
hi

i'm not new to linux but it's the first time i work with ubuntu
and i'm having some problem getting my wifi card (SMC 2802w V2)
to work with ndiswrapper .

what i've done so far :

unloading prism54 and adding it to blacklist.

```
ndiswrapper -i /home/cedric/2802W.inf
Installing 2802w
Forcing parameter EnableRadio|0 to EnableRadio|1

```

```
ndiswrapper -m
modprobe config already contains alias directive

```

```
ndiswrapper -l
Installed drivers:
2802w           driver installed, hardware present

```

```
modprobe ndiswrapper
ndiswrapper version 1.31 loaded (preempt=no,smp=yes)
usbcore: registered new driver ndiswrapper

```

that 'usbcore' msg is strange, my card being pci 
and at that point wlan0 should appear when i do 
iwconfig but all i get is lo.

could someone point me in the right direction ?

thanks a lot,
cédric.

ps : i've also set-ut wpa_supplicant but i don't think it has anything to do with the current problem.

---

### Post by c.dric on 2006-12-13
well... i've removed the ndiswrapper i got from synaptic and installed the latest one manually, following instructions from here : (3rd post) [http://ubuntuforums.org/showthread.php?t=315745&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=315745&highlight=ndiswrapper)

ndiswrapper version 1.31 loaded (preempt=no,smp=yes)
ndiswrapper: driver 2802w (SMC,04/29/2004, 3.0.11.1) loaded
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
ndiswrapper: using IRQ 5
wlan0: ethernet device 00:04:e2:cd:de:f8 using NDIS driver: 2802w, version: 0x3000b, NDIS version: 0x501, vendor: 'SMC2802W 2.4GHz 54 Mbps Wireless PCI Adapter', 1260:3890.5.conf
wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
usbcore: registered new driver ndiswrapper

it seems to be ok now ... wlan0 shows up in iwconfig.
(i still don't know what usbcore has to do with it tho...

well i'm gonna try to get wpa going now ;)

---

### Post by FrodoB on 2006-12-13
Using WPA-PSK on Ubuntu 6.10 Edgy Eft:

1) Install wpasupplicant:

$ sudo apt-get update

$ sudo apt-get install wpasupplicant


2) Create a /etc/wpa_supplicant.conf file that contains the following: (make sure that your psk is the same as is in your access point router.)

===================== cut ================================================== ========
ctrl_interface=/var/run/wpa_supplicant

ap_scan=2 # 1 = broadcast SSID and 2 = hidden SSID

network={
ssid="Your_Essid_Name"
key_mgmt=WPA-PSK
proto=WPA
pairwise=TKIP
group=TKIP
psk="vjGRNMaOrREWXAVd1lnI2K2JN203K93TIwF55z99FF5Ow kSM5c7i0BnVu7mqiDL"
}

===================== cut ================================================== ========

You can make the WPA-PSK passphrases at Gibson Research's Perfect Passwords - GRC's Ultra High Security Password Generator:

[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

You must use the same passphrase in your Access Point Router for this to work. Replace my example with your own.

3) Edit the /etc/network/interfaces file and add a record for your wireless device:

$ sudo gedit /etc/network/interfaces

Add a record similar to this one, replacing wlan0 with the actual name of your interface.

===================== cut ================================================== ========
auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
wpa-ssid Your_SSID_Name
post-down killall -q wpa_supplicant

===================== cut ================================================== ========

Note that -Dwext is the driver that your device is using, please refer to the wpasupplicant
documentation for additional device driver information. The wext driver is good for
ndiswrapper and the Atheros devices at least.

Note that you need to change the interface, -i, to your wireless device name such as ath0 or wlan0, etc.

4) Reboot your system or use the following command:

sudo /etc/init.d/dbus restart

A complete system reboot can be helpful, so I recommend that.

---

### Post by FrodoB on 2006-12-13
Also refer to:

[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

---

### Post by c.dric on 2006-12-13
thanks for the help FrodoB ...

i've tried your method and the method referred in your second post (without /etc/wpa_supplicant.conf) but i can't get a lease in both case.

```
/etc/init.d/networking restart

Listening on LPF/wlan0/00:04:e2:cd:de:f8
Sending on   LPF/wlan0/00:04:e2:cd:de:f8
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:04:e2:cd:de:f8
Sending on   LPF/wlan0/00:04:e2:cd:de:f8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

```
dmesg

ADDRCONF(NETDEV_UP): wlan0: link is not ready
ndiswrapper (set_auth_mode:663): setting auth mode to 7 failed (C0010015)
ndiswrapper (set_auth_mode:663): setting auth mode to 7 failed (C0010015)
```

```
iwconfig wlan0

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
less /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
wpa-ssid AppleNet2
post-down killall -q wpa_supplicant

```

```
less /etc/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1
network={
ssid="AppleNet2"
key_mgmt=WPA-PSK
proto=WPA
pairwise=TKIP
group=TKIP
psk="3b4247281e333c08a8725f67711e54310f8b6c7c573d7e68b589f413771c84a3"
}

```

---

### Post by c.dric on 2006-12-14
Ok, i got it now ... my last prob was due to the "" around my psk key .

Thanks for the help.

---

