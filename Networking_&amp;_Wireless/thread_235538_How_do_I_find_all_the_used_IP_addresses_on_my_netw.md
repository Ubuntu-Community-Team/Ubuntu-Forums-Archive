---
title: "How do I find all the used IP addresses on my network"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by heavyt on 2006-08-13
I am trying to get a list of all the used  ip-addresses on a home network. Is there a command I can type to get a list?
Thanks

---

### Post by lupine_nickt on 2006-08-13
You can scan the network with nmap.

e.g. 'nmap 192.168.0.0/16' will scan 192.168.0.0 - 192.168.255.255

You probably want one of:

'nmap 10.0.0.0/8' (will take ages!)
'nmap 192.168.0.0/24'
'nmap 192.168.1.0/24'

Note that nmap'ing a network that doesn't belong to you will likely result in abuse reports...

xF,

...Nick

---

### Post by NetworkGuy on 2006-08-13
If you are using a firewall router to connect to the internet, and you are using DHCP, you should be able to get this list from your router.  Using NMap will work unless you have devices on your network that won't reply to a ping request (Win XP).

Between this and nmap, you should get the results you need.

---

### Post by heavyt on 2006-08-13
> **lupine_nickt said:**
> You can scan the network with nmap.

e.g. 'nmap 192.168.0.0/16' will scan 192.168.0.0 - 192.168.255.255

You probably want one of:

'nmap 10.0.0.0/8' (will take ages!)
'nmap 192.168.0.0/24'
'nmap 192.168.1.0/24'

Note that nmap'ing a network that doesn't belong to you will likely result in abuse reports...

xF,

...Nick

Thanks, that did the trick. :)

---

### Post by slakkie on 2006-08-13
nmap -sP 192.168.1.0/24 will do the same thing, and not probe for all kind of services. It will only ping the metworks.

---

### Post by Thierry44 on 2006-09-28
You can scan the network with [autoscan]("http://autoscan.free.fr")

---

