---
title: "Not another internet connection sharing problem"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by brotakul on 2006-07-29
hi.
i know this problem was discussed over and over again in the past but i simply can't make it work. and i'm linux begineer too..
ok. so i have two pc's, one running ubuntu and one running windows xp professional.
the ubuntu pc has a pppoe connection using ech0 with dhcp. i also installed a working network card ech1 [static ip:192.168.0.1] and i connected it to the windows machine's network card[192.168.0.2] using a crossover cable.
i installed samba on ubuntu using synaptic.
i pinged both the pc's and i don't have a connection..
now, i was reading other threads about sharing the internet connection, but i don't really know how to do this. is there any checkbox like "share this internet connection" witch i miss, or how can you do this under ubuntu?
witch samba configuration should i use to make it work? do i really have to configure it? it shouldn't work like this, with default settings?

do i have to install firestarter? if i use a firewall on my ubuntu[or not], do i need a firewall for my windows machine too? [because i disabled that firewall to not having problems with the connections].

i think this is it. thanks in advanced for the help and support.

---

### Post by Matchless on 2006-07-29
Hi,
   You need to first ensure that both PC's can see or communicate with one another. As you gateway PC is the one with ubuntu, and the other is windows you will need to install samba. Create a shared folder on both PC's. You may know that ubuntu will not be able to share files properly if your windows share is on an NTFS partition, it would be a good idea to creat a seperate fat32 partition for sharing. To allow internet sharing you need to install firestarter as well. I would suggest that you first get the 2 PCs working and talking to each other. Search on the forum for howto that will help you with installing Samba and configuring. The most important is setting up the lan cards properly in both PC's

---

