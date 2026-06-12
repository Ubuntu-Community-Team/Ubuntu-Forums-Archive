---
title: "Lost connectivity outside of router"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by Armagguedes on 2007-08-16
Hello there.

I am on an Acer Travelmate, running Kubuntu Feisty with a Broadcom 440x 10/100 NIC, which never gave me any problems whatsoever.

Yesterday, all of a sudden (without changing any settings), I lost all connectivity from my laptop to the internets. However, I can still access the router and fiddle with the definitions.

I checked the Kcontrol/System settings, and all IP's (IP, netmask, gateway, etc) are correct.

Ideas, or do you want me to boot into K-Feisty and paste something here?

Thanks and cheers;
Bruno

---

### Post by misconfiguration on 2007-08-16
Does this box have a static IP assigned to it, or is this all dynamically done VIA DHCP?

I would check /etc/host and /etc/resolv.conf to see if settings are correct, that is the best place to start IMO.

---

### Post by Armagguedes on 2007-08-16
DHCP, but i have limited the ranges assignable (from 192.168.1.100 to 192.168.1.104).

Also, another cute problem I on occasion come accross, is that Kubuntu suddenly chnages my network settings (the IPs and such, and the default gateway always get re-defined as 0.0.0.0).

Thanks, I'll check it later.
Cheers

---

### Post by misconfiguration on 2007-08-16
Setup a temporary static IP with DNS info and everything pre-defined.

See if this changes anything?

---

### Post by Armagguedes on 2007-08-16
/etc/host is blank

/etc/resolv.config has only "nameserver 192.168.1.1" on it

---

### Post by misconfiguration on 2007-08-16
I'm sorry, /etc/hosts

---

### Post by Armagguedes on 2007-08-16
127.0.0.1 localhost
127.0.1.1 GEOS

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


»» that's my /etc/hosts file

---

### Post by misconfiguration on 2007-08-16
Seems as if that's the issue,

do a ifconfig eth0 | grep inet
Paste that output..

Then I would do this..


```
edit /etc/hosts
127.0.0.1 localhost.localdomain localhost
<ip of box> GEOS

edit /etc/resolv.conf
nameserver 192.168.X.X (routers IP)
search (localdomain name)
```

---

### Post by Armagguedes on 2007-08-18
do a ifconfig eth0 | grep inet
Paste that output..[INDENT]bpsg@GEOS:~$ ifconfig eth0 | grep inet
          inet adr.: 192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          address inet6: fe80::2c0:9fff:fe4a:130c/64 scope:Link
[/INDENT]Btw, since I have set my OS to pt_PT, i have translated the output.

----------

Below, on "(localdomain name)", I just put "localdomain", as I do not know what my localdomain is.[INDENT] edit /etc/resolv.conf
nameserver 192.168.X.X (routers IP)
search (localdomain name)
[/INDENT]Still does not work (and sorry for the time it took me).
Cheers

---

### Post by Armagguedes on 2007-08-19
I have tried to do an "/etc/init.d/networking restart" after editing those files, and still no solution.

If this keeps up, I will have to re-install Kubuntu, as I see no other choice.

Cheers;
Bruno

---

### Post by lsutiger on 2007-08-19
does your router have any type of diagnostic area? (Linksys does ). If you do, use the router to ping out.
If you can reach the router, there is probably some wrong between the router and your modem.
Try it out

---

### Post by Armagguedes on 2007-08-19
> **lsutiger said:**
> does your router have any type of diagnostic area? (Linksys does ). If you do, use the router to ping out.

If you can reach the router, there is probably some wrong between the router and your modem. 
Try it out


The router is an Huawei, and no, I don't think it does have a diagnostic area. Also, the router *IS* my modem.

Cheers;
Bruno

---

### Post by lsutiger on 2007-08-20
What's the model number of the modem?

---

### Post by will71110 on 2007-08-20
have you tried pinging:

127.0.0.1
your gateway ?

if you can then something is either up with the firewall (if you have one installed) or out side your internal network.

---

### Post by Armagguedes on 2007-08-20
> **lsutiger said:**
> What's the model number of the modem?

My modem is an Huawei Aolynk DR814Q (ADSL2+).

-------------

> **will71110 said:**
> have you tried pinging:

127.0.0.1
your gateway ?

if you can then something is either up with the firewall (if you have one installed) or out side your internal network.

I can ping everything inside my network (127.0.0.1; 192.168.1.1 and 192.168.1.100). It's the outside that is the problem.

Cheers;
Bruno

---

### Post by Armagguedes on 2007-08-20
> **will71110 said:**
> have you tried pinging:

127.0.0.1
your gateway ?

if you can then something is either up with the firewall (if you have one installed) or out side your internal network.

ups. see the post above yours. sorry

---

