---
title: "[SOLVED] Wireless on Dell XPS1530"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by LittleG on 2008-06-09
Hi 
I've done a clean install of 8.10 and followed the information in the stickies for "Manual network configuration" and "Wireless Security" but can't get the wireless working. Wireless works flawlessly on windows (XP and Vista) and on the Eee PC 901. Wired connectivity is fine.

[B]The output from iwconfig is:
[/B]wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Tortellini"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:0C:20:03:B7:16
          Bit Rate=54 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Power Management:off
          Link Quality=96/100  Signal level=-31 dBm  Noise level=-66 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**iwlist scan**
wmaster0  Interface doesn't support scanning.

wlan0     No scan results

**gedit /etc/network/interfaces**
auto wlan0
iface wlan0 inet static
address 192.168.1.98
gateway 192.168.1.1
dns-nameservers 192.168.1.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid Tortellini
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk f218dde191b5b229952ce7feffdcd11e79babdca27b7501eeea80e5344b70d0b

iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0


**lshw**
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:91:8e:51
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.98 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

Has anyone got this working? If so, would really appreciate some assistance as I'm new to Linux and struggling ;-)

Thanks

Graham

---

### Post by macness on 2008-06-09
what happens when you go to system>administration>network and try to access the wireless that way?

---

### Post by superprash2003 on 2008-06-09
are you able to ping 192.168.1.1?

---

### Post by LittleG on 2008-06-10
Thanks for the quick response - I could not ping the router (even with a static IP address) and when I used DHCP the adapter assigned itself a 169. address. 

I reinstalled to start again from scratch and Ubuntu can see the wireless network (and an islist wlan0 scan returned the correct channel and encryption being used) but I can't connect even when I turn security off. 

When I run a lshw -C network command, the logical name of the wireless interface comes back as wmaster0 (and not wlan0) - is this likely to be a problem?

When I run dhclient -r wlan0 I get an error wmaster0: unknown hardware address type 801 

I'm proficient at networking and windows - new to Linux so any assistance on getting the wireless adapter working on Linux would be gratefully received.

Thanks

Graham

---

### Post by LittleG on 2008-06-10
Resolved in the end using ndiswrapper ... thanks for some great postings on other threads that helped me get going with this.

---

### Post by macness on 2008-06-10
> **LittleG said:**
> Resolved in the end using ndiswrapper ... thanks for some great postings on other threads that helped me get going with this.

I'm glad it was fixed! I'm surprised that ubuntu didn't read the restricted drivers off the bat.

You should mark this thread solved in the thread tools by the way.

---

