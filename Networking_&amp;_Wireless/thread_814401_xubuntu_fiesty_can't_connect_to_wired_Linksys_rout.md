---
title: "xubuntu fiesty can't connect to wired Linksys router"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by dlstrife on 2008-05-31
I'm running Xubuntu Fiesty on a box and trying to connect to a Linksys WRT54GS router. I want to eventually get it working on wireless, but will need to download some new packages to do so, so in the meantime I'm trying to just get a wired connection to get online. My board has a built in ethernet port which is enabled and which I've connected directly to the router. The router functions fine on other boxes and my laptop running Hardy can connect wirelessly to it. Under Network the box recognizes the wired connection, so I enabled it and set to Automatic Configuration (DHCP). It fails to acquire any sort of IP or anything though, and pinging the router returns "Network is unreachable".

---

### Post by supremedalek on 2008-05-31
Which OS are you running in the wrt54gs: the factory linksys one or stuff like openwrt (which is what I use)? Can you check the status page in your website and see if the router picked the MAC of your network card? If you set your xunbutu box to do static IP, does that work?

---

### Post by dlstrife on 2008-05-31
the router is running the default OS from linksys. Statically configuring it doesn't seem to work either. The DHCP table of the router has 2 entries in it that I don't recognize and that don't have names associated with them. How do I find the mac address of the onboard LAN to check if it's listed?

---

### Post by dlstrife on 2008-05-31
i just ran ifconfig and it doesn't list eth0 or eth1. i believe that it sees the onboard LAN as eth1, at least that's how it's listed in /etc/network/interfaces.

---

### Post by supremedalek on 2008-06-01
> **dlstrife said:**
> the router is running the default OS from linksys. Statically configuring it doesn't seem to work either. The DHCP table of the router has 2 entries in it that I don't recognize and that don't have names associated with them.

That's nice. Let's see if they are not unwanted guests...

> **dlstrife said:**
> i just ran ifconfig and it doesn't list eth0 or eth1. i believe that it sees the onboard LAN as eth1, at least that's how it's listed in /etc/network/interfaces.

What happens if you do, say, "ifconfig eth1 up" and then type ifconfig?

Other thing I was thinking here: you could manually "create"/enable new interface:


```
raub@keg:~$ ifconfig eth0 plumb
or 
raub@keg:~$ ifconfig eth0 create
```

I think the latter is the proper linux way while the former is how I learned in Solaris, in which I put a 4 port card once and then had to enable each port manually (different port names but, hey). But, once that step was done, I could then do 

```
raub@keg:~$ ifconfig 
```

and would see the port. This may not be the proper solution but if you can create the interface like this, we may have a better clue about what is going on here. FYI, sometimes I like to try stuff manually to see if I can do it so I can then see if there is a step the automagic procedure is missing.

Before I hit post in this collection of misinformation, did you try typing "dmesg | grep eth1" to see if it knows of your interface?

---

### Post by dlstrife on 2008-06-01
Ok, the mac address for eth1 is in the router's DHCP table. It's also now recognized in ifconfig and dmesg after running "ifconfig eth1 up". However it still doesn't have an IP address. Also, what would enabling eth0 do, since the onboard LAN is being seen as eth1?

After a this followed by a reboot I now have an IP address. Go figure. Hopefully it will last. I'll post back after testing it for a while.

---

