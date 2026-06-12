---
title: "Everything to ok till I tried to use static ip"
date: 2015-07-04
forum: Networking &amp; Wireless
---

### Post by marta2 on 2015-07-04
Hi everybody,
First time I've installed Ubuntu 14.04.2 server. I had some problems with the Raid configuration, but finally I could solve them.
Then I tried to change from dynamic to static ip and began the problems that I can't solve. I've been doing a lot of things, but something is missing or wrong. Could you help me?

I've modified this to files: 
- /etc/network/interfaces:
  auto lo
  iface lo inet loopback
  auto eth0
  iface eth0 inet static
  address 192.168.1.25
  netmask 255.255.255.0
  network 192.168.1.0 (*)
  broadcast 192.168.1.255 (*)
  gateway 192.168.1.1
  (*) I'm not sure if they are necessary

- /etc/resolv.conf
  nameserver 80.58.61.250
  nameserver 80.58.61.254
  I've seen that somebody configure dns server in interfaces file

After this I execute sudo /etc/init.d/networking restart
I ifconfig doesn't show any play for eth0 and, of course, there is not internet connection.

Does anybody knows what happens?
Thanks very much

---

### Post by nlee2 on 2015-07-04
If you are not familar with network configuration files you could try nmtui networkmanager.

---

### Post by marta2 on 2015-07-04
Thanks nlee2. I'm not familiar with network configuration in Ubuntu, in Windows yes. I'm new with Ubuntu and I don't know what's nmtui network manager. I'm going to search information about it.
I'll inform if this solve or not my problem

---

### Post by nlee2 on 2015-07-04
nmtui is actually a very easy text based tool to configure IP address. It should be already installed on Ubuntu server. Open a command shell and type nmtui. You would edit your connection and set it to manual for static ip.

The following doc is for rhel but applies to ubuntu as well.

[http://networknuts.net/linuxblog/rhel7-configuring-ip-addresses/](http://networknuts.net/linuxblog/rhel7-configuring-ip-addresses/)

---

### Post by chili555 on 2015-07-04
Please try:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.25
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 80.58.61.250 80.58.61.254
```Restart the interface:```
sudo ifdown eth0 && sudo ifup -v eth0
```Check:```
ifconfig
ping -c3 www.ubuntu.com
```Please carefully check and verify your DNS nameserver addresses; neither are reachable for me.

---

### Post by marta2 on 2015-07-05
Thanks very much. Finally I've reinstalled again Ubuntu 14.04.2 server again, and then I've applied what you have said. Now, I've got static ip.
Thanks, thanks, thanks

---

### Post by chili555 on 2015-07-05
> **marta2 said:**
> Thanks very much. Finally I've reinstalled again Ubuntu 14.04.2 server again, and then I've applied what you have said. Now, I've got static ip.
Thanks, thanks, thanksGlad it's working! Please use thread tools to mark Solved. The searchers will appreciate it.

---

