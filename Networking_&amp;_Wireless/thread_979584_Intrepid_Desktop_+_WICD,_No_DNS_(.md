---
title: "Intrepid Desktop + WICD, No DNS :("
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by NitroBooster on 2008-11-12
I have it configed like this:
[https://www.opendns.com/smb/start/device/ubuntu](https://www.opendns.com/smb/start/device/ubuntu)

/etc/wicd/wired-settings.conf
> 
[wired-default]
afterscript = None
broadcast = 0.0.0.0
dns3 = 95.13.100.1
ip = 95.13.100.216
dns1 = 208.67.222.222
use_static_dns = 1
default = True
netmask = 255.255.255.0
dns2 = 208.67.220.220
beforescript = None
disconnectscript = None
gateway = 95.13.100.1
use_global_dns = 0


/etc/resolv.conf
> 
nameserver 208.67.222.222
nameserver 208.67.220.220


I got no DNS at all :(

---

### Post by Sealbhach on 2008-11-12
Did you change these files? As suggested on that link?

```
$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ gksudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
```


.

---

### Post by NitroBooster on 2008-11-12
Yes I did.

does my user need to be part of some group?

because nslookup seems to work only under root

If I wanted to wipe everything networking related clean, and start over, how do I go about it?

Also, where are the wicd profiles stored? It seems to not be using the conf files in /etc/wicd

---

### Post by Sealbhach on 2008-11-13
Sorry dude, I don't know anything about wicd. How come you could'nt use Network Manager?

What kind of network card have you got?


.

---

### Post by NitroBooster on 2008-11-13
It seems the problem was with my distro of wicd

I ended up reinstalling a different distro from
[http://apt.wicd.net/dists/intrepid/all/](http://apt.wicd.net/dists/intrepid/all/)

and voila!

---

### Post by Sealbhach on 2008-11-13
That's good. It would be a good idea to mark this thread as solved so it can help others find a solution.


.

---

