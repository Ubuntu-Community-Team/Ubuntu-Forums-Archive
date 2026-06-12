---
title: "ethernet not working with kvm.."
date: 2019-11-12
forum: Networking &amp; Wireless
---

### Post by Furycd001 on 2019-11-12
HI Guys.. I'm following [**this tutorial**]("https://linuxconfig.org/install-and-set-up-kvm-on-ubuntu-18-04-bionic-beaver-linux") for setting up kvm on xubuntu 18.04.3 which is fully up-to-date. My problem is that I edit "/etc/network/interfaces" adding in my ethernet details, and then whenever I restart my ethernet is down and does not work, leaving me with only wifi. If I remove my ethernet details from the file (change enp4s0 to eth0 or anything else) and restart then ethernet starts working again as normal. Any suggestion or help appreciated. Here is my "/etc/network/interfaces" file....

```

# ifupdown has been replaced by netplan(5) on this system.  See
# /etc/netplan for current configuration.
# To re-enable ifupdown on this system, you can run:
#    sudo apt install ifupdown
auto lo br0
iface lo inet loopback

iface enp4s0 inet manual

iface br0 inet dhcp
    bridge_ports enp4s0

```

---

### Post by Furycd001 on 2019-11-12
The tutorial I was following was telling me how to incorrectly set up the bridge connections. Followed [**this tutorial**]("http://linuxtechi.com/install-configure-kvm-ubuntu-18-04-server/") and everything now works....

---

