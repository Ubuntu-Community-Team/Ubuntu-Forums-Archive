---
title: "Help: static vs. DHCP"
date: 2005-07-02
forum: Networking &amp; Wireless
---

### Post by skirkpatrick on 2005-07-02
Okay, this is weird.  Everything works fine when this machine is setup for DHCP.  However, if I assign a static IP and reboot, the startup tells me that it can't connect to the NTP server or a local server I have that I automount with fstab.  After the machine finishes booting, I can go into a console and "sudo mount -a" and everything is fine.  Why doesn't it like the static IP at bootup?  The appropriate section of /etc/network/interfaces is:
> 
# The primary network interface
auto eth0
iface eth0 inet static
broadcast 192.168.0.255
address 192.168.0.110
netmask 255.255.255.0
gateway 192.168.0.1


---

### Post by skirkpatrick on 2005-07-05
^^bump^^

Anybody got a thought?  Correct or otherwise? :)

---

### Post by thechitowncubs on 2005-07-05
[QUOTE=skirkpatrick]^^bump^^

Anybody got a thought?  Correct or otherwise? :)[/QUOTE]
 we need information about your network setup not just the computers

---

### Post by skirkpatrick on 2005-07-05
Okay, how's this:
This computer is connected to a Linksys WRT54G and is configured as a router with the cable modem connected to it.  The automount in fstab is to a Samba share on another machine.  This machine is accessed in fstab with the machine's name, though that name doesn't appear in a DNS.  I'm not sure if my machine is picking up the server's name through Samba or what.  But the NTP connection during bootup doesn't happen when it's configured for static IP.

If this isn't what you're looking for, let me know what you want.

---

### Post by manicka on 2005-07-05
[QUOTE=skirkpatrick]

Anybody got a thought?  Correct or otherwise? :)[/QUOTE]

Probably a silly question but does your router does use 192.168.0.* for it's addresses? 

Some use 10.1.1.*

---

### Post by skirkpatrick on 2005-07-05
The router is configured to hand out DHCP addresses in the range 192.168.0.200 - 192.168.0.250.  It uses NAT to hide my network.

---

