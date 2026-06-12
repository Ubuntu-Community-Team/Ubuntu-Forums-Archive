---
title: "How can i  change the ip address to be static?"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by asaren on 2008-12-12
Hi,

How can i  change the ip address to be static?

Thank a lot.

---

### Post by doctorbighands on 2008-12-12
Generally, it's up to your ISP to determine whether your IP is static or dynamic. In many cases, you can purchase a static IP from them if you want one, in addition to your dynamic.

As an alternative, check out DynDNS ([http://www.dyndns.com/](http://www.dyndns.com/)). They provide a free service to help you host a server with a dynamic IP. I'm not 100% certain how it works (mostly because I was too lazy to read up on it before I signed up!), but I do know that it's a great service. It works for me!

---

### Post by iponeverything on 2008-12-12
> **asaren said:**
> Hi,

How can i  change the ip address to be static?

Thank a lot.

Edit this file:

```
sudo nano /net/network/interface
```

Add a section something like this:

```

auto eth0

iface eth0 inet static
address 10.0.0.2
netmask 255.255.255.0

```

Where 10.0.0.2 is your static IP address. Do a:

```
man interfaces

```
for more information on the format of the file.

---

### Post by donkyhotay on 2008-12-12
I think this question needs clarification. Do you want a static *internet* IP address or a static *local* IP address. As bighands mentioned a static internet IP address is up to your ISP. If you want a local static IP address you would just go to 
system > preferences > network configuration
then edit your connection, click on the ipV4, change to manual and then specify you IP addres. Remember though this only changes your local IP address for your LAN.

---

### Post by azzid on 2008-12-12
And if you are just wondering how to set a static address on your network interface you could tweak the file **/etc/network/interfaces**.

The network interface receiving the dynamic address should have a line there looking like this:
```
iface eth0 inet dhcp
```

Change that into:
```

iface eth0 inet static
        address 10.0.0.1
        netmask 255.255.255.0
        broadcast 10.0.0.255
        network 10.0.0.0
```

*But changing the addresses to match your demands naturally.*

Should help.

After you've done the change you can run:
```
sudo /etc/init.d/networking restart
```

That will activate the changes.

---

### Post by Keith Hedger on 2008-12-12
If you prefer a gui way go to System->Administration->Network click "unlock" select an interface ie "wired connection" click "properties" and select "static ip address" from the drop down list

---

### Post by iponeverything on 2008-12-13
> **Keith Hedger said:**
> If you prefer a gui way go to System->Administration->Network click "unlock" select an interface ie "wired connection" click "properties" and select "static ip address" from the drop down list

seems that System->Administration->Network is gone under 8.10 -- I think that Network Manager has taken over the duties.

---

### Post by Keith Hedger on 2008-12-13
Sorry I'm using 8.04

---

