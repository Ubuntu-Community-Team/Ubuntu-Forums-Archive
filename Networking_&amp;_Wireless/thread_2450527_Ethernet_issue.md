---
title: "Ethernet issue"
date: 2020-09-15
forum: Networking &amp; Wireless
---

### Post by hmiersch on 2020-09-15
Every time I boot or restart my pc, Ethernet doesn't work because for some unknown reason the default gateway is set to 0.0.0.0 instead of 192.168.0.1. Then I have to go to settings -> network and turn the network off and on again, and then Ethernet works normally - until the next time I boot or restart the pc.
What's going on? Why is it doing that? What can I do about it?

---

### Post by Skaperen on 2020-09-15
what instructions have you tried, so far, to configure a gateway address?

---

### Post by hmiersch on 2020-09-15
I tried the settings app, of course, and I tried editing config files. But I can't find anything that says gateway 0.0.0.0
If you need the names of those config files, I'd have to check.

---

### Post by TheFu on 2020-09-15
dhcp?  check your dhcp server. It might be the router.

---

### Post by hmiersch on 2020-09-16
i don't use DHCP, i set my IP addresses manually. it is set to use manual addresses. IP 192.168.1.64, subnet mask 255.255.255.0, router (gateway) 192.168.1.1, DNS server 192.168.1.6 (a raspberry pi running pihole)

but every time i boot, the router IP shows up as 0.0.0.0. turn the network off and on gain, and it works until the next boot.

---

### Post by TheFu on 2020-09-16
please post the config file where those settings are stored.

---

### Post by hmiersch on 2020-09-16
the problem is, none of the files in /etc that i checked had any IP info. where should i look?

---

### Post by TheFu on 2020-09-16
> **hmiersch said:**
> the problem is, none of the files in /etc that i checked had any IP info. where should i look?

Where do you make those settings if not in a config file?

---

### Post by hmiersch on 2020-09-16
I remember editing some config files with ip addresses, bug I don't remember which files. There was something about networkmanager and netplan, but those files don't have any ip info. I have to say I'm confused... does the settings app overwrite those files?

---

### Post by TheFu on 2020-09-16
> **hmiersch said:**
> I remember editing some config files with ip addresses, bug I don't remember which files. There was something about networkmanager and netplan, but those files don't have any ip info. I have to say I'm confused... does the settings app overwrite those files?

I don't use any "settings app", sorry. About the 3rd thing I do on my systems after purging nano and setting up the sudoers file the way I like is to purge anything that looks like network-manager or nm-*  I remember fighting with network-manager years ago and losing the battle, so I use the nuclear option to win the war every time.  Same for resolvconf and systemd.resolved - purged. Don't want them screwing with my network settings.

There are lots of examples of simple netplan files here, assuming it is wired, not wifi.

$ more /etc/netplan/01-ens3-static.yaml 
```
network:
  version: 2
  renderer: networkd
  ethernets:
     ens3:
       addresses:
          - 172.22.22.3/24
       dhcp4: false
       dhcp6: false
       gateway4: 172.22.22.1
       nameservers:
         addresses: [ "172.22.22.80", "172.22.22.81" ]

```
Here's one for my 20.04 desktop. You'll need to change the device name, IP/network, gateway and nameservers, almost certainly. Don't us tabs, only spaces. The levels must be consistent. Align vertically the stuff exactly as I've done here.  2, 3, 4, 5, spaces for each level are fine, just be consistent.

After editing, run 
```
sudo netplan generate
sudo netplan apply --debug
```
to make it active, then restart the network service, if needed.

Good luck.

---

