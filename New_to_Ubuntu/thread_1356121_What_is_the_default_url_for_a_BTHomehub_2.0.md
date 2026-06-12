---
title: "What is the default url for a BTHomehub 2.0?"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by bwallum on 2009-12-15
Hi

I am trying to connect to a BTHomehub using a wired ethernet connection.

The manual says to put [http://bthomehub.home](http://bthomehub.home) into a browser. This doesn't work for me. Firefox insists on putting www in front of the url and 'server not found' error ensues.

Does the BTHomehub 2.0 have a traditional number style url? e.g 192.168.1.254 (which is the default url for the BTBusinesshub)

---

### Post by northern lights on 2009-12-15
I have no experience with that particular device, but have you tried pinging it?

What does```
ping bthomehub.home
```yield?

---

### Post by NoaHall on 2009-12-15
Try [http://192.168.1.1/](http://192.168.1.1/)

---

### Post by 3rdalbum on 2009-12-15
I think it's [http://192.168.0.1](http://192.168.0.1)

The Home Hub is not much of a hub, it only has two Ethernet ports ;-)

---

### Post by bwallum on 2009-12-16
The 2.0 version has 4 ethernet ports so maybe we have two different devices in mind.

If I want to force Firefox to only try to connect to [http://bthomehub.home](http://bthomehub.home), what prefix do I use?

---

### Post by gary0 on 2009-12-16
It is definately 192.168.1.254. I have just set one up as an AP on my network (not connected to phone line), and did a factory reset beforehand. The book of words states the above IP is the default one for the hub. By the way, works very well as an AP.

Gary.

---

### Post by Grenage on 2009-12-16
When in doubt: You know that you have a DHCP lease from the router, and that the default gateway you were given in the lease is the IP of the router.

Therefore:

```
route -n
```

Will reveal the IP address (destination 0.0.0.0).  On a BT router it's usually 192.168.1.254.

---

### Post by HermanAB on 2009-12-16
You can always guess these addresses.  Look to see what is your computer IP address:
$ /sbin/ifconfig

Say it shows 192.168.1.200

Your router address will then be either 192.168.1.1 or 192.168.1.254 and you can test it either by simply connecting with a browser,telnet or ping.

The address should also appear in /etc/resolv.conf. For example:
$ cat /etc/resolv.conf
nameserver 192.168.1.254

---

### Post by NE Key on 2009-12-16
192.168.1.254

---

### Post by 3rdalbum on 2009-12-16
I just set up a similar modem today. Sorry my memory failed me. It's not 192.168.1.1, it's 192.168.1.254.

---

### Post by markyb73 on 2009-12-16
yep definately 192.168.1.254 if its the black one :)

---

### Post by bwallum on 2009-12-16
Finally made connection! 

I used the [http://bthomehub.home](http://bthomehub.home) url. Initially Firefox insisted on putting www on so the url became [http://www.bthomehub.home](http://www.bthomehub.home), which failed.

So I stopped the 'Domain Guessing' function in Firefox by:

type about:config into the location bar

search for 'fixup'

select browser.fixup.alternative.prefix and then set to false by clicking on it.

It is then possible to locate [http://bthomehub.home](http://bthomehub.home)

The [http://192,168.1.254](http://192,168.1.254) did not work for me and I have not found out why.

Thanks everybody!

---

