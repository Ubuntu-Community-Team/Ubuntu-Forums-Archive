---
title: "Static internal ip on Ubuntu 18.04?"
date: 2020-02-15
forum: Networking &amp; Wireless
---

### Post by garyed on 2020-02-15
I used to have a static ip on my desktop with Ubuntui 16.04 & upgraded to 18.04 & it still worked fine. I just changed routers & my default gateway changed from 192.168.1.1 to 192.168.0.1
I figured it would just a matter of changing the 1 to a 0 in my network/interfaces file but that didn't work. After finding out about netplan I installed it but I only ended up with an empty directory no matter what I did. I can't find a way to get a .yaml config file in the /etc/netplan directory. I know I can create one but I don't know what parameters to use like "network, version, renderer " or whatever.  So my question is how do I generate a .yaml file automatically with the correct parameters or how can I find the correct parameters to create my own .yaml file?  Also is there anything else that I would need to do besides getting the correct settings on a .yaml file to have a static internal ip? Thanks for any help

---

### Post by TheFu on 2020-02-15
You have to manually create it, if you don't do a fresh install (I'm guessing).  

Use sudoedit.

Here is my 
/etc/netplan$ more 50-cloud-init.yaml 
```
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    renderer: networkd
    ethernets:
        ens3:
            addresses:
            - 172.22.22.90/24
            dhcp4: false
            dhcp6: false
            gateway4: 172.22.22.1
            nameservers:
                addresses: [ "1.1.1.1", "1.0.0.1" ]
                search: []
```

Indentation is absolutely critical, so best to copy/paste it, then change only the parts for the NIC device, gateway and IP/subnet.  Those nameservers are for cloudflare. They don't track anything, but it might be best to use a dnssec or dns-over-http solution these days.  I do on desktops.

I had to manually modify this file post-install. The 18.04 server installer didn't leave a working config. Booooo!

---

### Post by garyed on 2020-02-15
> **TheFu said:**
> You have to manually create it, if you don't do a fresh install (I'm guessing).  

Use sudoedit.

Here is my 
/etc/netplan$ more 50-cloud-init.yaml 
```
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    renderer: networkd
    ethernets:
        ens3:
            addresses:
            - 172.22.22.90/24
            dhcp4: false
            dhcp6: false
            gateway4: 172.22.22.1
            nameservers:
                addresses: [ "1.1.1.1", "1.0.0.1" ]
                search: []
```

Indentation is absolutely critical, so best to copy/paste it, then change only the parts for the NIC device, gateway and IP/subnet.  Those nameservers are for cloudflare. They don't track anything, but it might be best to use a dnssec or dns-over-http solution these days.  I do on desktops.

I had to manually modify this file post-install. The 18.04 server installer didn't leave a working config. Booooo!

Thanks for the help,
I'm not sure if I got the changes right so I'm going to post the results of ifconfig & then the new .yaml file. Here goes:
```
[CODE]
$ ifconfig
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.123  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::864e:c885:8cf5:b67f  prefixlen 64  scopeid 0x20<link>
        ether fc:aa:14:76:3e:af  txqueuelen 1000  (Ethernet)
        RX packets 273949  bytes 284291199 (284.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 101977  bytes 13795028 (13.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf7f00000-f7f20000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2054  bytes 224569 (224.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2054  bytes 224569 (224.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```[/CODE]  
.yaml file:
> 
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    renderer: networkd
    ethernets:
        eno1:
            addresses:
            - 192.168.0.129/24
            dhcp4: false
            dhcp6: false
            gateway4: 192.168.0.1
            nameservers:
                addresses: [ "1.1.1.1", "1.0.0.1" ]
                search: []


My other questions are:
1 - What do I name the .yaml file?
2 - Do I need to do anything else besides just putting that file in the /etc/netplan directory?

---

### Post by pcfan1234 on 2020-02-16
You can name that what you want,
e.g. use **01-netcfg.yaml**

There is no further configuration required.
Please notice that if you config your network using netplan you can't config this adapter in the graphical NetworkManager.
So I recommend keeping a .yaml file that configs only the use of NetworkManager if you are in another environment and like to use NetworkManager to easily config your network adapter.

---

### Post by TheFu on 2020-02-16
> **garyed said:**
>  
My other questions are:
1 - What do I name the .yaml file?
2 - Do I need to do anything else besides just putting that file in the /etc/netplan directory?

The name doesn't matter, provide netplan recognizes it.

There is a command to get netplan to reparse the files and reload the new config. I haven't looked it up in a few months and no netplan using systems are booted today.   
Google found this : [https://www.linux.com/tutorials/how-use-netplan-network-configuration-tool-linux/](https://www.linux.com/tutorials/how-use-netplan-network-configuration-tool-linux/)

pcfan1234's suggestion makes sense for laptops.  On my laptop, at home, I use a DHCP reservation to effectively have a static IP. When the machine is away from home, it uses whatever DHCP server connection is provided.  For servers and desktops, I purge network-manager and nm-* from the system.  I also purge nano and bluetooth stuff off all my systems. :)

Should point out that the example provided ignores IPv6.  I don't use IPv6. If you live in China or India, it is much more likely you can't ignore it.

---

