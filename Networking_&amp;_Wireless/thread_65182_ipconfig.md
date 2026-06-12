---
title: "ipconfig???"
date: 2005-09-13
forum: Networking &amp; Wireless
---

### Post by X5-655 on 2005-09-13
how do I do a command in linux, that is like ipconfig release/renew?

I need to release the IP of a computer, and renew it, due to a network change..

---

### Post by frodon on 2005-09-13
ifconfig

---

### Post by heimo on 2005-09-13
release:
 ```
sudo dhclient -r
``` 

lease:
 ```
sudo dhclient
``` 
you can add eth0 or other network interface after those commands (I think it can be omitted in most cases)

Hmm... but it may be that all you're after is this:
 ```
sudo /etc/init.d/networking restart
```

---

### Post by X5-655 on 2005-09-13
[QUOTE=frodon]ifconfig[/QUOTE]
ok, then what else?  i don't know how to use that command, i enter ifconfig --help, but all it told me was nothing i could understand..

I need a command that will tell my router "DHCP_RELEASE"..

---

### Post by X5-655 on 2005-09-13
[QUOTE=heimo]release:
 ```
sudo dhclient -r
``` 

lease:
 ```
sudo dhclient
``` 
you can add eth0 or other network interface after those commands (I think it can be omitted in most cases)

Hmm... but it may be that all you're after is this:
 ```
sudo /etc/init.d/networking restart
```[/QUOTE]
thanks, that command worked perfect, and now I got the new IP settings from the router!  :)

EDIT: the dhclient one worked..  i didn't try the other one, as i needed more than just restarting the networking device, but needed to send "DHCP_RELEASE" to the router, in which dhclient did, and even rebooting ubuntu did not do...

---

