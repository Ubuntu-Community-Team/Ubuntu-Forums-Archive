---
title: "Need restart for wireless (WG311T/madwifi/wpasupplicant)"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by jdbartlett on 2006-07-28
I 'm setting up a Linux test server for use in an office where there may only be wireless access available. So far, I've set up the Netgear WG311T card I put in the machine using madwifi (which didn't come with Ubuntu Server, so I installed linux-restricted-modules-2.6.15-23-386) and configured /etc/network/interfaces to work with wpasupplicant (which oddly enough did come with Ubuntu Server). The connection seems fine - WPA encryption, unbroadcast SSID, all fine! The problem is that if I ifdown ath0 and then try to ifup ath0 again, it fails to connect unless I restart the machine (using shutdown -r now). Even if I try a networking restart, it still fails until Ubuntu is restarted.

When failing, DHCPDISCOVER starts sending out its requests. Finally, after 7 requests or so, I get the notice "No DHCPOFFERS received" followed by the line "No working leases in persistent database - sleeping."

Any ideas how I can correct this problem?

If it helps, this is my complete /etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Ethernet
iface eth0 inet dhcp

# Wireless
iface ath0 inet dhcp
wpa-driver madwifi
wpa-ssid MYSSIDWASHERE
wpa-ap-scan 1
wpa-scan-ssid 1
wpa-key-mgmt WPA-PSK
wpa-passphrase MYPASSPHRASEWASHERE
```

I've been working with Linux for a couple of years now but am still very much a "noob" and not especially familiar with its workings (if anyone has any book recommendations, please post!) My lack of familiarity is in part why I wanted to make this a server install and not a regular desktop installation with Apache, MySQL, etc. installed afterward. This way, I can force myself to become familiar with command line Linux.

If you'd like to see any logs or other files, please tell me the commands and I'll post them. Thanks!

---

### Post by wieman01 on 2006-07-29
Not sure if that's your problem but with hidden ESSID's you need to change this:

> wpa-ap-scan 2

I am scratching at how you get it working in the first place... Let me know if that works.

---

### Post by jdbartlett on 2007-08-22
I spotted this old thread of mine after a search.  Sorry to have left it dead for so long!

I wasn't really able to resolve this issue and ended up lugging the box over to the router and remoting in via NX. From the latest Tribe it looks as though better Madwifi drivers may be coming in 7.10.

---

