---
title: "I Lost my Network Adapter I can get it back but....."
date: 2019-06-04
forum: Networking &amp; Wireless
---

### Post by nambi on 2019-06-04
I use windows hyper V within this I have Ubuntu Server 18.4 LTS

When I reboot I dont' have any network adapters in the system.

I then run 
dhclient eth0 

this brought back my NIC, but now every time I reboot I need to run this  command to get my NIC back, Anyway i can have the NIC back permanently  and working even after reboot? I tried to run apt-get install  network-manager and it installed but this didn't fix my issue. The  machine will still reboot without the NIC until I run dhclient eth0  Using Ubuntu Server 18.04

When I reinstalled Ubuntu on the same Hyper V server using the same NIC card I dont' have any issues, I don't want to lose my old server and all the settings and data or I would have reformatted. 

Thank you

---

### Post by SeijiSensei on 2019-06-04
Give the adapter a static address so it won't need to use DHCP.

---

### Post by nambi on 2019-06-05
I've tried this,i changed yaml file but it doesn't' work unless i did this wrong.

network:
  version: 2
  renderer: networkd
  ethernets:
    etH0:
      dhcp4: no
      dhcp6: no
      addresses: [192.168.1.110/24, ]
      gateway4:  192.168.1.1
      nameservers:
              addresses: [8.8.8.8, 8.8.4.4]

---

### Post by kpatz on 2019-06-05
I think indentation matters on yaml files.  Please post inside ```
 tags next time.

It should look like this:
[code]network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      dhcp4: no
      dhcp6: no
      addresses: [192.168.1.110/24]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
```

etH0: should be eth0:.
You don't need the comma after /24 in the addresses line.

Also, make sure the file is named something like /etc/netplan/01-netcfg.yaml.  The directory is important, and I think the digits at the front are as well (it tells netplan what order to execute the files, if more than one exist).

Also, if you set dhcp4 on, will you get an ip that way?  Dynamic IPs are always easier to keep track of than static ones.  I only use static IPs on servers.  If you have a router handing out dhcp addresses, use an IP outside the range the router hands out for static IPs.  For example, 192.168.1.10 through 99, if the router hands out IPs at 100+.

The command **sudo netplan try** will validate your yaml file and tell you if it has errors.  If it's good, **sudo netplan apply** should apply the changes.

---

### Post by nambi on 2019-06-05
Thank!!! it worked. 

A few things that fixed it etH to eth:

but i had to remove the "." after the ":" 

ever since the last update this stopped working, thanks for helping me out.

---

