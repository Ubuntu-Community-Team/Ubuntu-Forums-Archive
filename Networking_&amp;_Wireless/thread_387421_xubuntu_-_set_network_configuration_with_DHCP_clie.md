---
title: "xubuntu - set network configuration with DHCP client"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by mbrando on 2007-03-18
Hi,

I have installed xubuntu 6.10 on a Gateway 9100. When I rebooted the system, after installation, it was not getting network settings via DHCP. So I ran these commands from the terminal with SUDO:

sudo ifconfig eth0 192.168.0.11 netmask 255.255.255.0 broadcast 192.168.0.255

sudo ifconfig eth0 up

sudo route add default gw 192.168.0.1

Then I went into the network tool through the GUI and set the name servers. It worked fine until I rebooted. Then I thought I should have just run dhclient from the terminal. That works too, but only for the time that the computer is on. Upon next power up I have to manually do some kind of network setup. Also since I ran the SUDO commands the GUI will not let me access the network tool via the GUI. I'm thinking that this is a permissions issue, but I do not know which file to look at.

Can anyone help me get this setup to automatically use DHCP? And on a lesser note allow me to use the network tool in the GUI? There may be time where DHCP is not available and a static or manaul address will have to setup.

Sincerely,
Mike
-- 
Mike Brandonisio
Tech One Illustration
 [www.techoneillustration.com](www.techoneillustration.com)

---

### Post by chili555 on 2007-03-18
I think the answer lies in your /etc/network/interfaces file. This section: ```
iface eth0 inet dhcp
```should look like this: ```
auto eth0
iface eth0 inet dhcp
```Then I believe it will start on boot. You can amend with sudo gedit. Don't forget to save.

Reboot and let us know.

---

### Post by lloyd_b on 2007-03-18
The key control file for networking is "/etc/network/interfaces".  If you add two lines to that file, it should automatically reconfigure based on DHCP:
```
auto eth0
iface eth0 inet dhcp
```

(Note: you'll need to do a "sudo nano" or "gksudo gedit" to change these files, as they're owned by root)

To set this for a static IP instead (using the addresses from your post):
```
auto eth0
iface eth0 inet static
   address 192.168.0.11
   netmask 255.255.255.0
   broadcast 192.168.0.255
   gateway 192.168.0.1
```

Finally, if you're not using DHCP, you'll need to manually set the nameserver.  This is done by editing the file "/etc/resolv.conf", and adding a line for each nameserver:
```
nameserver 192.168.0.1
```

A final useful trick.  The script "/etc/init.d/networking" can be used to stop/start/restart network functions:
```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
sudo /etc/init.d/networking restart

```

The GUI tools are primarily a front end for editing these files (and running the various programs needed, such as ifconfig and route).  If you know which files to edit, you're good to go even on a server that doesn't have a GUI.  Personally, I prefer to edit the files myself (but I'm biased, as I'm a long-time command-line junkie).

Lloyd B.

---

### Post by mbrando on 2007-03-18
Hi,

Thank you for the really fast response. I think this will fix my problem. :) 

The ubuntu community looks very active. I think I'll settle in here nicely.

Edited a few hours later:

Thanks again. It worked like charm.

Sincerely,
Mike
-- 
Mike Brandonisio
Tech One Illustration
[www.techoneillustration.com](www.techoneillustration.com)

---

