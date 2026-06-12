---
title: "server 64bit and hardware"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by futsysmids on 2011-02-19
I have an old pc that I am using as a server and wish to install ubuntu server 64bit on it.

I have a broadband connection provided by sky and the broadband is going to plugged into the server.

Firstly - can I set up ubuntu as a firewall to stop unwanted hackers, as a web server for hosting my own websites, as an email server, print server and a place for file sharing all at the same time?

I have downloaded unbuntu 64bit server and have tested it out on vmware, and i know installing gnome on the server is not a good idea but I don't know enough about the "dos" based version to set it up.

Secondly (should have been first really) - hardware has two rj45 network cards in it and a wireless network card.

I assume that I loop back the broadband router through the server, disabling dhcp on the router and setup a proxy and dhcp on the server?

Any help would be of great help from such gurus as yourselves, especially if someone else on this forum has done something similar in the past.

One other thing - do I need a bigger hdd if I can do all of the above - the current one is a 160gb sata?

---

### Post by WannabeFantasma on 2011-02-19
I made myself a server to test all the stuff I can do with it, yeah you should be able to put all those things at the same time (I have samba share, ftp server, webserver)

I think you can make a firewall that blocks connections, but I also think (might just be me) that you can't access your webserver from any other port that you set. (I set mine at 1800 and I can only access my website through that port)
Note: I don't use my server as a firewall.

I only use 1 RJ45 connection, looked at my router (with dhcp) and checked the DHCP pool and made the server using a static IP (IP outside of that pool), that way the server allways has the IP I want.
You'll need to port forward the ports on the router used on the services you installed to the static ip.

Well you can first try it with gnome interface and try Terminal after that, I just did it with Terminal right away, and I had to say, I learned using it pretty fast.

Your HDD is big enough I think, depends on how much stuff you want to put on it. My hdd is only 40 GB... 

(Note I'm only a "noob" to servers)

---

