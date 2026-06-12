---
title: "Sharing Wi-Fi over ethernet cable"
date: 2016-02-07
forum: Networking &amp; Wireless
---

### Post by blake17 on 2016-02-07
Lately, I have been using my ubuntu laptop to share my wifi connection over an ethernet cable, as my desktop pc has no wireless card #-o .  It works great for browsing the internet, playing games, etc.... however when I turn on my ftp server, or any other server for that matter, it doesn't seem to be able to make it onto my other devices in my local area network, (phone, tablet).  I assume this has something to do with the connections not being sent through the ubuntu laptop or something of the sort.  What I'm trying to ask is, how do I make it so that web servers are accessible on my other devices?  Thanks

-Blake :D

---

### Post by blake17 on 2016-02-09
Bump

---

### Post by SeijiSensei on 2016-02-10
I don't understand the question. If the other devices like your phone and tablet support wifi, they should be connecting directly to the wifi router and have full Internet access already just like the laptop.

---

### Post by QIII on 2016-02-10
Does your router have both wifi and wired connectivity?

I am also confused about what you are trying to achieve here.

---

### Post by blake17 on 2016-02-10
Sorry for any confusion I may have caused :oops: .  So basicly, I have an wifi connection at home, but my desktop pc has no wifi card so it is unable to connect to it.  So, I use my ubuntu laptop to share the wifi connection over to my pc via ethernet cable.  My problem, is when I host any sort of web server on the desktop pc, I'm not able to connect to it on any other devices EXCEPT for the laptop thats being used to share the wifi.  I am wondering if I can make it so that the connection passes through the laptop and into my actual network.  Again, sorry for any confusion.

-Blake

---

### Post by blake17 on 2016-02-10
Sorry for any confusion I may have caused :oops: .  So basicly, I have an wifi connection at home, but my desktop pc has no wifi card so it is unable to connect to it.  So, I use my ubuntu laptop to share the wifi connection over to my pc via ethernet cable.  My problem, is when I host any sort of web server on the desktop pc, I'm not able to connect to it on any other devices EXCEPT for the laptop thats being used to share the wifi.  I am wondering if I can make it so that the connection passes through the laptop and into my actual network.  Again, sorry for any confusion.

-Blake

edit, I see my post has been posted twice XD

---

### Post by SeijiSensei on 2016-02-10
It's pretty likely a routing problem and probably requires adding an entry to the routing table on your wifi router.  Suppose the desktop has address 10.10.10.10 connected to the laptop's Ethernet port with address 10.10.10.1.  Also suppose the wlan0 interface of the laptop has address 192.168.1.2.  On the wifi router you would need to add a route equivalent to this command in Linux:
```
ip route add 10.10.10.0/24 via 192.168.1.2
```
Your router will likely have its own method for entering routes.  This tells the wifi router to send traffic from machines on the 192.168.1.0/24 network to machines in 10.10.10.0/24 via the laptop rather than out to the Internet as is the router's default. 

You will also need to exempt traffic between 10.10.10.0/24 and 192.168.1.0/24 from being masqueraded by the laptop.  In iptables on the laptop I'd use something like this:
```

/sbin/iptables -t nat -s 10.10.10.0/24 -d 192.168.1.0/24 -j FORWARD
/sbin/iptables -t nat -o wlan0 -j MASQUERADE

```
That leaves traffic between the two internal networks unmasqueraded while masquerading all other traffic sent out wlan0.

This stuff is very tricky to set up, so I'm just giving you some ideas that you can adapt to your own situation.

---

### Post by blake17 on 2016-02-11
I appreciate the help, Thanks :)

---

