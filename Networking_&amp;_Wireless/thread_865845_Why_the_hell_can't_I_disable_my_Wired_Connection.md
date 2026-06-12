---
title: "Why the hell can't I disable my Wired Connection?"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by unc0nn3ct3d on 2008-07-21
Good god I am frustrated with this BS.  I have been having problems with my samba shared drives/directories ever since switching to a wireless connection and I believe I have narrowed the problem down to the fact that both my wired and my wireless connection are active.  So I attempt to do what most people suggest which is disable my wired connection and Ubuntu is having absolutely nothing to do with that plan.  My network manager has Dashes infront of all of the connections(see attachment) I am assuming that is because they are on roaming mode.  So first thing I try is to set the wired connection off roaming mode with a DHCP configuration, which gives me hope as now instead of a dash I see a checkmark in my network manager.. So I go to Uncheck it, it applies the changes which takes a good 30 seconds or so and now I have NO checkmark next to wired so I am even more hopeful as this would appear to have disabled my wired connection.. HOWEVER, I shut down the network manager and reopen it and VIOLA the Wired connection is checked and enabled again.
So I think maybe all of the net connections have to be off of roaming mode and I manually configure my wireless connection and then disable wired.. But nope it comes back again with vengeance as soon as I reopen the window.  

Now the funny thing is that when I disable my Wired connection my wireless connection dies with it, however if wireless is kept onto roaming it re-enabled my wired connection into roaming mode all on its own after a few seconds.

I've edited out the /etc/network/interfaces file, it is basically empty right now.  Everytime I take wired out of roaming and put it into DHCP it adds a nice entry in there which I have tried commenting out but it doesn't seem to do much of anything in preventing it from re-activating the wired connection.

Anyways, ANYTHING anyone has in mind about how to allow me to run my wireless connection without having the wired enabled would be great.

I'm running a Linksys W300N and the wired NIC is built in to the mobo.

thanks in advance

---

### Post by rrm3 on 2008-07-21
Have you tried running the following in a terminal (replacing eth0 with whatever your wired interface is, a list of all your interfaces will appear if you run ifconfig without any options):

$ sudo ifconfig eth0 down

I'm just as puzzled as you though as to why you should have to disable your wired connection.

---

### Post by unc0nn3ct3d on 2008-07-22
> **rrm3 said:**
> Have you tried running the following in a terminal (replacing eth0 with whatever your wired interface is, a list of all your interfaces will appear if you run ifconfig without any options):

$ sudo ifconfig eth0 down

I'm just as puzzled as you though as to why you should have to disable your wired connection.

Well firstly I{ have to take the wired connection off of roaming and then as soon as I do that command it disconnects my wireless connection entirely.  After a brief moment of having the Network manager open it automatically puts my wired connection back on roaming and the wireless connects again as if it just can't work without the wired NIC being operational.

The reason I am doing this is because I have been unable to access any of the LAN since I moved the comp and had to go wireless, even when I have one other Ubuntu computer on the lan and a Vista machine.  They can both see each other but my comp can't see them and vice versa.  I googled the heck out of the problem and found someone else had a similar problem where samba kept on defaulting to the wired connection(which was disconnected) and disabling that fixed it all.  It was the only solution I had found so I figured I'd try it but now can't because of this little glitch :(

It also should be noted that I can access the internet just fine, just nothing else on the LAN

---

### Post by sputnikkk on 2008-07-22
Seems this version of of the NetworkMISmanager in ubuntu 8.04 Hardy Heron is borked.  

Im ready many folks just get rid of it altogether.  I havenet been able to totally un-install it yet.

I solved my wireless networking idiosyncracies Network MisManager created by using a new tool - Wicd

[www.wicd.net](www.wicd.net)

[http://www.wicd.net/wiki/doku.php?id=faq](http://www.wicd.net/wiki/doku.php?id=faq)

---

### Post by Yannick Le Saint kyncani on 2008-07-22
> **unc0nn3ct3d said:**
> So I attempt to do what most people suggest which is disable my wired connection and Ubuntu is having absolutely nothing to do with that plan.

Why don't you unplug the cable o.O ?

---

