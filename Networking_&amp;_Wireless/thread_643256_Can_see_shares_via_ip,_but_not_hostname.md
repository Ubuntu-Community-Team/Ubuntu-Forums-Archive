---
title: "Can see shares via ip, but not hostname"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by z-vap on 2007-12-17
I am attempting to figure out why I cannot see windows computers via their hostnames.  I have ubuntu-gutsy installed and it dualboots windows xp pro. They have winxp installed also.  

In nautilus, If I type:
```
smb://192.168.1.100
```

I can see whatever shares they have open.  

If I type:
```
smb://ComputerA 
```

I cannot.  They can ping my linux hostname server. I can't ping their hostname.  

When I am booted into winxp I can see and ping their stuff no problem.

---

### Post by HermanAB on 2007-12-17
You need to resolve the hostnames somehow.  Either use BIND or the /etc/hosts file.

Cheers,

Herman

---

### Post by chili555 on 2007-12-17
BIND is how windows does it, so naturally, some of us avoid it like the plague! Seriously, if you have many computers to deal with, BIND is best. If you have two or three, you can simply edit your /etc/hosts file to add:```
192.168.1.100  ComputerA
192.168.1.101  ComputerB
etc.
```This only works if A and B have static IP addresses.

---

### Post by z-vap on 2007-12-17
ah.  BIND you say.  I take it if the router dynamically assigns the IP then linux starts to have trouble?

---

### Post by z-vap on 2007-12-18
okay so wait a second.  Why is it that when my friend decides to change his computer name from ComputerB to ComputerS my windows computer notices the change.

But my Linux install does not?  There is nothing in the windows host files about these two Pc's but they seem to notice each other... What is running on these two pc's that are allowing them to "know" each other under the windows world, but Linux doesn't.

---

### Post by chili555 on 2007-12-21
> What is running on these two pc's that are allowing them to "know" each other under the windows world, but Linux doesn't.Bind.> I take it if the router dynamically assigns the IP then linux starts to have trouble?With Bind; it will find the computers by name, just as easily as any Windows machine (Bind is Bind, as Shakespeare suggested) even if they are assigned different IPs by the router. With /etc/hosts, you only find what you explicitly list.

Bind is a bit tricky to configure; hosts is EZ. Take your pick.

---

### Post by z-vap on 2007-12-22
well, Its fixed.  I didn't do anything to my host file, or play around with 'bind' What I did was go into my Network Settings (System > Administration > Network) and change the properties, by turning off "Enable roaming mode" and turning on "Automatic Configuration (DHCP)".

I assume DHCP utilized bind itself to resolve this.

---

### Post by jetsam on 2007-12-22
Network Manager!  Good find-- your fix might help some other people with this problem.  

Most smaller, Windows workgroup based, networks use NetBIOS to provide naming service.  Bind is another way to do it that's usually for larger corporate sized networks.  My guess is that Network Manager in roaming mode was blocking or disrupting NetBIOS.

---

