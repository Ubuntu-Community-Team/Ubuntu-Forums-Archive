---
title: "Wireless internet just stopped working"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by Notclive on 2007-03-11
A few days ago my wireless internet just stopped working, I can't remember what I did before it happened a day later it worked again then stopped again and hasn't worked since. If i try "$ sudo dhclient eth 1" I get ```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:11:50:3b:26:fa
Sending on   LPF/eth1/00:11:50:3b:26:fa
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
I can connect on my Windows partition but that's acting a bit weird, it can never connect straight away I have to press repair. I've noticed other people have had this problem but it usually tends to be after a 6.10 install whereas I upgraded ages.
Some more info:
Router shows up in wifi-radar
Can't ping anything
Tried changing the host name to the same as windows

---

### Post by rabid emu on 2007-03-11
Mine stopped working too.  It worked fine since install, and then one day my wireless card seemed to disappear.  It works fine in Windows too.

I'm planning on reinstalling the restricted-drivers package and I'll let you know how that goes.

---

### Post by rjfioravanti on 2007-03-11
This also happened to me just a few weeks ago

I fixed the problem for myself by changing to use a static IP instead of aquiring a dynamic IP from my router

---

### Post by Notclive on 2007-03-11
Static IP never seems to work for me what, settings should I use

---

### Post by Notclive on 2007-03-11
Static IP never seems to work for me, what settings should I use

---

### Post by rjfioravanti on 2007-03-12
looks like you are using eth1

i think you can do 

```

sudo gedit /etc/network/interfaces

```

and then you can edit the file to look something like this:

```

iface eth1 inet static
address    <ip address>
netmask   <your subnet mask>
gateway   <your default gateway>
wireless-essid  <name of wireless network>

```

i think you would have to add something else if there is encryption on your network, you can probably start with this and find how to do the password on google

---

### Post by gwpritch on 2007-03-12
Anyone have any idea why this is happening?!? My wireless internet just stopped a couple of hours ago and I can't get back on. Local network is fine and I can connect via windows...what gives.

---

### Post by Notclive on 2007-03-13
Can't get the static ip working I think I might be using the wrong settings.

@ gwpritch, my theory is it's something is changing in the router or with the isp like my dynamic ip changing because I didn't change any internet settings or files and it just stopped.

---

### Post by gwpritch on 2007-03-13
Can't be dynamic IP's, I've been using a static IP for some time. And as I said I am still able to connect via windows.

---

### Post by Notclive on 2007-03-18
Iv'e installed Fedora Core 6 and am having exactly the same problem, wireless on my Windows partition also acts strangely.

---

