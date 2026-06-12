---
title: "How to properly set up ethernet interfaces"
date: 2021-12-21
forum: Networking &amp; Wireless
---

### Post by tc2020 on 2021-12-21
Hello,

My device has two ethernet interfaces eth0 and eth1. I would like to assign static IP addresses to them so that the ports/interfaces come up automatically on system power on and reboot. This is on Ubuntu server 20.04.

Currently eth0 has its IP auto assigned with DHTP set in /boot/firmware/network-config file. Is this where I make changes for my requirements above or there are other config files that I need to edit?. Also, is there a document that talks about the syntax used in network-config file?

Thanks.

---

### Post by TheFu on 2021-12-21
Use netplan files. During the installation, there are questions about the ethernet interfaces and static IP setups in the 20.04.3 server installer (I just used it a few days ago).  And finally, they fixed the interface to prevent bogus entries which easily could have been solved by putting gray example text in the textentry box to be overwritten.  Alas, they just wait for bad entries and provide a correction error message instead.

There are lots of netplan example files posted in these forums. Netplan files go in /etc/netplan/.  I typically use a different file for each NIC, but not each port.  Since you are on a server, use **man -k netplan** to see the documentation.  Sadly, the early examples in the manpage don't provide the most common or even complete examples. It isn't until 
> This is an example of a static-configured interface with multiple IPv4 addresses and multiple
line that the next example is actually a complete file.  Netplan uses YAML and is extremely space-indentation specific. Don't use tabs, ever.

I'm not sure what DHTP is and doubt that  /boot/firmware/network-config  is used by Ubuntu, but perhaps it gets used by some specialized ubuntu embedded versions?  I've never used it on normal x86 servers, ever.

If you are trying to install on a non-amd64-x86 system, that is critical information to always, always, include in the question post.  I don't have a /boot/firmware directory at all.

---

### Post by tc2020 on 2021-12-21
The file /boot/firmware/network-config actually gets used by Ubuntu  (server 20.04 LTS 64-bit version). The default file has the following  content:

```
# This file contains a netplan-compatible configuration which cloud-init
# will apply on first-boot. Please refer to the cloud-init documentation and
# the netplan reference for full details:
#
# https://cloudinit.readthedocs.io/
# https://netplan.io/reference
#
# Some additional examples are commented out below

version: 2
ethernets:
  eth0:
    dhcp4: true
    optional: true
#wifis:
#  wlan0:
#    dhcp4: true
#    optional: true
#    access-points:
#      myhomewifi:
#        password: "S3kr1t"
#      myworkwifi:
#        password: "correct battery horse staple"
#      workssid:
#        auth:
#          key-management: eap
#          method: peap
#          identity: "me@example.com"
#          password: "passw0rd"
#          ca-certificate: /etc/my_ca.pem
```

If you uncomment "wifis" entries and enter proper values, wifi networking will work on bootup. Otherwise, it will not. Ubuntu looks up this file on bootup.

I looked up netplan.io link above but I cannot really relate what presented there and this config file in term of entries. It look like under "ethernets:" you can add "eth1" and its parameters. I just do not know what the valid entries are and also their syntax. And yes, I did see various indentation as well as dashes. 

There is only one file under /etc/netplan/50-cloud-init.yaml in default Ubuntu install. It has similar content:


```
# This file is generated from information provided by the datasource.  Changes
# to it will not persist across an instance reboot.  To disable cloud-init's
# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        eth0:
            dhcp4: true
            optional: true
    version: 2

```

I guess I have to dig deeper for more relevant info.

---

### Post by TheFu on 2021-12-22
[https://ubuntu.com/server/docs/network-configuration](https://ubuntu.com/server/docs/network-configuration) might provide more relevant details?
There are lots of examples on netplan.io - the official website for the netplan.

Config files in /etc/netplan/ are all I use with 20.04 and later systems - servers or desktops.

For example, a /etc/netplan/01-ens3-static.yaml on a desktop:
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
         addresses: [ 172.22.22.80,172.22.22.81 ]
         search: [thefu.lan]
```

With more NICs, I'd add another file just for that card, perhaps named 02-ens4-static.yaml, in the same directory. Then just run
```
sudo netplan generate
sudo netplan apply --debug
```
to have the files reparsed.  A reboot does the same thing.

Want more IPs on the same NIC?  Add another line just below the other one:
```
          - 172.22.22.[COLOR="#FF0000"]4[/COLOR]/24
```
I don't use IPv6 and actually have all the systems and firewalls setup to block it here. I'm just not ready for it.

Netplan isn't so bad, but it definitely was change for the sake of change. Nothing of any value seems to have been added by removing the old ifupdown methods.  They converted from a layout noobs disliked to a layout that noobs and experts dislike. Plus, it took a few years to mature to the point where non-trivial networking setups are supported by netplan.  I bet someone will claim that YAML is better for script parsing - perhaps. But it isn't like we don't have great parsers for the inifile format used by the old "interfaces" files. YAML is very picky. That's good and bad.

---

### Post by tc2020 on 2021-12-23
I created two files (and no other files under /etc/netplan directory), as follows:

/etc/netplan/01-xx_eth0-static.yaml
```
network:
   version: 2
   renderer: networkd
   ethernets:
      eth0:
         addresses:
            - 192.168.0.110/24
         gateway4: 192.168.0.1
```


/etc/netplan/02-xx_eth1-static.yaml
```
network:
   version: 2
   renderer: networkd
   ethernets:
      eth1:
         addresses:
            - 192.168.0.111/24
         gateway4: 192.168.0.1
```

It works after running sudo netplan generate and apply. 
Questions:
1). If I want eth1 to be on a different network,say 192.168.1.xxx, what entries do I have to add to the file for routing?. In this case, eth0 is my WAN/internet and eth1 is internal/isolated LAN.
2). Are there any problems if I just add empty placeholders for nameservers search suffix and IP addresses, like below:

```
network:
   version: 2
   renderer: networkd
   ethernets:
      eth0:
         addresses:
            - 192.168.0.110/24
         gateway4: 192.168.0.1
         nameservers:
            search: [ ]
            addresses: [ ]
```

3). What are the pro's and con's for having only one yaml file for both eth0 and eth1?.

Thanks.

---

### Post by TheFu on 2021-12-23
I don't know. Sorry.
I'm just providing practical solutions in this thread.

If you aren't really good with IPv6, I'd strongly suggest blocking it AND blocking the IPv6-over-IPv4 tunnels.  There are just so many ways for bad guys to have much more access than we expect because the mindset for IPv6 security doesn't follow what most non-guru network people believe.  I started blocking it after attending an offensive security training class on IPv6.

---

