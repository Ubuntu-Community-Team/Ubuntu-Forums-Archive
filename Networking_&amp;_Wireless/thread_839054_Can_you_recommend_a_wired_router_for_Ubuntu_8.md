---
title: "Can you recommend a wired router for Ubuntu 8?"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by Jamface on 2008-06-24
I'm back after a long lay-off while I tried to work up the courage to have another go at Ubuntu.  I have a D-Link DSL-504L wired router which Ubuntu 6 and 7 did not work with when I installed Ubuntu.  I have spent too long trying to get this setup to work.  Please could someone recommend a wired router which  is known to work with Ubuntu 8 from installation, without having to alter settings in network manager.

---

### Post by dmizer on 2008-06-24
first of all, what leads you to believe that your router is at fault?

routers are completely independent of operating systems.  this means that no matter what OS you use (mac, windows, os/2, BEos, linux or any other os) the router will pass traffic to your computer.  so if you're having problems, it's likely a result of something other than your router.

bad ethernet cable
bad module driving your network adapter
completely broken router (can other computers use it?)

take a computer and a live cd to another location, and connect it.  see if you can get online.  try rebooting your router (turn it off and turn it back on).

second of all, you may run into problems with getting a new router.

the dsl-504 L is a modem/router combination.  this means that it's configured to connect to your internet provider.  you can't just replace this piece of equipment with a router and be able to surf.  you'll need both a router and a modem (or another modem/router combo).

problem with getting a new modem is that you'll have to configure the new modem for your ISP settings yourself.  these settings can be a real pain to get because no ISP supports third party equipment.

---

### Post by Jamface on 2008-06-24
Many thanks for your help.
The modem/router is not broken nor are the cables.  It all works very well connecting my desktop PC and laptop together and to the internet when running Windows XP on both machines, but I have not been able to get an internet connection when installing Ubuntu 6 or 7 on the PC. Ubuntu sets up the network connection as DHCP but it will not connect.  I had read on one of the threads that Linux does not like D-Link routers so I thought changing to a modem/router which is known to work with Ubuntu would save me spending yet more time trying to get the network connection to work. 

If you can suggest what I should do to get the connection to work I would be very grateful. I'm not sure if i need to change the setings in the router, in network manager or both.

I have tried ping tests and they show packets sent but 0 packets received.  /sbin/route/ -n gives me 192.168.1.1 I can get to the router using [www.192.168.1.1](www.192.168.1.1) but not beyond it to the internet. 
/sbin/route does include a default line with 'mygateway' o.o.o.o as the genmask (whatever that is) and eth0 under Iface. 

What else might be the problem?

---

### Post by dmizer on 2008-06-24
try disabling ipv6 with this howto:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

also try using opendns dns servers:
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

if neither of those two things help, let me know.

---

### Post by Jamface on 2008-06-24
I tried the OpenDNS first.  I put the addresses in the router setup. This worked OK for Winows on both machines but not for Ubuntu.  So I tried to put the addresses into the Ubuntu Network Manager as OpenDNS suggests.  But the DNS window would not accept the new first new address as a replacement for the existing 192.168.1.1.  Every time I put in the 208. etc. address it was replaced by the old 192. etc. address. So I deleted the 192. etc. address.  Fatal mistake!  The window would not then accept any addresses.  A reboot did not restore the original address. I seem to be making things worse!

I then had a look at the ipv6 issue and followed the instructions for Ubuntu 8!. Not surprisingly this did not seem to do anything as I have Ubuntu 7 installed.  The instructions for Ubuntu 7 looked rather too complicated for my very limited abilities with the terminal.  

After I tried to replace the DNS addresses in Ubuntu network manager my internet connection on this laptop ceased working.  I could not even access the router from this machine.  Could the 2 events be connected?

A reboot to Windows on both machines has restored my internet connection.  What next?

---

### Post by dmizer on 2008-06-24
for opendns, follow the directions under step 2, below where it says: "To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:"

for disabling ipv6, type this in terminal:
```
gksudo gedit /etc/modprobe.d/blacklist
```
scroll all the way to the bottom of the file, and add this on a new line:
```
blacklist ipv6
```
save the file, and reboot.

---

### Post by Jamface on 2008-06-24
Many thanks for all your help, demizer.  My Ubuntu 8.04 disc arrived today and I have been trying to install it but without success.  I will start a new thread about this in the appropriate forum and come back to the internet connection problem if it arises after I have installed Ubuntu 8.04.

---

