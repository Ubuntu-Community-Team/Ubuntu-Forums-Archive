---
title: "Setting up WPA on a WAP on Ubuntu Server"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by porterusaf on 2008-04-16
Ok so I've got a WAP setup on my atheos based card on my Ubuntu Server. No problems there.

My problem is trying to get some sort of WEP encryption setup.... I tried using WPA, but can't get the /etc/network/interfaces setup correctly. This is what my file looks like...

```
     # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.44
        netmask 255.255.255.0
        network 192.168.1.1
        broadcast 255.255.255.255
        gateway 192.168.1.1
pre-up iptables-restore < /etc/iptables.rules
post-down iptables-restore < /etc/iptables.rules



#Wireless Setup
auto ath0
iface ath0 inet manual

wpa-driver madwifi

#wireless-mode master
#wireless-essid bnxserver

wpa-ssid bnxserver
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-psk 62c59da32fcf88f0f5052cd85f70affa84a64cbe498e33396f321c6f15bfa8f8



auto br0
iface br0 inet static
        address 10.1.1.1
        network 10.1.1.0
        netmask 255.255.255.0
        broadcast 10.1.1.255
        bridge-ports eth1 ath0      
```


Any ideas??

This is what I get after running a restart with my current setup (I still need to add a line for master mode that works too...
```
 root@bnxserver:/home/porterusaf# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          ioctl[SIOCSIWMODE]: Invalid argument
Could not configure driver to use managed mode

Waiting for br0 to get ready (MAXWAIT is 32 seconds).

```

 I'm running out of ideas or places to look. I followed about every guide I could come up with. Thanks guys!

-Porter

---

### Post by porterusaf on 2008-04-17
bump for still looking for help...

---

