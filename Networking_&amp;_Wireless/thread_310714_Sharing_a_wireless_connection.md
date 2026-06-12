---
title: "Sharing a wireless connection"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by goofdawg on 2006-12-01
Here's my situation:

I use Wireless-B to connect my Ubuntu box in my bedroom to the internet. It has two nics and I have a spare hub. I want to be able to route traffic from that hub over the wireless network, purpose being to hook up my Xbox to the internet without buying M$'s $100 wireless adapter.

I tried using Firestarter to set up internet connection sharing, wlan0 as my primary internet connection, eth0 as my local network, and set to run DHCP. As soon as I turn the firewall on, I can't get on the internet any longer.
Opening up Network Settings shows my default net connection has been switched to eth0, and I can't change it. I have to disable eth0 to get back online.

Any help is much appreciated. Has anyone else tried to share a wireless connection like this?


Thanks
goofdawg

---

### Post by goofdawg on 2007-02-02
bump

---

### Post by Mushed on 2008-03-01
bump bump

---

### Post by superprash2003 on 2008-03-01
firestarter didnt work for me too...maybe this can help you setup internet connection sharing [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by Mushed on 2008-03-02
did you get yours working using that site? If so, post your findings. (please. =]

---

### Post by superprash2003 on 2008-03-03
otherwise.. try the following commands.. first go to the terminal and type sudo -i .. and enter your password.. then type the following commands

ifconfig eth0 (whatever ip you want for your internal network eg 192.168.0.1)
iptables -A FORWARD -i wlan0 -o eth0 -s (ip of your wlan0 eg 192.168.1.2) -m state --state NEW -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE 
sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

if possibile..manually setup your xbox ip to 192.168.0.2 if you followed the example ip's in this tutorial

---

### Post by darkmdbeener on 2008-03-10
i wasnt able to get this to work. is there anoughter way


nothing i am doing is seeming to work

---

