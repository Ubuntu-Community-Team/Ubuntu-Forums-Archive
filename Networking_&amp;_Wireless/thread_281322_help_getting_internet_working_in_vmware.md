---
title: "help getting internet working in vmware"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by solidtransient on 2006-10-20
I've got ubuntu 6.06.1 installed as a virtual appliance on vmware. The host OS is Windows XP Home sp2.  I'm trying to get the internet to work in ubuntu, but can't figure out the network settings.  VMware ethernet settings are set to NAT.  eth0 in ubuntu is set to dhcp.  

I'm a novice with Linux and come from a windows background.  Any help is greatly appreciated!

solid

---

### Post by happynix on 2006-10-21
VMware's website has some goo docs on NAT w/ vmware.

If that's the way you want to go then considerin asigning a statis IP to the vmware guests (ubuntu included)

If, per chance you simly chose NAT pseudo randomly as you vmware networking mode, then rerun vmware-config and choose bridging and your life will be much easier. Especially if you don't hvae a firm grasp on routing.

I'm not trying to be rude, I run almost all my vmware guests as bridged

---

### Post by foxmulder881 on 2006-10-21
Why are you running Ubuntu through VMWare in the first place? Why don't you just use the Live CD that Ubuntu doubles as?

---

### Post by darrenm on 2006-10-21
Yeah bridged just works.

It will then work just as if you plugged another computer onto your network. If you have a working DHCP server, it should work fine. If you are statically assigned then you will have to set this part up yourself just like your windows machine.

---

### Post by darrenm on 2006-10-21
> **foxmulder881 said:**
> Why are you running Ubuntu through VMWare in the first place? Why don't you just use the Live CD that Ubuntu doubles as?

I wouldn't because its pretty terrible to use for anything but trialling and installing.

---

### Post by solidtransient on 2006-10-21
I'm happy to use whatever mode works best.  If bridged makes more sense, I'll go that route.  I changed it to bridged and eth0 in ubuntu is still set to dhcp.  I do use dhcp on my home network, but so far I don't see my network in ubuntu as I did with NAT.  Still can't surf the web either.

---

