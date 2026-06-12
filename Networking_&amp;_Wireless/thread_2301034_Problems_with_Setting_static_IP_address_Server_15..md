---
title: "Problems with Setting static IP address Server 15.10"
date: 2015-10-30
forum: Networking &amp; Wireless
---

### Post by matt_smith2 on 2015-10-30
Hi All,

Totally new to Ubuntu and Linux, I am trying to set up an Ubuntu server which is running on a Generation 1 Hyper-V machine on my 2012 R2 server.  From this [web page]("https://help.ubuntu.com/lts/serverguide/network-configuration.html") I ran the command sudo nano /etc/network/interfaces ammending the file to look like this:

auto eth0
iface eth0 inet static
address 192.168.0.210
netmask 255.255.255.0
gateway 192.168.0.1

Saved and exited and ran the command systemctl restart if@eth0

Then using ifconfig it still shows eht0 as having a DHCP address.  Rebooting the server yielding the same result. 



 I've tried googling this but have not been able to find anything that has helped me to resolve this issue.  I would like to assign a static IP to the server as I intend using it as a PXE server eventually.  Anyu help and suggests will be gratefully appreciated.

Thanks
Matt

---

### Post by howefield on 2015-10-30
Hello matt_smith2 and welcome to the forums, your thread has been moved to the "*Networking & Wireless*" forum where it will be more likely be seen by the networking gurus.

---

### Post by wyliecoyoteuk on 2015-10-30
Works here, 
It should look like this:

# This file describes the network interfaces available on your system
# and how to activate them. for more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.210
netmask 255.255.255.0
gateway 192.168.0.1

However, Hyperv does set network parameters, so that might have an effect.

---

### Post by wyliecoyoteuk on 2015-10-30
Just checked on a HyperV guest here, no real difference, except the source line is missing, and these 2 lines have been added:
broadcast 192.168.0.255
network 192.168.0.0

---

### Post by wyliecoyoteuk on 2015-10-30
Is there anything in /run/network/ifup.eth0 ?

---

### Post by matt_smith2 on 2015-10-30
Hi Wylie,

Thank you for your suggestions, I shall have to check when I get home as that is where I am testing before moving to a live environment.

---

### Post by matt_smith2 on 2015-10-30
Bizarrely enough when trying again tonight with with the static IP address I got it to work.  Not too sure why it would work now yet wouldn't yesterday?  But anyway happy its working, have rebooted 5 times and the server has kept its IP so all is good.

[ATTACH=CONFIG]265272[/ATTACH]

---

