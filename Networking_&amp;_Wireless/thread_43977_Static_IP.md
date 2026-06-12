---
title: "Static IP"
date: 2005-06-24
forum: Networking &amp; Wireless
---

### Post by spacemonkey on 2005-06-24
I've got a server install of Ubuntu with fluxbox installed for my WM, and very few other programs.  I didn't want to install GDM or Gnome as it's an old computer without much power.  I'm using it for a small server, and I know I should know how to do this without the GUI tools, but I for the life of me cannot figure it out.  How do I make it have a static IP.  I can set the IP manually using 
```
sudo ifconfig -a eth0 <IP> netmask <netmask> 
``` 
and the gateway manuall by using 
```
sudo route add default gw <default gateway>
``` 
but everytime I reboot, a different IP gets assigned via DHCP.  The IP I'm trying to used is reserved for the computer, I just can't get it to stick after a reboot.  Any suggestions?

---

### Post by eskaypey on 2005-06-24
Look in /etc/network/interfaces

It should look something like --- 

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1

---

### Post by spacemonkey on 2005-06-24
aha, there it is.  all it had was:

iface eth0 inet dhcp

I didn't know about that file.  I changed it to static and entered the correct values.  Thanks for the help.

---

