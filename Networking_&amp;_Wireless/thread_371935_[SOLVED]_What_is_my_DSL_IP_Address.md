---
title: "[SOLVED] What is my DSL IP Address?"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by arvevans on 2007-02-27
Is there a quick command-line based way for me to find my current network/DSL IP address?

I have a dynamic IP via DSL, and a local Netgear router behind the DSL modem.  My local PCs use 192.x.x.x IP addresses assigned by the local Netgear router which is connected to the DSL modem.

I would like to find a way to build a chron based tool that periodically informs me of my network side (DSL) IP address.  I need this info in a text stream or text file for further processing.

Thanks,
Arv

---

### Post by bapoumba on 2007-02-27
```
 wget http://checkip.dyndns.org/ -O - -o /dev/null | cut -d: -f 2 | cut -d\< -f 1

```
Got it from a friend some time ago. Do not ask me to explain ;)

---

### Post by arvevans on 2007-02-27
**Bapoumba**  

Thanks very much.  I had not thought to use the facilities of dyndns.com for this.
Running the command without all the filtering is interesting and shows pretty much what the post-command filters are doing.

        "wget [http://checkip.dyndns.org/](http://checkip.dyndns.org/) -O - -o /dev/null"
        "wget [http://checkip.dyndns.org/](http://checkip.dyndns.org/) -O - -o /dev/null | cut -d: -f 2 | cut -d\< -f 1"


FYI:  The use is to allow a few select friends become aware of my current network IP so they can access my local servers.  This info may then be of value to others with similar situations.

Thanks again,

Arv

---

### Post by bapoumba on 2007-02-27
You're welcome and thanks to you.
Let me give him credits (he is cep, a real debian wiz):
[http://forum.ubuntu-fr.org/viewtopic.php?pid=530625#p530625]("http://forum.ubuntu-fr.org/viewtopic.php?pid=530625#p530625")
It's in French, but the commands are the same ;)

One more thing, get it in a nice box (not so useful to your friends, but fun anyway):
```
 zenity --info --text=" `wget http://checkip.dyndns.org/ -O - -o /dev/null | cut -d: -f 2 | cut -d\< -f 1 ; /sbin/ifconfig eth0 |grep inet\ adr | awk '{ print $2} ' |cut -d: -f 2 `"

```

---

### Post by eggdeng on 2007-02-27
Olé!

---

### Post by arkangel on 2007-02-27
ok  i can access my router , how can i access my Laptop  and do an ssh from outside to it ?  ;)

---

### Post by arvevans on 2007-02-27
**arkangel**

_Partial answer:_  Assuming that your laptop has a static IP address on your LAN, go into the router configuration and set up IP Forwarding for the specific function (by IP port number) to your laptop.  You will be mapping say port 80 (HTTP) so that all external calls to HTTP that enter your router from outside will be forwarded just to your laptop.

If your laptop has a dynamic IP address (i.e. local DHCP served address) some routers will still allow you to do port forwarding based on the host name of your laptop.  Others may allow port forwarding to happen based on MAC address.

Which method you have to use really depends on your router and how it is configured.

As to SSH, someone more familiar with the process can probably do a better job that me in this area.

Arv
_._

---

