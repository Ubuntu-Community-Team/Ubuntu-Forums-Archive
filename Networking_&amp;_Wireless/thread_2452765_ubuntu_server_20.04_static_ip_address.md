---
title: "ubuntu server 20.04 static ip address?"
date: 2020-10-28
forum: Networking &amp; Wireless
---

### Post by josephchrzempiec on 2020-10-28
Hello i have been trying to figure out how to setup a static ip address on ubuntu server 20.04 i know it is different from the desktop version. I'm not a programmer but i'm learning. I tried to look over online for it and got confused on where to add the information into getting a static ip address. Can someone please help me and point me in the right direction where can i add a static ip address please?


Joseph

---

### Post by TheFu on 2020-10-28
An example:
```
network:
    version: 2
    renderer: networkd
    ethernets:
        **ens3**:
            addresses:
            - **172.22.22.90/24**
            dhcp4: false
            dhcp6: false
            gateway4: [B]172.22.22.1
[/B]            nameservers:
                addresses: [ "**1.1.1.1**", "**1.0.0.1**" ]
                search: []
```
The indentation is important. Don't use {tabs}. Ensure the things that I've lined up above are lined up in your file too.  1 space off the alignment level and it won't work.  Don't worry if you use 2 or 4 or 10 spaces for each *level*. That isn't important, but be 100% consistent.
Change the stuff that is "**bold**" for your needs/network.

The ;location and name of the file is:
```
$ ls /etc/netplan/*
/etc/netplan/01-ens3-static.yaml
```
Just the 'yaml' at the end matters.

After the file is created, run these commands:
```
sudo netplan generate
sudo netplan apply --debug
```
May need to restart the networking service too ... or reboot. In general, rebooting a Unix system really shouldn't be needed.
I don't have any static IPv6 addresses and because we aren't ready to secure IPv6, we simply block all that traffic on the network.

---

### Post by josephchrzempiec on 2020-11-04
Hello thank worked perfectly thank you.


Joseph

---

### Post by TheFu on 2020-11-04
Please mark this thread as solved to help the community out - faster to search for SOLVED in a thread metadata.  There's a "Thread Tools" button near the top.

---

