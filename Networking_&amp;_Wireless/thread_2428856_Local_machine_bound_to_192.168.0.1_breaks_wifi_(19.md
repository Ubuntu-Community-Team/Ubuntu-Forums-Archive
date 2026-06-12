---
title: "Local machine bound to 192.168.0.1 breaks wifi (19.04)"
date: 2019-10-10
forum: Networking &amp; Wireless
---

### Post by bk6u on 2019-10-10
I'm experiencing issues connecting to a particular wireless network on Ubuntu 19.04. The machine works fine on other networks, and even on the problematic network via a wifi hotspot on my phone. Other devices work fine on the problematic network, including a machine running 18.04.

The core issue seems to be that the machine is always available on 192.168.0.1, which is the default router address on many networks. I've confirmed on one network that changing the router IP address fixed the problem.

I can't find any useful error messages in the logs - those that I do see have lead me down rabbit holes of editing my resolv.conf and hosts files, neither of which have fixed the problem.

I don't know how else the machine would be making itself available on 192.168.0.1, or how to track down what is causing the issue.

(This may be a red herring, but the problem may have started after I tried to connect to an VPN. However, it could also be that I just didn't notice until after I did that.)

See attached for the output of the [wifi diagnostic script]("https://github.com/UbuntuForums/wireless-info"). If anyone can point me in the right direction, it would be much appreciated.

---

### Post by bk6u on 2019-10-11
As an additional data point, I've now tested on the same machine with an Ubuntu 19.04 live USB with no issues, so this is presumably some kind of configuration issue which only affects this network, and not a problem with the machine hardware or the router.

---

### Post by jeremy31 on 2019-10-11
See if ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```
Fixes the disconnects

---

### Post by bk6u on 2019-10-11
Thanks for the suggestion. Unfortunately that hasn't helped, but I think I've figured out why this particular network has issues (although not what's the underlying cause). In trying to ascertain what I can connect to I tried connecting to my router's admin page at 192.168.0.1 and got...the Apache server that's running on my local machine. Presumably this is the cause of all the issues, and explains why it's only an issue on this network, because it happens to use that address for DNS lookups.

What I don't know is **why** this is the case. Presumably something is binding to that IP (my first thought was something in /etc/hosts or my apache config but nothing jumped out). Any suggestions as to how can I track down what is using this IP address?

---

### Post by bk6u on 2019-12-18
This is still an issue - I've updated the original post with some more information reflecting what I've found so far.

---

### Post by SeijiSensei on 2019-12-18
What does
```
ip addr | grep 'inet '
```
return?  Are any addresses 192.168.0.1?

Next try
```
arp -n
```
which will show a list of machines with their IP addresses and MAC addresses. Is 192.168.0.1 in the list?  

If I look up my router's MAC address on Google, it takes me to page that correctly identifies the device as manufactured by TP-Link.

---

### Post by bk6u on 2019-12-19
Thanks for the pointers - this looks like it's turned up something useful. I get the following information from those commands:

```

$ ip addr | grep "inet" | grep 192
    inet 192.168.43.51/24 brd 192.168.43.255 scope global dynamic noprefixroute wlp59s0
    inet 192.168.0.1/20 brd 192.168.15.255 scope global br-5bf3d35782b1

$ arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.39                     (incomplete)                              br-5bf3d35782b1
192.168.43.35            ether   7e:10:eb:6e:1b:74   C                     wlp59s0


```

The bridge with the IP 192.168.0.1 appears whether I'm connected to a network or not, which strongly suggests it's something that's configured on the machine that's the problem. How can I now go about figuring out what this interface is and remove/reconfigure it? Thanks.

---

### Post by The Cog on 2019-12-19
I would search the whole of /etc looking for that IP address to find out which config file it's in. try:
```
sudo grep -RsC3 '192.168.0.1' /etc
```
You will likely get several hits, but it should be fairly obvious which one is a network configuration file.

---

### Post by bk6u on 2019-12-19
Thanks for the suggestion. Unfortunately I can't see anything that looks relevant or active. The one reference that seemed promising was in /etc/xl2tpd/xl2tpd.conf, where I had:

```

ip range = 192.168.0.1-192.168.0.20

```

However, changing this range to start at 192.168.0.2 and restarting still results in the same result from ip addr show br-5bf3d35782b1, so unless I need to do something extra to clear that interface that doesn't seem to be it. All of the other results look benign or inactive:

```

$ sudo grep -RsC3 '192.168.0.1' /etc
/etc/fwupd/redfish.conf-[redfish]
/etc/fwupd/redfish.conf-
/etc/fwupd/redfish.conf-# The URI to the Redfish service in the format <scheme>://<ip>:<port>
/etc/fwupd/redfish.conf:# ex: https://192.168.0.133:443
/etc/fwupd/redfish.conf-#Uri=
/etc/fwupd/redfish.conf-
/etc/fwupd/redfish.conf-# The username and password to the Redfish service
--
/etc/avahi/hosts-# See avahi.hosts(5) for more information on this configuration file!
/etc/avahi/hosts-
/etc/avahi/hosts-# Examples:
/etc/avahi/hosts:# 192.168.0.1 router.local
/etc/avahi/hosts-# 2001::81:1 test.local
--
/etc/sane.d/saned.conf-# The hostname matching is not case-sensitive.
/etc/sane.d/saned.conf-
/etc/sane.d/saned.conf-#scan-client.somedomain.firm
/etc/sane.d/saned.conf:#192.168.0.1
/etc/sane.d/saned.conf:#192.168.0.1/29
/etc/sane.d/saned.conf-#[2001:db8:185e::42:12]
/etc/sane.d/saned.conf-#[2001:db8:185e::42:12]/64
/etc/sane.d/saned.conf-
--
/etc/sane.d/magicolor.conf-
/etc/sane.d/magicolor.conf-### The following is a magicolor 1690mf with explicit IP-Address
/etc/sane.d/magicolor.conf-#net 10.0.0.5 0x2098
/etc/sane.d/magicolor.conf:# net 192.168.0.1
/etc/sane.d/magicolor.conf-
/etc/sane.d/magicolor.conf-### USB: format is "usb" for automatic (libusb) discovery, based on USB IDs,
/etc/sane.d/magicolor.conf-###      or "usb <vendor ID> <device ID> to force the use of a particular

```

---

