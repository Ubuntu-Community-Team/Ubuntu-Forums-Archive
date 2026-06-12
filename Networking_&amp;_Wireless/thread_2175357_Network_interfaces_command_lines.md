---
title: "Network interfaces command lines"
date: 2013-09-18
forum: Networking &amp; Wireless
---

### Post by djuvalentin on 2013-09-18
Hey guys,

so here is the deal: I'm new to linux, absolute beginner. I connect to the internet through WiFi and a pppoe connection over it. So far, a have had some problems with the network manager.. As well, when I created the pppoe and connected to it, the first time I rebooted the system, my network manager wouldn't recognize wireless networks. Therefore, i couldn't get the internet to work. After some messing with the 'interfaces' file in the etc/network/ directory, I found out that when I delete the 'iface wlan0 inet manual' command line and restart my machine, the network manager works just fine. So, I would like to know what does that line stand for. What did I do there?

Regards.

---

### Post by Hadaka on 2013-09-18
Hi, you can use either ...
[B]/etc/network/interfaces
               OR
Network Manager
 
[/B]but not both to manage your network.

To use Network Manager

Right click on network manager (the network connection icon)
    Edit connections
    DSL
    Add
    You should be able to work out the rest

Your /etc/network/interfaces
*should only contain these lines.
auto lo
iface lo inet loopback

---

### Post by djuvalentin on 2013-09-24
Yes, mate, but it seems that I can't trigger the dsl connection I make over the wireless (or don't know how to..). The dsl connection becomes available only when I plug in the ethernet cable which I'm not using: wireless connection + broadband connection. Any help?

---

### Post by Hadaka on 2013-09-24
Hi,please post the output of..
```
lsb_release -a
cat /etc/network/interfaces
```
thanks.

---

### Post by djuvalentin on 2013-09-24
Here: 

```
tici@tici-ESPRIMO-E5720:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 13.04
Release:        13.04
Codename:       raring
tici@tici-ESPRIMO-E5720:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
provider dsl-provider


auto wlan0


tici@tici-ESPRIMO-E5720:~$ 
```

---

### Post by Hadaka on 2013-09-24
Hi, please do..
```
sudo gedit /etc/network/interfaces
```
comment out '#' the following lines.
```
auto lo
iface lo inet loopback


#auto dsl-provider
#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
#provider dsl-provider

#auto wlan0
```
save and close gedit
boot.
then follow this link..
[http://www.youtube.com/watch?v=tNlHfM1HgHQ](http://www.youtube.com/watch?v=tNlHfM1HgHQ)

thanks.

---

