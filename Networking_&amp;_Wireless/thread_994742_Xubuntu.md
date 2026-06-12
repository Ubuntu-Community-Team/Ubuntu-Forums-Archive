---
title: "Xubuntu"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by radu1984 on 2008-11-27
Hi all and great to be here ! I am from Romania , Timisoara ! I have installed last night XUBUNTU 8.10 and i want to know how to make my download work better , i am on CABLE not on MODEM or WIRELLES ! Were and how to make my internet conection work best ? Thanks !

---

### Post by rlzyoner on 2008-11-27
The most influential factor that affects your download speed is the bandwidth that your ISP provides, 1meg, 2meg 3meg or whatever.
Have you perforemed any speedtests to determin what your download speeds actually are ?
Also, sometimes, manually entering the DNS addys into your network connection can speed things up just a little as the machine does not have to resolve these addys each time.

---

### Post by radu1984 on 2008-11-27
> **rlzyoner said:**
> The most influential factor that affects your download speed is the bandwidth that your ISP provides, 1meg, 2meg 3meg or whatever.
Have you perforemed any speedtests to determin what your download speeds actually are ?
Also, sometimes, manually entering the DNS addys into your network connection can speed things up just a little as the machine does not have to resolve these addys each time.

Ies i know , i have a 10 Megabits download speed and i usually downloaded torrents , on windows witch i hate allready , with 6 megabits , and now the same fille with only 200 kb or so ! Some help please and thanks allot !

---

### Post by rlzyoner on 2008-11-27
Torrent config aint my strong point but can you confimr that the necessary ports are opened on your router.
Which client are you using for torrents on xubuntu.
Are you running any firewalls that may affect the downstream speed

---

### Post by radu1984 on 2008-11-29
> **rlzyoner said:**
> Torrent config aint my strong point but can you confimr that the necessary ports are opened on your router.
Which client are you using for torrents on xubuntu.
Are you running any firewalls that may affect the downstream speed

Hi and thank you ! I dont know wich is the best *.torrent client in xubuntu, in windows i was using Bittorrent and / or  Utorrent ! Maybe il try with Wine ! Is there any firewall or antivirus on xubuntu allready installed ? I dont have a router , my internet cable comes from outside the electric and thelephone poll and its a simple cable thats plugd in to my network board !
Hellp please ! And thank you !

---

### Post by J172 on 2008-11-29
Its plugged directly into your computer or did you mean your cable modem?

Applications -> Internet -> Transmission BitTorrent Client in UBUNTU (GNOME)

If its not on your computer open a terminal and try 
**sudo apt-get install transmission**
Enter your password, wait a sec and press **y** and then enter.

It should install it for you. 

Also speedtest.net is a good speed test site. (atleast here in the states).

Hope this helps a bit.

Xubuntu/Ubuntu contains a firewall program called iptables. 
Here is the project homepage: [http://www.netfilter.org/projects/iptables/index.html](http://www.netfilter.org/projects/iptables/index.html)

---

### Post by radu1984 on 2008-11-29
> **J172 said:**
> Its plugged directly into your computer or did you mean your cable modem?

Applications -> Internet -> Transmission BitTorrent Client in UBUNTU (GNOME)

If its not on your computer open a terminal and try 
**sudo apt-get install transmission**
Enter your password, wait a sec and press **y** and then enter.

It should install it for you. 

Also speedtest.net is a good speed test site. (atleast here in the states).

Hope this helps a bit.

Xubuntu/Ubuntu contains a firewall program called iptables. 
Here is the project homepage: [http://www.netfilter.org/projects/iptables/index.html](http://www.netfilter.org/projects/iptables/index.html)


plugged directly into my computer , and can i disable that firewall ? Wont i get ""visitors"" ?

---

### Post by ugm6hr on 2008-11-29
> **radu1984 said:**
> plugged directly into my computer , and can i disable that firewall ? Wont i get ""visitors"" ?

You don't want to disable your firewall if you don't have a router performing that function.

You can just open the port that your torrent engine uses with ufw (or gufw):
[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

---

