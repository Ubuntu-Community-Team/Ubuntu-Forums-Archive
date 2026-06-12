---
title: "Router assign dynamic IP to static IP ubuntu server"
date: 2019-09-03
forum: Networking &amp; Wireless
---

### Post by caravaggio971 on 2019-09-03
I run a wired linux server (ubuntu 18.04) with static ip attached to my netgear R6300 (i'm attaching the network config file). Router's IP is 192.168.50.1. PC has static IP (192.168.50.100).

DHCP on router is enabled with ip's range starting at 192.168.50.150-200.


Every now and then the router renew the ips and assign a random IP to my server that hence cant be reached. I don't understand where the problem is. Hope someone can help.

yaml file

> 
network:
  version: 2
  renderer: networkd
  ethernets:
        enp3s0:
            dhcp4: no
            dhcp6: no
            addresses: ['192.168.50.100/24']
            gateway4: 192.168.50.1
            nameservers:
                addresses: [1.1.1.1,8.8.8.8]
                search: [terraveler.com]

hosts file

> 127.0.0.1       localhost127.0.1.1       ubuntu-standard

The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


[ATTACH=CONFIG]283924[/ATTACH]

---

### Post by texpat on 2019-09-03
Some routers give you the possibility to assign a certain IP to a device MAC. You have to dig through your router's options to see if has that feature. If it does offer that option, the dhcp server will always assign the IP address you entered to the device with the MAC address you entered the IP for.

---

### Post by chili555 on 2019-09-03
Will you please amend your yaml file to:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      addresses:
        - 192.168.50.100/24
      gateway4: 192.168.50.1
      nameservers:
          search: [terraveler.com]
          addresses: [1.1.1.1, 8.8.8.8]

```Netplan is very particular about spacing and indentation, please proofread carefully twice. Follow with:```
sudo netplan generate
sudo netplan apply
```Is there any improvement?

---

### Post by caravaggio971 on 2019-09-03
Thanks for your reply. I reserved the IP and MAC on my router and I was having the same problem. I'm wondering if there some conflict. I once installed on top of Ubuntu server Regolith wich is a distro based on ubuntu 18.04 as well. I purged it but I'm wondering if Regolith comes with the old network manager configuration that overwrites the yaml file.

---

### Post by caravaggio971 on 2019-09-03
> **texpat said:**
> Some routers give you the possibility to assign a certain IP to a device MAC. You have to dig through your router's options to see if has that feature. If it does offer that option, the dhcp server will always assign the IP address you entered to the device with the MAC address you entered the IP for.

Thanks for your reply. I reserved the IP and MAC on my router and I was having the same problem. I'm wondering if there some conflict. I once installed on top of Ubuntu server Regolith wich is a distro based on ubuntu 18.04 as well. I purged it but I'm wondering if Regolith comes with the old network manager configuration that overwrites the yaml file.

---

### Post by caravaggio971 on 2019-09-03
> **chili555 said:**
> Will you please amend your yaml file to:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      addresses:
        - 192.168.50.100/24
      gateway4: 192.168.50.1
      nameservers:
          search: [terraveler.com]
          addresses: [1.1.1.1, 8.8.8.8]

```Netplan is very particular about spacing and indentation, please proofread carefully twice. Follow with:```
sudo netplan generate
sudo netplan apply
```Is there any improvement?

I've added a couple of screenshot taken few minutes ago. One reports a dynimic IP .161 and the device name is ubuntu standard. The other one after rebooting has changed into 100 as per the YAML file and the name is UBUNTU. now I dont understand where this second name comes from. Any idea?

I pasted your yaml file I'll let you know if the situation improves. 
Thank you.
D.

---

