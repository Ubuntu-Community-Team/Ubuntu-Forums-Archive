---
title: "I can ping sites, have dns servers, and dhcp is set up.  But can't browse."
date: 2009-10-25
forum: New to Ubuntu
---

### Post by Remagen on 2009-10-25
This has me stumped.  I am connected to a college network, which requires me to have my MAC registered (Done, windows works fine).

So, when I boot to Ubuntu, I try to access a page in Chromium, and I get an 
Error 102(net::ERR_CONNECTION_REFUSED): Unknown error.

Firefox fails too.

Resolve.conf has several servers, all of which I can successfully ping, and I can ping digg.com and google.com using their names.  

Also, there is constant network activity, but I can't tell what process/ports are downloading and uploading. (netstat -tupl didn't seem to show anything)

I don't have any network managers installed (for w/e reason).

---

### Post by LewRockwell on 2009-10-25
which browser in windows?

.

---

### Post by Remagen on 2009-10-25
Google Chrome

---

### Post by Remagen on 2009-10-25
Update:  I randomly tried to update my system, and it of course failed, but I read the text.

The error states that: 
failed to fetch package blah blah 
at IP ADDRESS: 192.168.0.1:80 (connection refused).

Obviously, the ip addr of canonical is not 192... but I don't have a router between me and the internet now (I used dhclient to update my settings) so what is rerouting all my http requests to 192.168.0.1?

---

### Post by QLee on 2009-10-25
> **Remagen said:**
> Update:  I randomly tried to update my system, and it of course failed, but I read the text.

The error states that: 
failed to fetch package blah blah 
at IP ADDRESS: 192.168.0.1:80 (connection refused).

Obviously, the ip addr of canonical is not 192... but I don't have a router between me and the internet now (I used dhclient to update my settings) so what is rerouting all my http requests to 192.168.0.1?

I could make a guess. When you had the router it had an internal LAN address of 192.168.0.1 and so that address was set as the gateway. It appears that your system is still trying to access that gateway for the 'Net.

---

### Post by Remagen on 2009-10-25
where can I change the internet gateway on the commandline?  I'm not finding it in the usual places (that I know of).

---

### Post by QLee on 2009-10-25
Are you using network manager or perhaps, wicd and is it trying to auto connect to the last used connection?

---

### Post by Remagen on 2009-10-25
There is no network manager, either nm-applet or wicd.

---

### Post by QLee on 2009-10-25
What is the content of your /etc/network/interfaces file?

I'm going to have to leave but someone else will help from this point.

---

### Post by Remagen on 2009-10-25
interfaces holds:

auto eth1
iface eth1 inet dhcp

auto lo
iface low inet loopback

---

### Post by QLee on 2009-10-25
> **Remagen said:**
> interfaces holds:

auto eth1
iface eth1 inet dhcp

auto lo
iface low inet loopback

Still around you were back quickly.

If you are no longer connected to a router, what is doing DHCP and assigning IP adresses for your interface?

---

### Post by LewRockwell on 2009-10-25
sounds like you might have to contact the college network administrator to find out the specifics for their LAN/WLAN

.

---

### Post by falconindy on 2009-10-25
Give us the output of `route`. Also, it sounds like there might be an http proxy enabled locally somewhere.

---

### Post by Remagen on 2009-10-27
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.250.0       U       0        0        0   eth1
default         192.168.0.1     0.0.0.0               UG     0        0        0   eth1

Where can I find/configure any local proxies?

---

