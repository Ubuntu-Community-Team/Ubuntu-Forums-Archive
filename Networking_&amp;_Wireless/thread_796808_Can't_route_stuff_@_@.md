---
title: "Can't route stuff @_@"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by IFailAtLinux on 2008-05-16
I tried installing linux again and I have setup like this:

Linux, web interfaces:
eth1: connects to world trough LAN, gets IP trough DHCP.
eth0: connects to laptop trough 2nd LAN card

Windows XP, connections:
It's connected trough LAN to eth0 on linux

Well, I set up my local network like this:
eth0 has adress 192.168.5.1/24 and laptop has 192.168.5.5/24 and uses 192.168.5.1 as default gateway.

Now, I want on my laptop to be able to connect to world using linux as a router of sorts,  I guess.

On 2 windows XP systems I would just set "allow other users to use this connection"(rough translation) on equivalent of eth1 to do this, here I'm completely stuck.

I tried working with quagga but zebra and ripd are too hard to understand for me, lol. I tried working with iptables as well, but I don't have nearly enough knowledge to figure it out.

---

### Post by spd106 on 2008-05-16
It's probably easiest to use install and use firestarter.

See [http://www.fs-security.com/](http://www.fs-security.com/)

Hopefully [ufw]("https://wiki.ubuntu.com/UbuntuFirewall") will make this easier in future releases.

---

### Post by rlcomstock3 on 2008-05-16
Temporarily Share Internet Connection on Ubunty Gutsy (Linux)

On host machine:

Connect to the internet with eth1

I am going to set the network for eth0 to be 192.168.10.*
Server: 192.168.10.1
Client: 192.168.10.2

$ sudo ifconfig eth0 192.168.10.1 netmask 255.255.255.0
$ sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
$ sudo su
$ echo 1 > /proc/sys/net/ipv4/ip_forward

On client machine:
(this machine wants to connect to host over eth0)

$ sudo ifconfig eth0 192.168.10.2 (set a manual IP address)
$ sudo route add default gw 192.168.10.1 eth0  (This sets the gateway, you can do this in windows too)

---

### Post by SpaceTeddy on 2008-05-16
[[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874") is a thread that explains what you need to do to make an ubuntu box a router. You can probably skip most of it since your setup already sounds quite nice. 
if any question arise after that, just ask :)

---

### Post by IFailAtLinux on 2008-05-16
I am pretty lazy (after sitting on that for whole day) so I went with firestarter and it worked wonders with just few clicks. Now I put my system in init 3 and let it go with update as it has like 400 packets to go, heh, heh. I'll leave it overnight.

I've bookmarked the other link and if I feel adventurous(and have some time) I'll play around with manual settings for the sake of learning. Thanks a lot for quick replies.

---

