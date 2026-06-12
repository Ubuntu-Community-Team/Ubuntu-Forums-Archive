---
title: "Dual Networks (Wireless and Wired) with printer sharing"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by Grey Box on 2008-01-08
I've been looking and looking but I couldn't find any solution on-line. Can anyone help?

I have two separate networks. One wired, one wireless. All my computers run Gutsy Gibbon.

The wired LAN connects to the internet, and my Ubuntu laptop connects to it automatically, in preference to the wireless LAN which has a network printer on it:

<Internet modem / router> ---[wired ethernet]--- <**ubuntu box**> --[wireless, WPA] -- <router> --[wired ethernet]--<printer>

If I connect to the wireless network I lose the wired network, even though they are on different subnets (192.168.0.* and 192.168.2.*)

Can anyone explain how to get Ubuntu to connect to both networks without creating conflicts?

---

### Post by chewearn on 2008-01-08
You need to set-up your ubuntu box as a gateway.  Easiest way (I think) is to use Firestarter.
```
sudo aptitude install firestarter
```Else, you will have to manually edit the iptables, enable ip forwarding, etc.

---

### Post by Grey Box on 2008-01-08
Thanks I will try that.

---

### Post by Grey Box on 2008-01-08
I have made some headway. Network manager now says it is connected to the wireless and wired networks (had to switch of Roaming Mode for both, DHCP auto for both)  after rebooting. Firestarter shows no errors and doesn't complain when I set it up for network sharing. I suspect that actually I need to set up bridging mode, but for now I just want the two networks to work together:

I am having a problem however - when I reboot, the wired connection comes up without a problem and the internet is browsable. However the wireless connection requires a manual "sudo ifdown eth1" followed by "sudo ifup eth1" to get it going. 

I can then access the router home pages for both routers, but my internet access is lost.

How can I fix this?

---

### Post by chewearn on 2008-01-08
Frankly, I only have a basic networking knowledge, and have only really deal with simple setups.

What I think you have to decide is whether the modem/router will function as the modem only or modem and gateway.
1. modem only
The ubuntu box will "dial" to modem using pppoe (or as specified by your ISP).  Then you ubuntu box will be the gateway, perform functions like NAT, DNS, DHCP, firewall, and route the traffic on the second subnet.  This is the more flexible option, but require more complicated set-up on your ubuntu box.

2. modem and gateway
The modem/router dial to your ISP; and provide the NAT, DNS, etc.  You will have less flexibility, but it should be easier to set-up.  Your ubuntu box will then bridge the two sides of the connection into one subnet.

Hopefully, someone with more experience can confirm my thinking.

---

### Post by subbejon on 2008-01-08
Hello there,

First of all I'd like to mention that I'm pretty n00b with ubuntu as well as with forums. So if this post isn't in right category and place, please teach me.

My comp is connected via LAN to internet. I have also laptop (with Win XP, unfortunately I have to keep it) with wlan possibility, so that would be the natural choice. BUT is it somehow possible to connect my laptop via bluetooth to my computer, and that way to internet?

WinXP (laptop) ---[bluetooth]---Ubuntu (PC) ---[LAN]---internet

Bluetooth works perfectly in my Ubuntu 7.10. and sending/ receiving files is not a problem with my XP-laptop.

Thank in advance!

---

### Post by Grey Box on 2008-01-08
> What I think you have to decide is whether the modem/router will function as the modem only or modem and gateway.
1. modem only
The ubuntu box will "dial" to modem using pppoe (or as specified by your ISP). <..etc.>
2. modem and gateway
The modem/router dial to your ISP; and provide the NAT, DNS, etc. You will have less flexibility, but it should be easier to set-up. Your ubuntu box will then bridge the two sides of the connection into one subnet.

I am definitely doing option 2, but I am getting stuck and, not knowing enough about all this, I can't figure out what I'm missing. I am using Network Manager with manual configuration, I have assigned a static IP for the wired network, and this works without a problem until I come on-line with the wireless network. I variably am able to either:
[LIST=1]
[*]browse the net and access the wired network (192.168.0.*) 
[*]not browse the net but access both wired and wireless LAN's, including the router homepages (192.168.0.* and 192.168.2.*)
[*]browse only the wireless network
[/LIST]
I think, if I can just get the ubuntu box to access both networks without conflicts, I could work out how to bridge and everything else, but until then I suspect I'm not going to get anywhere.
Has anyone managed to do this, and what did you do differently? Use the same subnets on both lans or what?

---

### Post by chewearn on 2008-01-08
> **Grey Box said:**
> I am definitely doing option 2, but I am getting stuck and, not knowing enough about all this, I can't figure out what I'm missing. I am using Network Manager with manual configuration, I have assigned a static IP for the wired network, and this works without a problem until I come on-line with the wireless network. I variably am able to either:[LIST=1]
[*]browse the net and access the wired network (192.168.0.*)
[*]not browse the net but access both wired and wireless LAN's, including the router homepages (192.168.0.* and 192.168.2.*)
[*]browse only the wireless network[/LIST]I think, if I can just get the ubuntu box to access both networks without conflicts, I could work out how to bridge and everything else, but until then I suspect I'm not going to get anywhere.
Has anyone managed to do this, and what did you do differently? Use the same subnets on both lans or what?

For bridging, I figure it should be easier to use same subnet for both sides of the network.

I only know about bridging from configuration of virtual machines.  Essentially, you need to manually create an entry "br0" into /etc/network/interfaces.  I have thought that firestarter might have an wizard (or some options) that will create this, but apparently I was wrong.

You might be able to figure out how to set up a bridge, by studying Virtual Machines howtos.

---

### Post by chewearn on 2008-01-08
> **subbejon said:**
> Hello there,

First of all I'd like to mention that I'm pretty n00b with ubuntu as well as with forums. So if this post isn't in right category and place, please teach me.

My comp is connected via LAN to internet. I have also laptop (with Win XP, unfortunately I have to keep it) with wlan possibility, so that would be the natural choice. BUT is it somehow possible to connect my laptop via bluetooth to my computer, and that way to internet?

WinXP (laptop) ---[bluetooth]---Ubuntu (PC) ---[LAN]---internet

Bluetooth works perfectly in my Ubuntu 7.10. and sending/ receiving files is not a problem with my XP-laptop.

Thank in advance!

This is a tougher question, compared to the WiFi one.  I know only a bit about bluetooth set-up on Windows side, but nothing on ubuntu bluetooth set-up.


Actually, it will make your life so much easier to stick with stable/known/older way to connect.  It cost less than $50 to buy two standalone WiFi Access Points, which you can bridge together.  Then, you have wireless connection across your house, minus hassle of dealing with OS set-ups and such.
I have this been relying on this kind of point-to-point set-up since wireless-g hit mainstream.  Never have to worry about linux driver support, and never have to worry about wifi interoperability between linux and windows.

---

### Post by Grey Box on 2008-01-09
This has proven to be quite tricky so far. I succeeded in getting both interfaces to connect to wired & wireless networks (at least they were each assigned an ip address) but the wireless interface is as yet non-functional. When I tried to bridge it using various howto's I found on these forums I found it just kills the setup without any success. So at this stage I'm assuming it hasn't been done by anyone on Ubuntu, which surprises me. I always assumed linux was a bit more robust when it came to networking - and I'm sure the process of setting it up is simple, but I just don't know what it is.

I'll give it another few goes. If all else fails I will just go ahead and buy another wireless router and get them to talk to eachother instead of relying on linux to do it.

---

### Post by Grey Box on 2008-01-09
Bump? Ok, I have looked again over the net, and it seems what I want to achieve is possible in Windows but not Linux, which I refuse to believe.

Is it possible to be a client of two separate networks in linux? That's all I want to achieve, using wired and wireless cards.

---

### Post by chewearn on 2008-01-09
> **Grey Box said:**
> Bump? Ok, I have looked again over the net, and it seems what I want to achieve is possible in Windows but not Linux, which I refuse to believe.

Is it possible to be a client of two separate networks in linux? That's all I want to achieve, using wired and wireless cards.

So, have you add a virtual bridge into /etc/network/interfaces?

---

### Post by Grey Box on 2008-01-11
Forgive my noobiness on this stuff, but I did try to bridge the connections, here was my interfaces file which managed to kill all the network connections - they were 'connected' but not associated with an ip address:

```

auto lo
iface lo inet loopback
iface eth0 inet dhcp
address 192.168.0.4
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0
auto eth1
auto br0
iface br0 inet static
address 192.168.0.125
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1
pre-up ifconfig eth0 0.0.0.0 up
pre-up ifconfig eth1 0.0.0.0 up
bridge-ports eth0 eth1
post-down ifconfig eth0 down
post-down ifconfig eth1 down

```

I only half understand what I'm doing which is why it's not working, though I am learning I think! I still haven't found a working example of what I want to achieve. Also I think part of the problem with my setup is that I don't want the computer to be the master of any network, but a client to both. If I ever get this working I will definitely write a howto!

In the meantime I'm taking measurements and so on to see if I can get a cat5 cable to go under the floor from the wired router to the wireless routerand printer at the end of the house.

---

### Post by chewearn on 2008-01-11
Another thing worth investigating is enabling ip forwarding.

```
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```

If the above command works, you need to make it persistent by:
```
gksu gedit /etc/sysctl.conf
```

Add this line:
```
net.ipv4.conf.all.forwarding=1
```

Also, I'm not sure if you need to enable kernel module "tun".

---

