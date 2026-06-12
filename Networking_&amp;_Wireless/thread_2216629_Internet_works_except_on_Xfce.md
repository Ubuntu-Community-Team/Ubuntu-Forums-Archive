---
title: "Internet works except on Xfce"
date: 2014-04-12
forum: Networking &amp; Wireless
---

### Post by Justin_Frahm on 2014-04-12
I have Ubuntu 12.04.4 LTS server installed on an old desktop and installed Xfce so that I could remote into a desktop environment if I needed to (this does not run by default - I only get a command line unless I am using a VNC connection). The internet seems to work fine over the command line; I can wget, access Ubuntu repositories, ssh and use tightVNC with no issues. The problem is, when I do use VNC, which starts Xfce, it says that networking is disabled *while I maintain a vnc connection*! Why does Xfce not seem to see the network? You can probably tell from my description of this problem that I am by no means a linux expert so I'm not sure what all other information to provide.

This is what my /etc/network/interfaces says:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp


# Set primary to static - results in unmanaged network device...
#auto eth0
#iface eth0 inet static
#address 192.168.1.99
#netmask 255.255.255.0
#gateway 192.168.1.1

```

Thanks in advance!

---

### Post by chili555 on 2014-04-13
> when I do use VNC, which starts Xfce, it says that networking is disabled while I maintain a vnc connection!I expect it's because Network Manager starts and takes over when Xfce starts. NM is waiting for you to click its icon and direct it to connect. Confirm:```
ps aux | grep -i network
```I would suggest you remove it:```
sudo apt-get purge network-manager*
```I also suggest you revert to a static IP address:```
# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
#auto eth0
#iface eth0 inet dhcp


auto eth0
iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
```Reboot and tell us the result.

---

### Post by Justin_Frahm on 2014-04-13
```
ps aux | grep -i network
```
 gives:
```
root      1116  0.0  0.4 158844  4972 ?        Ssl  Apr12   0:00 NetworkManager
1000      4302  0.0  0.0   9336   908 pts/0    S+   12:56   0:00 grep --color=auto -i network
```

regardless of whether a vnc connection is open (starting up xfce) or not.

I set interfaces to a static connection as suggested then purged network-manager and rebooted.

btw, confirming network-manager is gone:
```
ps aux | grep -i network
```
now gives:
```
1000      1759  0.0  0.0   9332   904 pts/0    S+   20:11   0:00 grep --color=auto -i network
```

Opened up a VNC connection and the browser can access the web! How about that!

So... what is the deal with network-manager that seems to be fixed now?

---

