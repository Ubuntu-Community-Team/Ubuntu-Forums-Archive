---
title: "ubunto as a gateway howto?"
date: 2004-12-22
forum: Networking &amp; Wireless
---

### Post by snipes420 on 2004-12-22
My network is setup like this:

I have a 4 port broadband router with DHCP/NAT and DSL on the WAN and 4 computers are plugged in to the router.
-a Mac OS X machine(roomates)
-a windows XP Machine(roomates)
-a ubuntu machine(my file/backup server)
-my ubuntu workstation

Now since I am out of spare ports on my router, I added a second NIC to the file/backup server hoping to use it as a gateway so my xbox can go online for xbox live and such. But the network card does not show up when I type "ifconfig". 
It also doesn't show up when I go to Computer > System Configuration > Networking.
only the original integrated NIC shows up. 

im not sure if I am going about this the right way.

I've looked around but I dont see any howtos to make a gateway. Can you help me?

Thanks

Edit: A bridge would work good for me too because the router will support more than 4 ip addresses. I found this article, [Bridging](http://www.ibiblio.org/mdw/HOWTO/Bridge/x23.html) MiniHowto and the first paragraphs make me thing that linux isnt even trying to find the second nic. I have to tell it to look for a second one in the lilo.conf file but ubuntu uses grub not lilo. ?

Edit: Heh, well I went too look again and the second network card _was_ in the list in the Networking window so I activated it and set it to activate on boot.  Ive installed firestarter on the file server and went through the wizard and think It is set up properly. The XBox is set to use DHCP now but it doesnt get any connection.

---

### Post by mistic on 2004-12-25
I just made my PC a gateway to the network connected to it on the secondary card, for that i used iptables...

a great tutorial can be found here:
[here](http://iptables-tutorial.frozentux.net/iptables-tutorial.html) 

grtz
Mistic

---

### Post by snipes420 on 2004-12-25
ok, now does anyone have a howto to mistics howto?  ;) 
just kidding I'll try to see what I can do with it.

Edit: Well sorta reading that helped me find another howto on google. its a lot shorter because it gives you only what you need to know for this exact thing. 
[Masquerading Made Simple HOWTO](http://www.tldp.org/HOWTO/Masquerading-Simple-HOWTO/) 
Thanks mistic

PS dont goto that ipmasq.cjb.net link, its no longer there

---

### Post by zenwhen on 2004-12-25
It is really rather simple. 

sudo apt-get install squid dnsmasq ipmasq

Set up squid as a local web cache to save yourself and the webmasters who give you free information bandwidth.

[http://squid.visolve.com/squid/sqguide.htm](http://squid.visolve.com/squid/sqguide.htm)

Set up dnsmasq as a dhcp server / dns server.

[http://www.enterprisenetworkingplanet.com/netos/article.php/3377351](http://www.enterprisenetworkingplanet.com/netos/article.php/3377351)

Now, ipmasq will provide you with NAT, dnsmasq with DHCP, and squid with caching. Clients will be able to grab an IP from your server's allowed range or take an IP based upon their MAC address. The individual guides will help you more than I can. :)

---

### Post by senectus on 2004-12-28
I know it's an odd question.. but can you get squid to cache EVERYTHING?
As in binaries downloaded from http?
So If I have a Windows PC that does an update, can I get the squid server to cache those .exe files etc so that any other windows PC's can get them locally/transparently?

---

