---
title: "IP Configuration"
date: 2016-01-25
forum: Networking &amp; Wireless
---

### Post by jerry60 on 2016-01-25
I am brand new to Linux and we had somebody at a PC shop configure a Ubuntu machine with Samba to see if we would like it instead of our current database server. When he configured Samba before he installed the GUI he put the static IP as 192.168.2.133 and I have tried multiple commands and played with the GUI to try to change it to 192.168.1.133 and it keeps telling me SIOCSIFFLAGS1: Operation not permitted. He recommended I just reinstall the whole thing and start from scratch, but my boss would prefer I did not do that. I apologize if I broke any forum rules!

---

### Post by Bucky Ball on 2016-01-25
*Thread moved to **Networking & Wireless**.*

Welcome. What gui did you play with? What machine, Ubuntu release, flavour? Are you talking about the computer's static IP, the router's, some setting in Samba ...

Hard to figure out how to help with what you've got here. For clarity, you can't change the static IP on a Ubuntu machine?

---

### Post by jerry60 on 2016-01-25
We are using Ubuntu 15.10 and the server software is Gadmin-Samba 0.3.2. I need to change the IP address of the server to get off the 192.168.2.133 and change it to 192.168.1.133. He configured it on the .2.133 network before installing the GUI so the tech who set it up thinks its just stuck.

---

### Post by chili555 on 2016-01-25
> He recommended I just reinstall the whole thing and start from scratch, but my boss would prefer I did not do that. Old Doc Chili would prefer not, as well. There is very little that a mortal man or woman did to an Ubuntu computer that other mortal women and men can't put right!

Please click the Network Manager icon and select 'Edit Connections.'  [http://i.stack.imgur.com/dbgXx.jpg](http://i.stack.imgur.com/dbgXx.jpg)

Is that where the static IP address is configured? Can you change it and also change the gateway?

Please open a terminal Ctrl+Alt+t and do:```
cat /etc/network/interfaces
```Is that where the address is configured? Something like:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.100
netmask 255.255.255.0
gateway 10.0.0.1
dns-nameservers 10.0.0.1
```If so, simply edit the file:```
sudo gedit /etc/network/interfaces
```Use nano or kate or leafpad if you don't have the text editor gedit. Make your needed changes; in this case, to the address, gateway and dns-nameservers.

Proofread carefully, save and close the text editor. Restart the interface:```
sudo ifdown eth0 && sudo ifup eth0
```Post back any questions, errors, warnings, etc. and we'll be happy to help.

EDIT: If you are using 15.10, then the interface is probably not eth0. Check and substitute:```
ifconfig
```It is probably enp2s0 or some such.

---

### Post by jerry60 on 2016-01-25
> **chili555 said:**
> Old Doc Chili would prefer not, as well. There is very little that a mortal man or woman did to an Ubuntu computer that other mortal women and men can't put right!

Please click the Network Manager icon and select 'Edit Connections.'  [http://i.stack.imgur.com/dbgXx.jpg](http://i.stack.imgur.com/dbgXx.jpg)

Is that where the static IP address is configured? Can you change it and also change the gateway?

Please open a terminal Ctrl+Alt+t and do:```
cat /etc/network/interfaces
```Is that where the address is configured? Something like:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.100
netmask 255.255.255.0
gateway 10.0.0.1
dns-nameservers 10.0.0.1
```If so, simply edit the file:```
sudo gedit /etc/network/interfaces
```Use nano or kate or leafpad if you don't have the text editor gedit. Make your needed changes; in this case, to the address, gateway and dns-nameservers.

Proofread carefully, save and close the text editor. Restart the interface:```
sudo ifdown eth0 && sudo ifup eth0
```Post back any questions, errors, warnings, etc. and we'll be happy to help.

EDIT: If you are using 15.10, then the interface is probably not eth0. Check and substitute:```
ifconfig
```It is probably enp2s0 or some such.


You are 100% correct on this solution I found it on google right before I checked back here. Thank you so much for the fast responses and excellent help!
Link for anyone interested (or just use solution above): [http://www.tecmint.com/set-static-ip-address-in-ubuntu-15-10-server/](http://www.tecmint.com/set-static-ip-address-in-ubuntu-15-10-server/)

---

### Post by Bucky Ball on 2016-01-25
If that worked, please see the first link in my signature. Good luck.

---

