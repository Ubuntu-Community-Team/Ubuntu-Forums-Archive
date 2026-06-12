---
title: "start vpn on boot"
date: 2018-05-25
forum: Networking &amp; Wireless
---

### Post by jgw on 2018-05-25
running with ubuntu 18.04

It used to be that one had an option to automatically run vpn with network manager.  There may still be one but I cannot find it.

Thank you................

---

### Post by #&amp;thj^% on 2018-05-25
> **jgw said:**
> running with ubuntu 18.04

It used to be that one had an option to automatically run vpn with network manager.  There may still be one but I cannot find it.

Thank you................

See if these are installed:
```
apt policy network-manager-openvpn-gnome openvpn 
```
They are needed for what you want.. so far anyway. You might have to restart network-manager

---

### Post by jgw on 2018-05-26
Thank you for the reply.

I had that installed.  When I ran your suggestion I got:
greg@movies:~$ sudo apt policy network-manager-openvpn-gnome openvpn
[sudo] password for greg: 
network-manager-openvpn-gnome:
  Installed: 1.8.2-1
  Candidate: 1.8.2-1
  Version table:
 *** 1.8.2-1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages
        100 /var/lib/dpkg/status
openvpn:
  Installed: 2.4.4-2ubuntu1
  Candidate: 2.4.4-2ubuntu1
  Version table:
 *** 2.4.4-2ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
        100 /var/lib/dpkg/status

What do I do now?

---

### Post by #&amp;thj^% on 2018-05-26
"gnome" I forgot the exact steps but in short it goes>> right hand corner on panel>>  settings, edit network-conections
and from there I'm sure you will see what you are a custom to.
if I'm to vague just ask, I'll try to clarify. :)

---

### Post by jgw on 2018-05-26
Thanks for the reply.............

What that does is just take one to the system settings/network.   There are no options in any of those settings for running the vpn (the only one is for turning that on and off)  You can also get to your vpn settings themselves and also the advanced settings but there seems to be no place to make it run when the network starts.

---

### Post by #&amp;thj^% on 2018-05-26
Here ya go: [https://blog.matthewurch.ca/?p=331](https://blog.matthewurch.ca/?p=331)
I have to dash for a bit, sorry to hit and run, but I'll be back.:)
EDIT: BTW don't you use PIA Vpn for service?

---

### Post by jgw on 2018-05-26
Thanks for the help.

I cannot find that link in 18.04   Settings are now much different than that   Now you press network, then the gear, then identity which gives you what it has and you can have at it.  However, there is no option to deal with connection when network comes up.

---

### Post by #&amp;thj^% on 2018-05-26
type in terminal:
```
nm-connection-editor
```
 click the gear, then general, then check automatically connect to VPN... and select your openvpn config

---

### Post by jgw on 2018-05-27
Thanks for the reply AND the answer!

Worked great (I am starting to gather quite a list of commands <G>)

---

