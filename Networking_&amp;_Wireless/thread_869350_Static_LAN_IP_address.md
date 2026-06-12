---
title: "Static LAN IP address?"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by flammenwurfer on 2008-07-24
I want to setup my computer to have a static ip address locally on my LAN, but I can't get it working with Network Manager.  I've done a manual configuration and entered all the necessary settings, but no go.  I've set my PS3 up with a static ip on the LAN using the same settings with success, so I know it should work.

Has anybody done this before?  Had any trouble?

---

### Post by bab1 on 2008-07-24
I usually do this manually.  But I see that you can config a NIC by:  
System-->Administration-->Network Tools.  Select the NIC interface (eth0 normally) and click on "Configure".  You need to have an IP address, subnet mask , and gateway address to connect.

My setup is:```
192.168.1.10
255.255.255.0
192.168.1.1
```

---

### Post by flammenwurfer on 2008-07-24
Yeah, I've played around with it for a while and I've entered the IP address, subnet mask, and default gateway, but it's simply not working.  

My default gateway ip is 192.168.11.1, the ip I want the computer to have is 192.168.11.5.  I enter those in the manual configuration part of network manager, but I get no IP address.

---

### Post by bab1 on 2008-07-24
What is the output of:```
ifconfig -a
```

I see that:```
>sudo network-admin
```

has all of the config settings including dns and host.

---

### Post by Interflex on 2008-07-25
This is the only way I could get a static to stick:

in term,
**ifconfig -v eth1 **(I have 2 NICs, this is the one I need static on - shows info on it)
**ifconfig eth1 10.104.5.35**
**ifconfig eth1 netmask 255.255.0.0**
**ifconfig -v eth1 **(to make sure I have it correct)

**route **( if route shows only one entry, you need a def GW)
**route add default gw **(***IP of your gateway***)
**route** (you should have at least 2 entries now)

**Ping google.com **(should now work)

---

### Post by Iowan on 2008-07-25
I usually enter the information directly into **/etc/network/interfaces**.

---

### Post by cariboo on 2008-07-25
What is the output of Apllications-->Accessories-->Terminal:

```
cat /etc/network/interfaces
```

There may be something in the file that needs changing.

Jim

---

