---
title: "Ubuntu Wireless crashes randomly"
date: 2015-10-01
forum: Networking &amp; Wireless
---

### Post by canberkana on 2015-10-01
Hello all. I have a HP A6750f which I still love using. Since a year, I have been lovingly using different versions of Ubuntu and unfortunately all versions crash randomly because of wireless connection. I have taken some shots addressing the  errors and the information collecting script from this forum. Any help will be greatly appreciated :confused:


[ATTACH]264772[/ATTACH]
[ATTACH=CONFIG]264774[/ATTACH][ATTACH=CONFIG]264775[/ATTACH]

---

### Post by chili555 on 2015-10-02
If it crashes with every version of Ubuntu, we suspect a hardware fault; in other words, the USB dongle is bad.

I did notice this in your wireless_info:> ##### rc.local ##########################

sudo modprobe rt73usb hwwep=0
sudo iwconfig wlan0 power off
First of all, rc.local doesn't require, nor can it use sudo. I suggest you amend the file to read:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iwconfig wlan0 power off

exit 0

```Second, the hwwep declaration is not a valid parameter for your driver:```
[rt73usb]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     BCF882E0CB338C7C3C172CF
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
```There is no hwwep parameter available.

If you keep getting drops, I'd look at a newer USB device.

---

### Post by canberkana on 2015-10-04
Hey chili. Thank you for your reply. I edited the rc.local as you have suggested. In my thread I forgot to add that my pc works completely fine on Windows. No errors or crashes. Is it possible to do anything else?

---

### Post by chili555 on 2015-10-04
Let's see if the log holds any clues as to the drop:```
cat /var/log/syslog | grep -e wlan -e rt73 | tail -n25
```

---

### Post by canberkana on 2015-10-04
Here is the output;

canberk@Canberk:~$ cat /var/log/syslog | grep -e wlan -e rt73 | tail -n25
Oct  4 20:55:34 Canberk NetworkManager[622]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Oct  4 20:55:34 Canberk NetworkManager[622]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '00000'.
Oct  4 20:55:34 Canberk NetworkManager[622]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  4 20:55:34 Canberk NetworkManager[622]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Oct  4 20:55:34 Canberk NetworkManager[622]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  4 20:55:34 Canberk NetworkManager[622]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  4 20:55:34 Canberk NetworkManager[622]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct  4 20:55:34 Canberk NetworkManager[622]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct  4 20:55:34 Canberk dhclient: DHCPREQUEST of 192.168.0.11 on wlan0 to 255.255.255.255 port 67 (xid=0x3dbf751c)
Oct  4 20:55:35 Canberk NetworkManager[622]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Oct  4 20:55:35 Canberk NetworkManager[622]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Oct  4 20:55:35 Canberk NetworkManager[622]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Oct  4 20:55:35 Canberk avahi-daemon[621]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.11.
Oct  4 20:55:35 Canberk avahi-daemon[621]: New relevant interface wlan0.IPv4 for mDNS.
Oct  4 20:55:35 Canberk avahi-daemon[621]: Registering new address record for 192.168.0.11 on wlan0.IPv4.
Oct  4 20:55:35 Canberk NetworkManager[622]: <info> (wlan0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Oct  4 20:55:35 Canberk NetworkManager[622]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Oct  4 20:55:35 Canberk NetworkManager[622]: <info> (wlan0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Oct  4 20:55:35 Canberk NetworkManager[622]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Oct  4 20:55:35 Canberk avahi-daemon[621]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::222:5fff:fe74:ba1e.
Oct  4 20:55:35 Canberk avahi-daemon[621]: New relevant interface wlan0.IPv6 for mDNS.
Oct  4 20:55:35 Canberk avahi-daemon[621]: Registering new address record for fe80::222:5fff:fe74:ba1e on wlan0.*.
Oct  4 20:55:35 Canberk NetworkManager[622]: <info> Policy set '00000' (wlan0) as default for IPv4 routing and DNS.
Oct  4 20:55:36 Canberk NetworkManager[622]: <info> Activation (wlan0) successful, device activated.
Oct  4 20:55:36 Canberk nm-dispatcher: Dispatching action 'up' for wlan0

---

