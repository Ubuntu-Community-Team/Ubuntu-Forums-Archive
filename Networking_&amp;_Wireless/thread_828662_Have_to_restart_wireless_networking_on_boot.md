---
title: "Have to restart wireless networking on boot"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by narsaw on 2008-06-14
I have running the latest desktop ubuntu on my Dell Inspiron 600m.

Everytime I boot up my wireless connection does not work. I cannot connected to the internet.

To get it to work I have to issue the following command:

```
sudo /etc/init.d/networking restart
```

At this point I get the following output:

```
Listening on LPF/eth1/00:0e:35:75:f4:89
Sending on   LPF/eth1/00:0e:35:75:f4:89
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0e:35:75:f4:89
Sending on   LPF/eth1/00:0e:35:75:f4:89
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.130 from 192.168.1.1
DHCPREQUEST of 192.168.1.130 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.130 from 192.168.1.1
bound to 192.168.1.130 -- renewal in 38318 seconds.
```

Then everything else works.

Here is what my /etc/network/interfaces looks like.

```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-psk ff224758a7e917f4303f3dd1969b27449cda733eb20cc167b42c6eeb660ad471
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid my_ssid

```

Any ideas on how to get this working at book?

---

### Post by Ayuthia on 2008-06-14
Are you using a Broadcom card?  If it is, what kind of wireless fix are you using?

---

### Post by lisati on 2008-06-14
After tinkering with the settings for my wireless to change over from WEP to WPA, I had a similar set of messages pop up, and also had to do a manual restart of the networking after rebooting.

There's a workaround for the manual restart in this thread: (edited) [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by lisati on 2008-06-14
Correction: have a look here: [http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2)

(Would have had it sooner, but my ubuntu box lost its wireless connection during an edit of my last post, and a little bit of troubleshooting was called for)

---

### Post by Rocket2DMn on 2008-06-15
I have this laptop, here is my /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

```
I am not using WPA, only WEP or open network.
If you do try that file out, don't forget to back up yours first (even though we have a copy in your original post).
I have sometimes found that if the computer did not shutdown properly, I have to wait a few minutes before I can bring up the wireless connection properly.

---

