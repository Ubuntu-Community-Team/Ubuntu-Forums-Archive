---
title: "Ubuntu Server unable to connect to LAN"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by reverbtank on 2007-05-14
Hello all, 
I've got a small problem, any help would be appreciated.

I installed Ubuntu Server Edition 7.0.4 on an old PC, my plan being to turn it into a file server for the house.  Install went fine, but the installer was unable to grab an IP from my router, which is set to use DHCP.
I set it up manually by editing /etc/network/interfaces and adding these lines:
auto eth0
iface eth0 inet dhcp
However, it still did not work, even after bringing eth0 down then up and restarting network services.  
So then I attempted to assign a static IP to the server.  
My Belkin router's address is 192.168.2.1
Netmask 255.255.255.0
I added these lines to /etc/network/interfaces:
auto eth0
iface eth0 inet static
address 192.168.2.5
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.2.1
I then edited the hosts file to contain the line:
192.168.2.5              thearchive
And then added this line to hostname:
thearchive
Reboot, run ifconfig, has the IP address, but unable to see or be seen by anything on the network.
The router is a Belkin wireless router and I have a mac and a PC working fine with it.  
I'm sure it's something small I'm missing.

---

### Post by Ateo on 2007-05-14
You need samba server on that old box.

---

### Post by chili555 on 2007-05-14
> You need samba server on that old box.If you are connecting Windows to Linux, you do, but that's not apparent here, nor does it help you connect.

I don't think these:```
address 192.168.2.5
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.2.1
```Are consistent. I might agree the network is 192.168.2.0 and the broadcast is 192.168.2.255. Please try those and post back to let us know.

---

### Post by reverbtank on 2007-05-14
Thanks for the advice so far.  
I tried changing the network and broadcast addresses but still nothing.  
When I run route -n I get this:
Destination            Gateway                  Genmask            Flags          Metric     Ref    Use    Iface
192.168.2.0            0.0.0.0                     255.255.255.0    U                0             0        0        eth0
0.0.0.0                    192.168.2.1             0.0.0.0                UG              0             0        0        eth0

Not sure if this helps.  All internet access does work fine with Ubuntu Desktop LiveCD however.  
I'm going to grab the disk and see if I can figure out something from checking out the config files.

---

### Post by reverbtank on 2007-05-14
Alright, figured it out, it was a broken network cable.  Everything is peachy now.

---

