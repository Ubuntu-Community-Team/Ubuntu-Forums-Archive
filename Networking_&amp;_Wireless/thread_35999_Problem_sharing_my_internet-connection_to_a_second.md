---
title: "Problem sharing my internet-connection to a second pc"
date: 2005-05-21
forum: Networking &amp; Wireless
---

### Post by TopasPV on 2005-05-21
Hi!
First i wana apologize for this post. I'm quite sure there is another post which gives the answer i'm looking for but after a whole day of searching through this and other forums, trying different programs and asking myself dumb questions i'm completely exhausted. I just can't find any usefull help.

The facts:
I have two computers running. PC 1 is a pentium with 700mhz which I want to use as a server. PC 2 is an AMD 2400+ which I use for my work, some games and some other things. Both have network cards and are connected by a network cable. PC 2 has a normal 10/100 mbit card while PC 1 owns something like an internal network hub. This card offers four ports. Through this card PC 1 is connected to the internet via DSL and to PC 2 via LAN. So I want to share the internet connection to the whole network and so make it reachable for PC 2. I know that the whole hardware is running because everything was fine when I used windows (where I knew how to configure it correctly ;-)).
The two computers are able to ping each other and PC 1 is able to access the internet. But as I mentioned before I want PC 2 to be able to access the internet, too. I tried to use Firestarter but somehow it didn't work correctly. Someone advised me to use ipmasq instead but I wasn't even able to run this programm after I had installed it.
So I realy hope someone can help me to configure my network correctly.

Thanks for reading.

---

### Post by stevenyu on 2005-05-21
When you setup the 2nd PC, just make sure it have gateway point to the 1st PC

---

### Post by TopasPV on 2005-05-22
[QUOTE=stevenyu]When you setup the 2nd PC, just make sure it have gateway point to the 1st PC[/QUOTE]
It has :)
But somehow it doesn't work. As an additional hint: The network hub is recognized as one single network card (the same under windows) and so needn't be installed in another way then other cards.

---

### Post by TopasPV on 2005-05-22
YEEEEEHAAAA!
As u can gues, i figured out :)

Someone helped me and found out about my problem. He handed me out a little firewall script that runs quite perfectly. The only thing I had to do was to install this script and then add some dns-information to PC 2.

---

### Post by dominik on 2005-05-22
Setting up Connection Sharing is pretty handy with Firestarter: [http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

---

### Post by TopasPV on 2005-05-22
[QUOTE=dominik]Setting up Connection Sharing is pretty handy with Firestarter: [http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)[/QUOTE]
I tried it like that but unfortunately it did not work.

---

### Post by lgl on 2005-05-23
Any chance of a deeper explanation of how your problem was fixwed as I am having a similar problem except that my pc with the adsl connection is a windows pc.

[my thread](http://ubuntuforums.org/showthread.php?t=35219) 

 ](*,)

---

### Post by TopasPV on 2005-05-23
Of course, i can tell u a bit more about how i fixed my problem. Luckily i found another post about this issue that helped me out. It was [http://www.ubuntuforums.org/showthread.php?t=5854&highlight=nameserver+forwarding](http://www.ubuntuforums.org/showthread.php?t=5854&highlight=nameserver+forwarding)

where is described how to configure ur /etc/network/options to forward ips. 

"[~] > cat /etc/network/options
ip_forward=yes
spoofprotect=yes
syncookies=yes"

After this i tried to install Firestarter again (cause the old script didn't work anymore - don't ask y :-)) and nearly everything worked. I could ping IPs and only had to add my prefered DNS to be able to visit any website again. If ur client is running windows u'll have no diffuculties to add ur dns. If it's runnin ubuntu u'll have to edit ur /etc/resolv.conf.

May the Force be with u ;-9

---

