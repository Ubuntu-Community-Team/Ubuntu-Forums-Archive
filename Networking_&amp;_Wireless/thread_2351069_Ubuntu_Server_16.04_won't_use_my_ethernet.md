---
title: "Ubuntu Server 16.04 won't use my ethernet"
date: 2017-01-30
forum: Networking &amp; Wireless
---

### Post by chunkydrew2 on 2017-01-30
Before I began the install of my home file server with Ubuntu Server 16.04 LTS, I researched the install extensively. One of the things all the guides agreed on was that I should use a static IP address, rather than DHCP. As such, immediately after install, I edited the /etc/network/interfaces file, which now reads like this: (I'm not including any lines which are commented out with #)[INDENT]
auto eth0
iface eth0 inet static[/INDENT]
[INDENT=2]address: 192.168.2.100 (the static address I'm trying to set)
network: 192.168.2.0
netmask: 255.255.255.0
broadcast: 192.168.2.255
gateway: 192.168.2.1 (the address of my Belkin router)
[/INDENT]

When I do this and either restart the network or reboot the server, then run the ***ifconfig*** command, the results are still:
[INDENT]lo         link encap: local loopback[/INDENT]
[INDENT=2]inet address: 127.0.0.0    mask: 255.0.0.0
inet6 addr:     : :1/128  scope: Host
[/INDENT]

Why is my server ignoring the settings in the /etc/network/interfaces file? is there another file that I must edit also, to set this to ethernet and static? Could my ethernet card or cable be bad? And, can someone explain the loopback to me? I'm still a Linux newbie, and now I'm lost. Two weeks ago, everything seemed to be working, and I was able to read folders on the server in both Linux (Ubuntu 16.04 & 16.10, Mint 18.1, Fedora 25) and Windows 10. Now, nothing. Any ideas, anyone?  :o

---

### Post by gdesilva on 2017-01-30
Hi not sure how it is on Ubuntu Server, but in Ubuntu Studio 16.04LTS which I am using the configuration file used is located in /etc/NetworkManager and not in /etc/network. I would presume Ubuntu Server uses Network Manager as well but since I have not used server edition cannot be sure about this.


EDIT:

Looks like Ubuntu Server does not use NetworkManager files.

Check out the config on the [post]("https://ubuntuforums.org/showthread.php?t=2350870") in this forum - Do you have the loopback interface defined in your config?

A good explanation of the use of loopback interface can be found [here]("http://askubuntu.com/questions/247625/what-is-the-loopback-device-and-how-do-i-use-it").

---

### Post by chili555 on 2017-01-30
Your file is quite incorrect, however, we need to gather some data first before I propose a change. Please run and post:```
ifconfig -a
lspci -nnk | grep 0200 -A2
```I doubt that your ethernet interface is eth0.

---

### Post by Morbius1 on 2017-01-31
> Two weeks ago, everything seemed to be working, and I was able to read  folders on the server in both Linux (Ubuntu 16.04 & 16.10, Mint  18.1, Fedora 25) and Windows 10. Now, nothing. Any ideas, anyone?
I don't know the answer to your question but until you get this fixed you might be interested to know that every operation system you mentioned can speak mDNS - including Win10.

So if your host name on the server is say ... serverhostname .. then the clients can access that server with that name and a ".local' at the end:

In nautilus, nemo, dolphin it's:
```
smb://serverhostname.local
```
And in WIn10's explorer it's:
```
\\serverhostname.local
```
This serverhostname.local mechanism should work for anything not just samba like a ping, etc..

You just have to make sure that avahi-daemon is running and port 5353 is open of the Ubuntu server.

---

