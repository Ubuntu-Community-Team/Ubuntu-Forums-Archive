---
title: "multiple routers"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by johnbravado on 2008-09-25
i have spent the last couple days trying to get my linksys wireless router to work with my ubuntu router and have just about given up for file sharing. 
ubuntu router does everything as an individual router i need file sharing internet access ssh works great no problems with the primary ubuntu router.
here is ghetto diaagram of my system
internet->modem->ubuntu router->4 port switch->wireless router and other wire comps.

out of the box no messing with the linksys router i can surf the web and any computer on the linksys router can ping outside to the internet and any computer connected to either the linksys router or the ubuntu router. however any computer on the ubuntu router cannot ping any computer on the linksys router. in fact i cannot even ping the linksys router. 

linksys router out of box information
ubuntu network is 192.168.2.0
linksys network is 192.168.1.0
both are setup for dhcp
so for internet connection on the linksys router is receives a dhcp address from the ubuntu router and that is why i can access internet. i place in the ip table of the ubuntu router 
destination:192.168.1.0 gateway:none use:eth1 which is inside lan card

things i have tried
changed the linksys router ip address to 192.168.2.3 and set its lease list to 100-124 and the ubuntu router lease list from 125-150 so there shouldnt be any conflict with the dhcp. when i did this i could no longer get internet connection on comps connected to the linksys like i was able to before.

tried static ip routing on the linksys which would involve setting up static ips for every comp on the system which is lame but i was trying anything to ping comps on the linksys router. 

i turned off firewalls on the linksys router 

tried other things on the ubuntu router to get packets to flow but cant think of them as it has beeen three days of random messing with it

tried various things that linksys support suggested but i wont even list them as they not oly failed but were dumb for what i want. 1 being change setup internet->modem->linksys->ubuntu->comps and turn off dhcp of the linksys router. however doing that anything connecting to the linksys router fails miserably so no wireless capabilities. linksys support blows they gave me other dumb suggestions too.

to recap my system is setup
internet->modem->ubuntu->4 port switch->linksys wireless and other comps
need internet and file sharing access with comps connected to the linksys. any suggestions would be most appreciated.

---

### Post by xebian on 2008-09-25
> **johnbravado said:**
> i have spent the last couple days trying to get my linksys wireless router to work with my ubuntu router and have just about given up for file sharing. 
ubuntu router does everything as an individual router i need file sharing internet access ssh works great no problems with the primary ubuntu router.
here is ghetto diaagram of my system
internet->modem->ubuntu router->4 port switch->wireless router and other wire comps.

out of the box no messing with the linksys router i can surf the web and any computer on the linksys router can ping outside to the internet and any computer connected to either the linksys router or the ubuntu router. however any computer on the ubuntu router cannot ping any computer on the linksys router. in fact i cannot even ping the linksys router. 

linksys router out of box information
ubuntu network is 192.168.2.0
linksys network is 192.168.1.0
both are setup for dhcp
so for internet connection on the linksys router is receives a dhcp address from the ubuntu router and that is why i can access internet. i place in the ip table of the ubuntu router 
destination:192.168.1.0 gateway:none use:eth1 which is inside lan card

things i have tried
changed the linksys router ip address to 192.168.2.3 and set its lease list to 100-124 and the ubuntu router lease list from 125-150 so there shouldnt be any conflict with the dhcp. when i did this i could no longer get internet connection on comps connected to the linksys like i was able to before.

tried static ip routing on the linksys which would involve setting up static ips for every comp on the system which is lame but i was trying anything to ping comps on the linksys router. 

i turned off firewalls on the linksys router 

tried other things on the ubuntu router to get packets to flow but cant think of them as it has beeen three days of random messing with it

tried various things that linksys support suggested but i wont even list them as they not oly failed but were dumb for what i want. 1 being change setup internet->modem->linksys->ubuntu->comps and turn off dhcp of the linksys router. however doing that anything connecting to the linksys router fails miserably so no wireless capabilities. linksys support blows they gave me other dumb suggestions too.

to recap my system is setup
internet->modem->ubuntu->4 port switch->linksys wireless and other comps
need internet and file sharing access with comps connected to the linksys. any suggestions would be most appreciated.

There can only be  1 dhcp server, so make your main router connected to the modem the dhcp server.  The linksys has to be disabled, otherwise there will be conflicts.  What make is your ubuntu router by the way?

---

### Post by johnbravado on 2008-09-25
7.04 i think made it 2 years ago and havent upgraded or did anything coz it works so wonderfully. when i disabled the dhcp capabilities of the wireless router then comps connected to the linksys router cannot not get an ipaddress from the ubuntu router.

---

### Post by superprash2003 on 2008-09-25
is the linksys router the wireless router?

---

### Post by johnbravado on 2008-09-25
yes, and at lunch i am gonna go home and try something after talking to the internet guy here at work let me know if this sounds good.

turn on NAT on linksys router.
set up static ip for mac address for linksys 192.168.2.3
under iptables
destination 192.168.1.0 mask:255.255.255.0 gateway:192.168.2.3 eth1
does that sound like it will solve a lot of my problems

it is either that or find a way to turn router off of the linksys and use as a bridge and let the ubuntu box handle everything i think option A provides for a better system though

---

### Post by johnbravado on 2008-09-25
how woul di set up a static ip on ubuntu for the mac address of the linksys router. i know i could prolly stumble on it somehow but if there is a simple task to it that you coul dput me in the direction of would be most appreciated.

---

### Post by xebian on 2008-09-25
> **johnbravado said:**
> how woul di set up a static ip on ubuntu for the mac address of the linksys router. i know i could prolly stumble on it somehow but if there is a simple task to it that you coul dput me in the direction of would be most appreciated.

I don't know how you set up Ubuntu to be  a router so I can't help you out.

I'm just curious though why your main router is to be Ubuntu.  You can have a setup where the main router is the linksys.  You can then connect 3 other boxes to the 3 ports wired, connect your 4-port switch to the 4th port which in turn can connect 4 more boxes.  At the same time, you can have as many more PC wirelessly connect with a total of 248?

---

### Post by johnbravado on 2008-09-25
i setup the ubuntu as a router so i could have a shared network server plus i got tired of store bought router problems 2 years with ubuntu as a router and not a single issue except for overflowing logs which filled up the hd and caused me to reinstall it. plus it was just fun. i cant setup linksys first becasue in doing so anything wirelessly connected would not be seen by the router which holds all my shared files or maybe i could make it but i dont want to do it that way i want to have ubuntu and all its control over what comes in and out of the internet to be first in line

---

### Post by y@w on 2008-09-25
> **johnbravado said:**
> how woul di set up a static ip on ubuntu for the mac address of the linksys router. i know i could prolly stumble on it somehow but if there is a simple task to it that you coul dput me in the direction of would be most appreciated.

I think what you're looking for is at the end of the dhcp.conf file posted on [this page]("http://www.askdavetaylor.com/how_do_i_install_dhcp_on_my_linux_server.html"). It looks like the structure might already be in the dhcp.conf file but commented out, though I don't have a system accessible for me to try at the moment.

---

### Post by xebian on 2008-09-25
This is what you need to do.

Connect your linksys to an standalone pc, and if you know your linksys ip address, logon to it.  You need to disable DHCP, in basic settings.  Then in advance routing, set it to be a gateway (not router).  Then, set it's ip address to a high number so it won't be clobbered by your router.  In this case, it should be 192.168.2.100 maybe. Save and logout.  Connect 1 of your linksys port (not the internet port) to your Ubuntu router.  That's it.

Try connecting a pc to one of the port of the linksys to check it out.  Let me know if it works.

---

### Post by johnbravado on 2008-09-25
well i am half way there i had a problem with the iptables i had one i shouldnt have. so now i every comp can ping every comp. woohoo. now i just have a problem with 2 networks. and i set linksys as router to make it work. havent tried the wirless part yet still trouble shooting and trying to perfect the wired portion. 2 networks meaning everything is part of HOME workgroup but everything on ubuntu is 192.168.2.X and everything on linksys is 192.168.1.X. any suggestions?

i use samba

---

### Post by John164918a on 2008-09-25
Now you have only one dhcp server, you probably have it set up to assign the ip addresses 192.168.2.x or 1.x depending on which one is the dhcp server. You need to fix the ip address of the non-dhcp server router to something where the first 3 numbers are the same for both routers, and the last one you choose for yourself, and (optionally but i dunno it might be a smart move) make that ip address fixed/static on the dhcp server. Make sure the last number in your routers ip address cant be allocated dynamically thru dhcp.

If your ubuntu router is a wireless one then if you make all the wireless settings the same, you can roam between routers.

I had to set up 2 routers at my house at uni and it took me ages especially since I was using ndiswrapper and had all sorts of problems with it! Eventually I had to find out about loads of stuff. Then it became easy. Wikipedia is rubbish on this sort of thing - its too technical. Forums are the best!

I hope that helps.

---

### Post by cariboo on 2008-09-25
You have to set a staic ip address and disable dhcp on your linksys router. You also can't use the wan port on this kind of setup, you'll have to connect to one of the regular ports with a crossover cable between your main router and the linksys router. Then use a crossover cable between your router and the switch.

Jim

---

