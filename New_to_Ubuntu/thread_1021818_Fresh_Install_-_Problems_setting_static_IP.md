---
title: "Fresh Install - Problems setting static IP"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by ZhiZaki on 2008-12-26
Alright, I'm an old time-y Slackware user who installed Ubuntu today. Everything seems fine, until it comes time to set a static IP. I attempt to setup static in the Network Manager (nm-applet), however it does not seem apply the changes. 

I have edited /etc/network/interfaces and attempt to set it statically that way, according to all the little tutorials out there, however nothing seems to work. One thing I have noticed is that my /etc/network/interfaces appears to be different from others. Here's what I've got:

<code>
auto lo
iface lo inet loopback
</code>

It does not contain an entry by default for eth0. Anyone have any ideas?


Using 8.10.

---

### Post by bodhi.zazen on 2008-12-26
> **ZhiZaki said:**
> Alright, I'm an old time-y Slackware user who installed Ubuntu today. Everything seems fine, until it comes time to set a static IP. I attempt to setup static in the Network Manager (nm-applet), however it does not seem apply the changes. 

I have edited /etc/network/interfaces and attempt to set it statically that way, according to all the little tutorials out there, however nothing seems to work. One thing I have noticed is that my /etc/network/interfaces appears to be different from others. Here's what I've got:

<code>
auto lo
iface lo inet loopback
</code>

It does not contain an entry by default for eth0. Anyone have any ideas?


Using 8.10.

You need to first bring your network down, then edit /etc/network/interfaces as set a static IP manually (I have the same issue with network manager).

Something like say :

```
auto eth0
address 192.168.0.20
netmask 255.255.255.0
gateway 192.168.0.1
```Use your network netmask and gateway

You can show those (with the network up)

```
# Netmask
/sbin/ifconfig | grep Mask

# gateway
/sbin/route | grep default
```HTH

---

### Post by namdung on 2008-12-26
> **ZhiZaki said:**
> Alright, I'm an old time-y Slackware user who installed Ubuntu today. Everything seems fine, until it comes time to set a static IP. I attempt to setup static in the Network Manager (nm-applet), however it does not seem apply the changes. 

I have edited /etc/network/interfaces and attempt to set it statically that way, according to all the little tutorials out there, however nothing seems to work. One thing I have noticed is that my /etc/network/interfaces appears to be different from others. Here's what I've got:

<code>
auto lo
iface lo inet loopback
</code>

It does not contain an entry by default for eth0. Anyone have any ideas?


Using 8.10.

Intrepid network manager has this issue. You need to manually enter the data from terminal.

```
sudo gedit /etc/network/interfaces
```

The value should be like (replace with ur n/w details):
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.10.52
netmask 255.255.255.0
gateway 192.168.10.1

auto eth0

```

Your DNS entry
```
sudo gedit /etc/resolv.conf
```

Entry should be something like:
```
nameserver 192.168.10.1
```

Now restart the n/w services
```
sudo /etc/init.d/networking restart
```

---

### Post by ambar_N on 2008-12-26
I get same issue, and everything OK after I remove the gnome network manager and do all explanation above...
To remove gnome network manager, try this :

update-rc.d -f NetworkManager remove

Don't forget to restart networking service or reboot your PC for better...

---

### Post by shankhs on 2008-12-26
You can also try wicd.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
Its a nice replacement for Gnome Network Manager

---

### Post by ZhiZaki on 2008-12-26
Thanks everyone for your help. I've been set straight and everything seems to be working fine.

---

