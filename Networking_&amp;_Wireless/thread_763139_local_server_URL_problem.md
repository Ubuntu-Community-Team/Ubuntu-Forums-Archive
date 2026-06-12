---
title: "local server URL problem"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by pcjunkie on 2008-04-22
I am having some problems with Firefox accessing a local servers xampp stack.

The server name is Jewel and the network id for the system is also jewel.

In XP I can type in [http://jewel](http://jewel) and will be pointed to the active server but in ubuntu 8.04 I get the damn thing redirecting to [www.jewel.com](www.jewel.com). 
[http://jewel/](http://jewel/) is never accepted. 

The only way I can access the server is by IP number (192.168.0.120:80)

ATM I am developing a website, building a POS system and eventually a mail hub so I really need the correct URL to work with folder names. 

[Edit]I fixed the autocomplete URL feature in Firefox [http://support.mozilla.com/en-US/kb/Location+bar+search](http://support.mozilla.com/en-US/kb/Location+bar+search)
but Ubuntu seems to blocking the server. Once again the ip number works ([http://192.168...but](http://192.168...but) it cannot resolve the the server name ([http://jewel/](http://jewel/)) correctly.

---

### Post by blastus on 2008-04-22
I don't know about the web server but on a Linux network you typically access other machines on the network with the notation hostname.local. So if the host name is jewel then you should be able to ping jewel.local

---

### Post by jetsam on 2008-04-23
A quick fix would be to add:
```
192.168.0.120  Jewel
```
to your hosts file /etc/hosts.  Put it after the last ip4 address in the file and before the ip6 stuff that's there.  

There are more complicated and network wide ways of handling name resolution, but the above will work, and it's easy.

---

### Post by pcjunkie on 2008-04-23
> **jetsam said:**
> A quick fix would be to add:
```
192.168.0.120  Jewel
```
to your hosts file /etc/hosts.  Put it after the last ip4 address in the file and before the ip6 stuff that's there.  

There are more complicated and network wide ways of handling name resolution, but the above will work, and it's easy.

Yes, Worked like treat. While I was there I looked at other files, I really like Ubuntu/Linux...This is much easier than a registry.

Browsed to etc using sudo nautilus.
etc/hosts

127.0.0.1	localhost
127.0.1.1	noob-desktop
192.168.0.120   Jasper

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I was able to use [http://jewel/](http://jewel/) 

Thank you.

---

### Post by jetsam on 2008-04-23
Glad it worked.

All the configuration files in Linux can be confusing sometimes to new users, but I agree with you-- the openness of the system is a big plus over Windows.

---

