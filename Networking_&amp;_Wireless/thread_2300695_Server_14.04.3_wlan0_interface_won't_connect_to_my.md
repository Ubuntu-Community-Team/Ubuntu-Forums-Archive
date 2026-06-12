---
title: "Server 14.04.3 wlan0 interface won't connect to my wireless router!"
date: 2015-10-27
forum: Networking &amp; Wireless
---

### Post by sly3 on 2015-10-27
Alright guys, 

I'm having a hell of a time trying to get my server to connect to my router.

-14.04 is the only OS on the machine, fresh install...
-router is WPA 2 personal, and yes I've jacked with the supplicants
- gateway addy verified
- I would prefer a static address

ifconfig:

lo   link encap:Local loopback
     inet addr: 127.0.0.1  Mask: 255.0.0.0
     inet6 addr:  ::1/128 Scope: Host
     UP LOOPBACK RUNNING  MTU:65536   Metric:1
     RX packets: 64 errors:0 dropped:0 overruns:0 frame:0
     TX packets:64 errors 0 dropped: 0 overruns: 0 carrier:0
     collisions: 0 txqueuelen: 0
     RX bytes: 5120 (5.1 KB) TX byes: 5120 (5.1KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:XX:XX:XX:XX
              UP BROADCAST MULTICAST MTU:1500 Metric:1
              RX packets: 0 errors: 0 dropped: 0 overruns:0 frame:0
              TX packets: 0 errors: 0 dropped: 0 overruns:0 carrier:0
              collisions: 0 txqueuelen: 1000
              RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

iwconfig: 

eth0   no wireless extensions

wlan0  IEEE 802.11abgn ESSID: "my essid in all caps & quotations"
          Mode:Managed   Access Point: Not-associated  TX-Power=14dBm
          Retry short limit:7  RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management: off

lo       no wireless extensions

my /etc/network/interfaces file:

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address: 192.168.0.250
netmask: 255.255.255.0
gateway 192.168.0.1
dns-nameservers 192.168.0.1 8.8.8.8
wpa-ssid <my ssid, all caps, no quotations>
wpa-psk <key>

When I type: sudo ifdown wlan0 && sudo ifup -v wlan0, I get this error:

"/etc/network/interfaces:4 misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"

What in the heck am I doing wrong, and how do I get this config to stick upon reboot??????

Thanks in advance!!!!!!!

---

### Post by chili555 on 2015-10-27
Do address and netmask actually have colons? It should read:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.0.250
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 192.168.0.1 8.8.8.8
wpa-ssid <my ssid, all caps, no quotations>
wpa-psk <key>
```Then try again:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```

---

