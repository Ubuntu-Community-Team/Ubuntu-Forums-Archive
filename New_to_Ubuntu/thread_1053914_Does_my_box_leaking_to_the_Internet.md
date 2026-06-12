---
title: "Does my box leaking to the Internet?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by unf4b1x on 2009-01-29
As you login, if your internet connection is active but you are not browsing or doing anything, does it always show that other ip addresses seem to be connecting to you? Because I could see that using etherape who is capturing on any interfaces other ip addresses seems connecting to my box. And checking it using the command: ```
sudo netstat -pantu
``` ..it shows havp/cupsd/nessusd: waiting/darkstat/avahi-daemon on a listening state... and also upon checking it on grc.com's Shield's Up using galeon browser...it shows ok... got a nonresolvable ip... then upon checking using the All Service Ports.. it showed a stealthed ports and I passed... but the thing is my modem is actively doing something... as well as etherape's graphical view Can somebody please help! I still don't know how to check this.

---

### Post by lazyart on 2009-01-29
Welcome to the internet.

---

### Post by 3rdalbum on 2009-01-29
If all ports are stealthed, it means nothing outside your network can connect to you. The other services are either listening to "localhost" only, or are accepting connections across your network, and are being protected by your broadband modem's firewall.

---

### Post by unf4b1x on 2009-01-29
> **3rdalbum said:**
> ... are accepting connections across your network, 
Do you mean "accepting connections on my ISP's network or mine? 

Are there any other way, maybe, using another application to check if I got open/close or hidden applications using some of my ports from within besides netstat?

---

### Post by xpod on 2009-01-29
> Are there any other way, maybe, using another application to check if I got open/close or hidden applications using some of my ports from within besides netstat?

You could install [nmap](http://nmap.org/) to scan your computers/network.
```
sudo apt-get install nmap
```
Or,you could try [Shieldsup](https://www.grc.com) for checking which ports you have open/closed/stealthed to the outside world.

---

### Post by unf4b1x on 2009-01-29
> **xpod said:**
> You could install [nmap](http://nmap.org/) to scan your computers/network.
```
sudo apt-get install nmap
```
Or,you could try [Shieldsup](https://www.grc.com) for checking which ports you have open/closed/stealthed to the outside world.

Thanks, but I already have done that with Shiedsup.  It looks fine though. 

I'm going to read more about nmap and maybe try some of its commands.. I think I'm going to do a trial and error here. I'm sure netstat has limits to its capabilities to scan ports on localhost. Or, maybe I am just missing some points here in using netstat. What dyou think?

---

### Post by Nepherte on 2009-01-29
You should really be running netstat from another computer than the one you are scanning to see if it is really accessible.

---

