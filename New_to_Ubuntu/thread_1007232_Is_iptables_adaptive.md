---
title: "Is iptables adaptive?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by philinux on 2008-12-10
I've a default install.

Went to grc.com and tried the common ports test. Came up all closed not stealthed. 

Tried the All service Ports. First 90 or so ports came up closed the rest stealthed. Tested again and all came up stealthed. 
Repeated the common ports test and Full stealth pass.

So is iptables adaptive as suggested by grc.com
> Strange Results?
Personal firewalls are beginning to exhibit "adaptive behavior". The grid shown to the left starts off showing ports mostly closed with a few open (mostly blue with a few red cells). Then at some point it suddenly switches into "stealth mode". This can occur when a firewall "adapts" to the scanning IP and raises its defenses against just the attacker. This complicates the job of accurately checking a system's security.

Wonder whats happens when I reboot?

---

### Post by gettinoriginal on 2008-12-10
Don't know if this will help:  :p

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by iponeverything on 2008-12-10
iptables by itself is not adaptive. The addition of a few scripts can make it so.  (port knocking, etc.)

---

### Post by philinux on 2008-12-10
So what's going on then to suddenly go from closed common ports to stealthed? Like I said it's a default install.

---

### Post by Gone fishing on 2008-12-10
Can't see why it should change - How are you connected to the net? through an ADSL router? If so you might have been testing the routers firewall

---

### Post by philinux on 2008-12-10
> **Gone fishing said:**
> Can't see why it should change - How are you connected to the net? through an ADSL router? If so you might have been testing the routers firewall

Yep got a router, same router for a while, but I've done this grc test before and always came back with closed ports.

---

### Post by hyper_ch on 2008-12-10
I wouldn't trust grc.com too much.. I'd rather nmap myself.

---

### Post by iponeverything on 2008-12-10
> **hyper_ch said:**
> i wouldn't trust grc.com too much.. I'd rather nmap myself.

+1

---

### Post by philinux on 2008-12-10
> **hyper_ch said:**
> I wouldn't trust grc.com too much.. I'd rather nmap myself.

Ok hyper, nmap installed. Without wishing to embark on a steep learning curve, just had a look at the man pages. Could you give me a useful command string to test my system and some sort of idea what to look for in the results it spits out. Cheers.

---

### Post by Sarmacid on 2008-12-10
You can try the basic portscan```
nmap <your ip>
```

But I would suggest getting zenmap, it's the graphical interface for nmap.```
sudo apt-get install zenmap
```

---

### Post by philinux on 2008-12-10
Not shown: 1713 closed ports
PORT   STATE SERVICE
23/tcp open  telnet
80/tcp open  http

So I guess this is ok by the look of it.

---

### Post by hyper_ch on 2008-12-10
and you should run nmap from a different computer and not the one you want to have scanned.

---

### Post by philinux on 2008-12-11
> **hyper_ch said:**
> and you should run nmap from a different computer and not the one you want to have scanned.

No can do, only one pc here.

---

### Post by Sarmacid on 2008-12-12
> **philinux said:**
> Not shown: 1713 closed ports
PORT   STATE SERVICE
23/tcp open  telnet
80/tcp open  http

So I guess this is ok by the look of it.

That doesn't seem so ok to me, you have the telnet port open, unless you understand the consequences of having the telnet service up.

---

### Post by philinux on 2008-12-12
> **Sarmacid said:**
> That doesn't seem so ok to me, you have the telnet port open, unless you understand the consequences of having the telnet service up.

This is a default install of ubuntu. No changes at all. That's what nmap shows.

According to grc.com port 23 is closed and 80 stealthed.

How do I get them all stealthed or is there no need.

---

### Post by Sarmacid on 2008-12-12
That doesn't sound right for a default Ubuntu install, try checking if the ports are actually open.

For the 80 go to firefox and type in the address bar [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1)

For the 23, in a console, type```
telnet localhost
```

---

### Post by philinux on 2008-12-12
> **Sarmacid said:**
> That doesn't sound right for a default Ubuntu install, try checking if the ports are actually open.

For the 80 go to firefox and type in the address bar [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1)

For the 23, in a console, type```
telnet localhost
```

80 = Failed to Connect
The connection was refused when attempting to contact 127.0.0.1.
Though the site seems valid, the browser was unable to establish a connection.

23 telnet localhost
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

---

### Post by Sarmacid on 2008-12-12
Seems like there's nothing to worry about, but if you want to have the ports closed by firewall, apply this rules

```
iptables -A INPUT -i eth0 -p tcp -m tcp --dport 80 -d 192.168.0.1 -j DROP
iptables -A INPUT -i eth0 -p tcp -m tcp --dport 23 -d 192.168.0.1 -j DROP
```Changing eth0 for your interface and 192.168.0.1 for your address.

---

### Post by philinux on 2008-12-12
> **Sarmacid said:**
> Seems like there's nothing to worry about, but if you want to have the ports closed by firewall, apply this rules

```
iptables -A INPUT -i eth0 -p tcp -m tcp --dport 80 -d 192.168.0.1 -j DROP
iptables -A INPUT -i eth0 -p tcp -m tcp --dport 23 -d 192.168.0.1 -j DROP
```Changing eth0 for your interface and 192.168.0.1 for your address.

grc.com says they are closed.

---

### Post by Sarmacid on 2008-12-12
Forgot to mention that those rules will be lost next time you reboot, to make them permanent```
sudo sh -c "iptables-save > /etc/iptables.rules"
```
And add this line to your /etc/network/interfaces file```
pre-up iptables-restore < /etc/iptables.rules
```

Bear in mind that if you set up a web server the firewall won't allow access to it, unless you set it on a port other than the default.

---

### Post by philinux on 2008-12-12
Am I ok just leave things as they are set by the default install?

---

### Post by Sarmacid on 2008-12-12
Usually it's fine, but in your case it seems weird you have those ports open. Did you download Ubuntu from a torrent or something like that?

---

### Post by philinux on 2008-12-12
> **Sarmacid said:**
> Usually it's fine, but in your case it seems weird you have those ports open. Did you download Ubuntu from a torrent or something like that?

Ubuntu's website torrent. Hyper_ch said to scan from another pc, maybe thats whats misleading, since grc.com reports them closed.

---

### Post by bodhi.zazen on 2008-12-12
Some information I have not seen posted yet.

First, when you are using a port scanning service, such as shields up, you are scanning your Router, not your computer.

Second, in terms of security there is very little difference between closed and stealth.

---

### Post by philinux on 2008-12-12
All ports seem closed and a couple stealthed so I'll stop bothering worrying. :lolflag:

---

