---
title: "network works internet doesn't"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by WilliamKB on 2006-10-07
I have been searching the internet for a solution to this problem for 2 weeks and I don't have a clue!

I am having trouble getting to the internet. I have a toshiba laptop (satellite) with atheros wireless network card. I have a home network thru a Linksys wrtg54 wireless broadband router connected to a TimeWarner cable modem (it is the only choice in my apt complex).

Here is the problem, I can get to my home network and access all the other computers on my network but I can't access the internet. I have even turned off all the security (on the router and my laptop - that I know about) and still no internet connection. I don't have a firewall running (that I know of). I also have noticed that I have no internet access when I am wired in, though most of the time I use my wireless.

If I go to a public hotspot, I am able to access the internet with very little trouble.

I am a little new to Linux/Ubuntu so I am not sure what information you might need or how to retrieve it. I would appreciate any help.

---

### Post by ruleboy on 2006-10-07
Try changing the network interface to use DHCP, or if thats set then try a static IP address. 

I had the same problem and setting the network interface to DHCP solved it, the router was set to assign a specific address to the network card and I was assigning the same address as a static ip in the interface settings for the network card in Ubuntu.

---

### Post by WilliamKB on 2006-10-07
I have tried static and dhcp. I get addresses within the range set up on my linksys, except the broadcast address is always one number high. I don't know if that would make any difference or not. (I "X" out my MAC ADDRESSES but they are set up in the linksys)

This is Static IP
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: ath0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 200
    link/ether 00:XX:XX:XX:XX:XX brd ff:ff:ff:ff:ff:ff
    inet 192.16.15.35/29 brd 192.16.15.39 scope global ath0
    inet6 XXXXX::XXX:XXXX:XXXX:XXXX/XX scope link
       valid_lft forever preferred_lft forever
3: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether XX:XX:XX:XX:XX:XX brd ff:ff:ff:ff:ff:ff
4: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0

This is DHCP
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: ath0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 200
    link/ether 00:XX:XX:XX:XX:XX brd ff:ff:ff:ff:ff:ff
    inet 192.168.15.35/29 brd 192.168.15.39 scope global ath0
    inet6 XXXXX::XXX:XXXX:XXXX:XXXX/XX scope link
       valid_lft forever preferred_lft forever
3: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether XX:XX:XX:XX:XX:XX brd ff:ff:ff:ff:ff:ff
4: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0

---

### Post by ruleboy on 2006-10-07
When I had this problem I could ping comuters in my network but not in the internet. And as I mentioned the problem was being caused by interactions between Ubuntu and the router.

So while I can't help much I would be looking over the settings in both places and trying to get them as basic as possible. That the wired interface did not work either is interesting.

If you have other computers in your network try booting one of them from the Ububtu CD and see if you can get the network working from that other computer...that would help narrow the problem down.

---

### Post by WilliamKB on 2006-10-27
I first want to apoligize to ruleboy and to thank him for his help (I hope he sees this).

Second I finally got to setting my linksys back to factory default and one step at a time resetting the security until I found the problem.

It turns out that no matter what MAC I enter in linksys - it won't let my laptop go to the internet. Why, I don't know - but at least it is working now. I had at one time every MAC address I could find (a total of three) entered and it still didn't work.

---

