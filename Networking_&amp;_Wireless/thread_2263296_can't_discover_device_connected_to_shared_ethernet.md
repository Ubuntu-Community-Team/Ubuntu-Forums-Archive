---
title: "can't discover device connected to shared ethernet"
date: 2015-01-30
forum: Networking &amp; Wireless
---

### Post by beelzebufo on 2015-01-30
This is a bit complicated and I hope I can explain myself properly, but I am trying to connect a bitcoin miner which has a stand alone controller built in.  I need to use wifi because that's all I have.  I have no ethernet connection to use.  I have set my ipv4 settings to shared with other computers, powered it up and plugged it in, but when I enter the static address that the device has, it will not connect.  If I run nmap, it can't see it either.  I will try to explain it another way just so that I make sense.  My laptop is connected to the internet via wifi, I am trying to run a bitcoin miner which only has an ethernet connection, so I set my network connections (ipv4) to shared with other computers, but I can't seem to get my laptop to discover it.  I really hope someone can help me, I didn't think this would be a complicated thing, I have used a shared wifi/ethernet connection before and it worked just fine.  Oh yeah, I went to a friend's house nearby and plugged it into his router and it worked.  So I know the device works.  How can I get ubuntu to discover it so that I can use it?

Thanks in advance
Beelzebufo

ubuntugnome 14.04
dell inspiron laptop
bitmain antminer s3 bitcoin miner.

---

### Post by Bucky Ball on 2015-01-30
I think I understand what you're doing, but wondering if you have a router and the device is plugged in to the router and not the laptop. :-k

You say your laptop is online wirelessly. You have a wireless router? Should have ports in the back for ethernet. Plug the device into that if it is not already. Don't know anything about bitcoin or bitcoin miners, but figure it would be reachable via samba or ssh or ftp. You could try with Filezilla (in the repos). You'll need the static IP of the device, the username and password.

---

### Post by beelzebufo on 2015-01-30
I don't have access to the wireless router, otherwise I would be hashing away lol  I have the static ip, the username and the password, but I am trying to share my wireless connection (from a router that I do not have access to) with it through the ethernet cable.  My laptop just can't see it for some reason, I must have something messed up in the network sharing options, but it should be simple enough.

---

### Post by beelzebufo on 2015-01-30
when I open the network settings, it's connected using 10.42.0.1 and when I do an nmap of it, I get 3 open ports, but I can't get into it for some reason.  Any ideas?  basically, I need the ethernet address to be 192.168.1.x but it's 10.42.0.x

---

### Post by beelzebufo on 2015-01-31
bumping just because I can't seem to figure this out, I can't find any information anywhere.  I set the static ip on the device to 10.42.0.99 as the ethernet ip says it's 10.42.0.1, but no luck, every time I try to change something in the /etc/networking/interfaces file something goes wrong, it usually ends up saying that the device is unmanaged.  I don't understand, this shouldn't be this hard, I just want my ethernet to run through my wifi, there shouldn't be all these different ip addresses and everything.  I tried to bridge and that didn't work either.  ANY ideas would be greatly appreciated, I am at the end of my rope.  I know this can be done.

---

