---
title: "Azureus says: NAT problem!"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by sohaibma on 2007-04-28
I just installed Azureus on my Feisty system. During the configuration wizard, when Azureus asks for the TCP listening port, and I select the default port (48572). It displays NAT error. How can I bypass this error. 

Noe: All bittorrent clients work fine in windows, so its not my Siemens Speedstream router which is not allowing connections.

please help me here

---

### Post by timczer on 2007-04-28
Are you using a firewall?  You may need to open that port in your firewall.  Also, you may need to go into your router setup and forward that port from your router to your computer.

---

### Post by sohaibma on 2007-04-28
1) no i'm not using any firewall, but i heard there is a built-in firewall in ubuntu.
2) about the port forwarding, if i haven't forwarded any ports how is torrent working in windows xp on the same computer

please help me

---

### Post by fwojciec on 2007-04-28
Torrent clients will work even if ports are not forwarded - Azureus is just particularly vocal anout NAT problems (It will download files in either case).  Are you sure your Windows Torrent client connects to other clients directly (as in, there is no NAT error)?

---

### Post by sohaibma on 2007-04-28
I use bitcomet on windows xp on the same network. And it works very well, i get downloading speeds upto 100kb/s. But in ubuntu on the same pc, the speeds are very slow, and azureus shows the NAT error.

what could it be? Do i have to open specific ports for azureus? If yes then how do i open those ports?

---

### Post by fwojciec on 2007-04-28
I've never used Bitcomet (it has very bad reputation in torrent community, and is banned on some trackers, or was...), but compared to Bittornado, for example, Azureus is pretty slow.

You can improve torrent download speeds, in general, if you set up port forwarding correctly on your router - Azureus is basically complaining that the ports are not being forwarded.  The idea is that you open specific ports on you router's firewall so that bit torrent clients can communicate between each other directly (so that other computers you are connected to are not blocked by firewall and are freely exchanging info with your computer) - this can make a big difference in download speeds.  It involves opening certain ports in your router's firewall configuration and then configuring the client to use those specific ports.

I can't give you any more detailed instructions on how to do it, the instructions are specific to particular router models.  You will need to have administrator access to your router.  Google is your friend ;)

---

### Post by jellystones on 2007-04-28
[http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)

Go here find your router model number. 
On the next screen click Bittorrent.

Follow the instructions and you should be good to go.

---

### Post by jellystones on 2007-04-28
> **jellystones said:**
> [http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)

Go here find your router model number. 
On the next screen click Bittorrent.

Follow the instructions and you should be good to go.

There is a BitTorrent link, but there should also be an Azureus link so click that instead.

---

### Post by sohaibma on 2007-04-29
thanks..
but are you sure Ubuntu's built-in firewall (iptables) has nothing to do with this slow down?

---

### Post by timczer on 2007-04-29
Are you  running firestarter?  Look in System-Administration and see if you have an icon for it.  If so, open it, and disable the firewall and try azureus again and see if the nat error goes away.  If so, you will need to set a new policy allowing the azureus port you are using to access the internet.  

In my past experience setting this up, it was forwarding the ports through my router that was the issue.

---

### Post by M$LOL on 2007-05-01
I'm having this problem, and I've tried disabling upnp, setting up a static IP, and it gives me "Nat Error" every time. I've noticed though, that when Azureus starts with upnp enabled, it gives me three successful mappings and one failed, all on the same port. I'm not running any firewall that I'm aware of, and I have ports forwarded on my router. What could be causing this problem?

---

### Post by Angelbeast on 2007-05-03
i'm getting the two errors show in the screenshots...any ides how to fix them? doing anything with the router though is outof the question...if it can'tbe remedied is there any other bit torrent client that works better with ubuntu?

---

