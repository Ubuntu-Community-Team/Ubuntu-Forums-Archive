---
title: "VirtualBox and Vista"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by kroenecker on 2008-05-17
I'm having trouble with my inspiron 1420 and it's wireless connection.  I want to connect to the internet through Vista (using VirtualBox), but I'm not sure what I need to do.

I've done the following:

1) [http://jhcore.com/2007/03/25/vista-on-ubuntu-using-virtualbox/](http://jhcore.com/2007/03/25/vista-on-ubuntu-using-virtualbox/)
   -- This link shows how to install the driver for the virtual machine's network interface.

2) [http://home.nyc.rr.com/computertaijutsu/vboxbridge.html](http://home.nyc.rr.com/computertaijutsu/vboxbridge.html)
   -- I've tried to follow the advice here but I'm still not able to connect.

Any suggestions?

---

### Post by kroenecker on 2008-05-17
Well I haven't figured this out yet, but I thought I might add some detail.

First of all my router used DHCP.  Will this cause problems?  The command below is setting a static ip for the tap0 device, but, frankly, I don't know how parprouted works so I'm confused if this will cause issues.

From the wiki:

I'm using the following to create the tap0 dev:

#!/bin/bash
sysctl net.ipv4.ip_forward=1
VBoxTunctl -b -u $USER
ip link set tap0 up
ip addr add 192.168.1.100/24 dev tap0
parprouted wlan0 tap0

I don't get any errors.  I've configured the the network as follows:

Adapter Type: Pcnet FAST III
Attached To: Host Interface

Interface Name: tap0

Now when I boot Vista, my network interface appears to be there... But I can't ping anything.

Again any advice is appreciated.

---

### Post by kroenecker on 2008-05-17
Alright I just got it to work.

After logging into Vista go to "Control Panel" > "Network and Internet" > "Network and Sharing Center" > "Manage Network Connections"

You should see one device listed.  If not, you should go back to one of the links in the first post to find out about how to install the driver for the network device.

So right click on the Local Area Connection and select properties.  Now select Tcp/IPv4 and edit its properties.  

Put in some other ip that is available on your network i.e. 192.168.1.109.  It should be unique I think?

Network Mask: 255.255.255.0
Default Gateway: 192.168.1.1

Finally be sure to "cat /etc/resolv.conf" to find out what ip your dns server has and use that for the DNS ip.  

That should do it!

---

### Post by kroenecker on 2008-05-18
Well I'm back to not having internet connectivity after a reboot.  I have no idea what I'm doing wrong :(

---

### Post by kroenecker on 2008-05-18
Alright I read the manual I found that NAT works best.  Basically all I did was to enable DHCP for the network interface.  I left the DNS server manually applied (the ip from /etc/resolv.conf).  Now I'm able to connect to the internet, which is all that I wanted to do anyway.

The more complicated solutions are really meant for running a server from the virtual machine (or being able to access the virtual machine from the internet e.g. ssh).

Well, I guess I learned something (that setting up a tap etc is a bit too much for me to want to really figure out :P )

---

