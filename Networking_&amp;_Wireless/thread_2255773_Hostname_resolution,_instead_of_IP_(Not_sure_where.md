---
title: "Hostname resolution, instead of IP (Not sure where to post)"
date: 2014-12-07
forum: Networking &amp; Wireless
---

### Post by Robert_Marvin on 2014-12-07
I'm migrating a website/database from a crappy windows 7 machine with Wampstack to LAMP on ubuntu. I have everything set up, but i am lost when it comes to having the computer name be the url. If i use the IP address "http://IP/index.php" it goes to the php i have setup. But, if i use the "http://hostname.domain/index.php" it is not working... How can i have the same hostname to ip resolution i used on the windows 7 machine? Everything will be used on a local intranet, no need for external DNS support...

---

### Post by praseodym on 2014-12-07
Its the file /etc/hosts. Example
```

127.0.0.1     localhost
127.0.1.1     jupiter

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
With hostnames in it
```

127.0.0.1      localhost
127.0.1.1      jupiter

# <IP-Address>  <computer name(s)>
[COLOR="#FF0000"]192.168.0.1    jupiter.homenetwork jupiter
192.168.0.2    mars.homenetwork mars
192.168.0.3    saturn.homenetwork saturn[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by Robert_Marvin on 2014-12-07
This works great for accessing it locally on maybe 1-2 comps. I will be using this on many other computers, all managers in an entire warehouse plus kiosks to send data to a sql table. Are there any other ways to accomplish this, other than manually editing the hosts files?

---

### Post by praseodym on 2014-12-07
Try [http://avahi.org/](http://avahi.org/) you may need to install

```
sudo apt-get install libnss-mdns 
```
afterwards the other PCs can be pinged, the names are *.local, e.g.

```
ping name.local 
```
It opens the ports 5353 and someone in the area 32768. Check it via

```
sudo netstat -tulpen | grep avahi 
```
More information on the project site or here (German!) with some tools from the repos:

[http://wiki.ubuntuusers.de/avahi](http://wiki.ubuntuusers.de/avahi)

You might want to translate it via Google ;)

---

