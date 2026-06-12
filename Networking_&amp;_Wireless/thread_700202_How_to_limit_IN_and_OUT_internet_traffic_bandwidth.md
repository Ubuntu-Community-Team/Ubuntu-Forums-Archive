---
title: "How to limit IN and OUT internet traffic bandwidth on a gateway/proxy pc"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by Robertobg on 2008-02-18
Good morning,
i'm trying to install and configure a pc as proxy server for my lan to limit the adsl bandwidth (in and out) for some pc.
So i start installing Squid but once i installed it i found that it is not possible to limit outgoing traffic but only incoming traffic (perhaps only download and not web surf, i don't understand).

Is it possible to limit the bandwidth in a simple way setting up 2 value: incoming and outgoing speed for the pc's that will use this pc as proxy server?

I wish to do: every client pc that use the specific pc configured as proxy server (using squid?) will share only 30 KB / incoming (web browsing, downloading, ftp,  pop3, video streaming ...)  and 20 KB / outgoing (web browsing, smtp, upload, ftp, chat ...) of traffic bandwidth.
Without any other control, only 2 value: 30KB incoming and 20 KB outgoing.

Please help me, i have read many faq and manuals (iptables ?!) but i have not found a simple solution at my capacity.

Thanks and best regards.
Roberto

---

### Post by SpaceTeddy on 2008-02-18
i have done quite a bit of researching on this topic myself... and it was painful !

The first thing i had to get used to was, you cannot shape the incomming traffic on any machine, you can only limit the outgoing capacity. But that is no problem, since shaping outgoing is acctually enough to share bandwidth...

what you want to look at is the programm tc (traffic control). it is pretty cryptic and hard to get into... but once you sorta get to know it, it grows on you

a quickstart can be found here [http://www.hackosis.com/index.php/2007/11/08/linux-router-bandwidth-management-example/]("http://www.hackosis.com/index.php/2007/11/08/linux-router-bandwidth-management-example/")

and the full howto is located at [http://tldp.org/HOWTO/Adv-Routing-HOWTO/index.html]("http://tldp.org/HOWTO/Adv-Routing-HOWTO/index.html")

also, since you might need to setup the tc on a changeing network interface, you will need to use tc in conjunction with iptables... here is what i do to shape my traffic. Setup is that everyone in the internal network can chew up to 824kit/sec, and that 200kbit/sec are purley and only reserved for the running webserver. Of course, if you use this, you will need to modify the classes and the iptables setup :)

> # cat /bin/tc.sh
#delete old traffic shaping
/sbin/tc qdisc del dev ppp0 root 2> /dev/null

#create root device
/sbin/tc qdisc add dev ppp0 root handle 1: htb default 22

#create root class
/sbin/tc class add dev ppp0 parent 1: classid 1:1 htb rate 1024kbit ceil 1024bit burst 1024k

#create bandwidth classes
/sbin/tc class add dev ppp0 parent 1:1  classid 1:11 htb rate 200kbit ceil 500kbit burst 30k prio 2
/sbin/tc class add dev ppp0 parent 1:1  classid 1:12 htb rate 824kbit ceil 800kbit burst 1024k prio 1

#create fair share handles
/sbin/tc qdisc add dev ppp0 parent 1:11 handle 11: sfq perturb 10
/sbin/tc qdisc add dev ppp0 parent 1:12 handle 12: sfq perturb 10

#other classes
/sbin/tc filter add dev ppp0 protocol ip parent 1: prio 1 handle 1 fw classid 1:12
/sbin/tc filter add dev ppp0 protocol ip parent 1: prio 2 handle 2 fw classid 1:11


and the coresponding iptables rules for it
> 
#put everything that goes out in handle 1
-A OUTPUT -j MARK --set-mark 0x1 
# put everything the webserver sends out in handle 2 (restrcited to 200kbit/s)
-A OUTPUT -p tcp -m tcp --sport 80 -j MARK --set-mark 0x2 


about limiting the IN traffic (what comes from the Internet, i presume) is the same as limiting the OUT to internal hosts. so you don't really need to limit an in... OUT is quite enought :)

i hope at least some of it makes sense to you... and you are quite welcome to keep asking question. i'll try (?!) to answer then as best i can

---

