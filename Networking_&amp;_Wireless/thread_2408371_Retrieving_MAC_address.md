---
title: "Retrieving MAC address"
date: 2018-12-17
forum: Networking &amp; Wireless
---

### Post by ubuntini2 on 2018-12-17
Ok so of course I have googled several sources 
ie [http://www.coffer.com/mac_info/locate-unix.html](http://www.coffer.com/mac_info/locate-unix.html)

and they usually suggest entering the following in the terminal

$ifconfig -a

However in the returned results I don't see eth0 or HWaddr.

Can anyone help?

If I go to System>Preferences>Internet & Network>Network Connections

and then select the Ethernet TAB

I do see a Device entry with 2 different addresses toggled with a select drop down.
One starts with ***eno1*** and the other with ***enp5s0***

and then under that an empty entry for 'Cloned MAC address'

---

### Post by chili555 on 2018-12-17
The only thing that's constant in Linux is change. Because of predictable interface naming, in recent versions of Ubuntu, ethernet interfaces are no longer eth0.

In your case, you have two ethernet devices; one named eno1 and one named enp5s0.

Find the MAC addresses with the command:```
ip addr show
```Here is a redacted sample from my machine; addresses have been obscured:```

2: enp0s25: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether [COLOR="#FF0000"]xx:f7:28:ae:83:xx[/COLOR] brd ff:ff:ff:ff:ff:ff

```I have highlighted the MAC address.

Reference: [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

---

