---
title: "interface configuration problem"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by mtime2457 on 2007-08-22
Problems configuring an interface with a static address.

From my understanding in order to assign a static ip you have to edit the /etc/network/interfaces directory.  Once this is complete you would save the changes (in this example I'm using pico) by typing Ctrl O and then Ctrl X.  You would then bring down the interface by typing ifdown eth0 and then bring up the interface by typing ifup eth0.....  This is where we are encountering problems! 

right now the interface directory looks like this;

iface eth0 inet static

address 198.x.x.x
netmask 255.255.255.0
broadcast 198.x.x.x
gateway 198.x.x.x
dns-nameserver 198.x.x.x 4.x.x.x

no entry for a secondary interface card since this server right now is only connected through one card.

At first we were able to bring down the interface by typing ifdown eth0 but we were not able to bring the interface back up by typing ifup eth0.  We received an error stating that the interface was not configured.  Now we can't bring down or up the eth0....Not actually sure what the problem is, any feedback would be greatly appreciated.

---

### Post by bernied on 2007-08-22
Try:
```
sudo /etc/init.d/networking restart
```
And you should really have an entry for the lo device in the /etc/network/interfaces file. Mine looks like this:
```
# cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
```

---

### Post by A$h X on 2007-08-22
Not sure about dapper drake but on feisty 7.04 clicking on the network icon in the top right brings up the NIC dialog. Select the wired connection and click properties. Thne just enter your desired static IP, subnet and gateway addresses. Saves you from getting down and dirty with sudo nautilus and the like.

---

### Post by zeger82 on 2007-08-23
I am having this issue as well. 
I tried restarting the server but that did not help.

When I try to restart networking I get the error below

```
# /etc/init.d/networking restart
SIOCADDRT: Network is unreachable
Failed to bring up eth0

```
 
My /etc/network/interfaces file looks like this:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address     192.168.xx.xx
netmask    255.255.255.0
broadcast 192.168.xx.255
gateway   192.168.xx.xx

---

### Post by zeger82 on 2007-08-23
Well I figured out the issue on my system.

The problem we had on the system was the netmask was incorrect.  Once I changed the netmask I was able to restart my networking with 
"# /etc/init.d/networking restart" and after that it worked fine.

---

### Post by mtime2457 on 2007-08-24
We too were able to fix our problem by changing out netmask.

---

