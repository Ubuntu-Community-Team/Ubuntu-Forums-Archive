---
title: "sudo: unable to resolve host"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by Rumpletumbler on 2010-08-10
I've checked the threads here with the same title and none are applicable to whatever I have going on that I can tell. 

127.0.0.1    localhost
127.0.1.1    hostname.

is what I have now. The rest is cutout because I have a lot of blocked addresses in the file. 

I was initially experiencing sendmail errors in the logs because the hostname couldn't be qualified. 

I read somewhere to put a period after the hostname and it would fix this. 

It did fix it but I get sudo unable to resolve host now. 

/etc/hosts and /etc/hostname both match 

This happens as well if I use hostname.desktop or whatever in both files. If I go back to the single name it breaks sendmails ability to get the hostname. 

Edit: when I boot I get "init hostname main process (number) terminated status 1

Any ideas?

---

### Post by Brandon Williams on 2010-08-11
When you say "/etc/hosts and /etc/hostname both match", do you mean that you added a dot at the end of the hostname in /etc/hostname, too? In order for sudo to be able to resolve your hostname, there should be a label in /etc/hosts that matches the value in /etc/hostname exactly. When you added the dot to /etc/hosts, you would also have had to add a dot in /etc/hostname. Alternatively, without changing /etc/hostname, you could have done this in /etc/hosts:
```
127.0.1.1 hostname hostname.
```

---

### Post by bodhi.zazen on 2010-08-11
You may need to add a line for your hostname.

127.*.*.* is localhost and probably not sufficient.

You probably need at least your LAN and a FQDN

192.168.0.x FQDN

You may need to also add your public IP as well.

---

