---
title: "wlan: unsuccesful DHCP lease renewal"
date: 2018-10-09
forum: Networking &amp; Wireless
---

### Post by geestbos on 2018-10-09
My WiFi connection on my desktop PC breaks regularly, only to be then restored again using "sudo service NetworkManager restart".

As far as I can remember the Wifi card in this PC has been giving my headaches. And I don't dear to count the hours I have already spent trying to decypher the syslog messages of NetworkManager, ModemManager and the likes. But, unlike my family members, I had come to accept a regular restart of the NetworkManager service as part of the Ubuntu deal.

However, where earlier network error logs seemed to be non-consistent, nowadays I do see a recurring pattern. And with some help from your side, I might be able to improve stability of my WiFi connection.

The pattern mentioned above boils down to the connection being systematically dropped at the end of the lease period. The DHCP lease is obtained with a least time of 3600s and a renewal time of 1800s. After that renewal time, I indeed see DHCPREQUEST messages appearing, like
```
dhclient[17105]: DHCPREQUEST of 192.168.1.9 on wlan0 to 192.168.1.1 port 67 (xid=0x4dff50b4)
```, but I don't see DHCPACK or DHCPOFFER messages following. When the lease period ends, the IP address is then withdrawn (```
avahi-daemon[1043]: Withdrawing address record for fe80::213:46ff:fe8a:7e6c on wlan0

```) and NetworkManager does not succeed in autonomously restoring the connection. Would you agree that the apparently ignored DHCP requests are something to look further into? If so, what should I check specifically?

Fyi: this is the output of the wireless-info script: [http://paste.ubuntu.com/p/zYMDPd5tkQ/](http://paste.ubuntu.com/p/zYMDPd5tkQ/). If requested, I'm also happy to provide other logs and/or syslog snippets.

---

### Post by geestbos on 2019-03-19
We're 5 months later and there has unfortunately not been a substantial breakthrough from my side yet. Nevertheless, I do have some new insights, that I wanted to append to this thread. 

First of all, the uneffectiveness of the renewal and rebinding requests appear to be linked to the network bridge (a wireless repeater) I'm connecting through. The same occurs with an Ubuntu netbook. Also there renewal and rebinding requests are uneffective when the netbook is placed behind the bridge, but they do result in lease renewal when the netbook is connecting directly to the router. The difference between the desktop and the netbook is that the netbook does automatically get a new lease at lease expiry (when placed behind the bridge), and the desktop doesn't. And that is the real issue that needs to be tackled. 

Next, I believe to have stumbled upon something when comparing the syslog messages for eth0 -which to my surprise does renew the lease after expiry- and wlan0 after lease expiry. There is a difference in the avahi-daemon logs:

For eth0 I get these messages:
Mar 19 14:27:48 desk1 avahi-daemon[852]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.4.
Mar 19 14:27:48 desk1 avahi-daemon[852]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.5.

Whereas for wlan0 I get these messages:
Mar 19 11:23:20 desk1 avahi-daemon[904]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.8.
Mar 19 11:23:20 desk1 avahi-daemon[904]: Interface wlan0.IPv4 no longer relevant for mDNS.

Up until that point there is no difference in the syslog messages between wlan0 and eth0, so I guess I would next need to try to understand that difference.

Finally, I would like to mention that the dhcp renewal issue is also present when manually connecting wlan0 through ifup. So, it's not a network-manager issue. 

As always, any help or input is appreciated. 



Different configuration changes occurred meanwhile (e.g. switched to systemd-resolved from resolvconf; re-installed many packages including network-manager; removed anbox; switch to network-manager's internal DHCP client ), so I've pasted the new wireless_info output here: [http://paste.ubuntu.com/p/P7pPt7RQN4/](http://paste.ubuntu.com/p/P7pPt7RQN4/).

---

### Post by geestbos on 2019-03-28
I believe I finally solved the issue. 

First of all, I removed openresolv, avahi-daemon and ifupdown. This did not resolve the issue, at least not alone, but perhaps cleared up some of the syslog fog. 

I also purged resolvconf -previously already removed- and manually removed some of the remaining -even after the purge- scripts inside /etc/network referrring to resolvconf and avahi-daemon (if-up.d/000resolvconf, if-up.d/avahi-daemon, if-down.d/avahi-autoipd, if-down.d/resolvconf ... I for now left if-up.d/avahi-autoipd as removal caused extra problems). I'm not sure whether this had any effect though. For sure the issue was still not solved afterwards.

Comparing now again syslog output between eth0 lease expiry and wlan0 lease expiry, I saw that wlan0 re-instatement failed from these lines in syslog onwards:

```
Mar 28 10:56:36 desk1 wpa_supplicant[794]: nl80211: deinit ifname=wlan0 disabled_11b_rates=0
Mar 28 10:56:36 desk1 NetworkManager[816]: <debug> [1553766996.4307] device[0x560603d3f780] (wlan0): wifi-scan: scan-done callback: failed
Mar 28 10:56:36 desk1 wpa_supplicant[794]: wlan0: CTRL-EVENT-TERMINATING
```

This brought me to following post on wpa_supplicant failure: [https://askubuntu.com/questions/828076/connection-802-1x-supplicant-failed](https://askubuntu.com/questions/828076/connection-802-1x-supplicant-failed).

And, indeed, the their suggested removal of wicd seemed to do the trick.

Going back to the previous wireless_info outputs, I now see the issue was under my nose the whole time. It was clearly indicated that two network managers were installed. 

For completeness, here is my current wireless config: [http://paste.ubuntu.com/p/wXpBqJH43j/](http://paste.ubuntu.com/p/wXpBqJH43j/)

---

### Post by geestbos on 2019-03-29
For completeness, some hours after yesterday' post suddenly no address could no longer be obtained from the WIFI repeater. The DHCP client kept spawning DISCOVER requests, but without a DHCP OFFER being received. Comparing the network packets using Wireshark between my netbook and desktop I observed the netbook was sending out MDNS packets just before the offer came, and the desktop wasn't sending them out. I realized that libnss-mdns had been removed along with avahi-daemon, and indeed re-installing avahi-daemon (which also re-installed libnss-mdns) solved the issue.

---

