---
title: "Wireless Router Question"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by WBL on 2009-04-08
I recently moved, and got Charter internet.  We tried connecting both my Linux laptop and PS3 to the internet with ethernet cables, but it did not work.  Charter says there is no problem since the (Windows) laptop that they brought over connected to the internet.

So I got a wireless router hoping that wirless internet would fix the situation.  Main problem I think...the wireless router came with a CD that said "Run this CD first."  Of course, that CD won't work on Linux.  :mad:

So I hooked up the wireless router, and Linux found the wireless network.  However, I am STILL not connected to the internet.

Does anybody know how I can configure the wireless router, or what I need to do?

-WBL

---

### Post by freak42 on 2009-04-08
Your wireless router (what's the model) likely comes with a web-configuration page you can use to setup all the stuff you need to connect to your provider. You can try these ip's in your browsers url bar to try to connect to your router:
192.168.1.1
192.168.0.1

if that doesn't work, find out the ip of your router (in the network setup stuff sometimes called gateway) or post the contents of this file here (/var/lib/dhcp3/dhclient.leases).

---

### Post by Hospadar on 2009-04-08
If, from a terminal, you run ```
netstat -nr
``` it'll tell you your gateway address, which should be your router ip, in my case:```
<luke@luke-node:~$> netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth1

```192.168.1.1 is my router's IP

If you put that IP into firefox it'll go to your router's config and you don't need to monkey with their bogus router cd business.  Your router will probably ask for a password, which should be in your user manual (since you would have had to known it to change it)

That said, if you are connected to the wifi, and you can get to your router's config page, then your laptop's connection is working just fine, and you need to tell Charter something nasty and make them come fix it.

Also too, as I recall for comcast, they had some bogus registration stuff I had to do in IE when I signed up after everything was connected, if that's the case, maybe you need to find someone with a windows machine to come over to turn it all on.

---

### Post by WBL on 2009-04-08
> **freak42 said:**
> Your wireless router (what's the model) likely comes with a web-configuration page you can use to setup all the stuff you need to connect to your provider. You can try these ip's in your browsers url bar to try to connect to your router:
192.168.1.1
192.168.0.1

if that doesn't work, find out the ip of your router (in the network setup stuff sometimes called gateway) or post the contents of this file here (/var/lib/dhcp3/dhclient.leases).


When I try 192.168.1.1, it asks for a username or password.  :mad:

How do I run the install CD from WINE?

-WBL

---

### Post by antmenj on 2009-04-08
It should come with a default password and user name.  Make sure you change this or anyone can hack your router.

The default is normally written on the box, in the book or on a sticker on the router.

A common default is:

user name: admin
password:1234

You may not need that disk at all.

---

### Post by ramjet_1953 on 2009-04-08
Regardless of whether you run the install disk from WINE,you will still need to have the default user name and password for your router.

If you don't have the original documentation that came with the router, just go to the manufacturer's web site and you should find that the documentation is available for download.
This documentation will have the default user name and password for your router and you will them be able to configure it from your web browser.

Regards,
Roger ;)

---

### Post by lisati on 2009-04-08
> **antmenj said:**
> It should come with a default password and user name.  Make sure you change this or anyone can hack your router.

The default is normally written on the box, in the book or on a sticker on the router.

A common default is:

user name: admin
password:1234

You may not need that disk at all.

My $0.02 worth: MY Netgear wgr614v7 has the following default:
user name: admin
password: password

---

### Post by coffeeaddict22 on 2009-04-08
Some(?all) routers let you access settings off a web interface.  If you post (or google) the router details, you may be able to find a web address that gets you in.

There was a nice article on troubleshooting networks a few days ago: 
[http://www.linuxjournal.com/content/troubleshooting-network-problems]("http://www.linuxjournal.com/content/troubleshooting-network-problems")
which has a good approach to breaking the problem down.

---

