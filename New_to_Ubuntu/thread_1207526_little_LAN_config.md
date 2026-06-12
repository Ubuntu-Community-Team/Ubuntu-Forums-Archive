---
title: "little LAN config"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by marcopalla on 2009-07-08
Hi,

at home I have two ubuntu computer connected to an ADSL modem (Pirelli Voice), Internet connection works well for both, but
I'd like to share a folder each to copy files among them.

...so I've tried every kind of Samba (and mambo and cha-cha-cha too :p),
I've shared in every way folders, but in ubuntu the network link I don't see nothing
two days of   ](*,)

....I think the problem is in the card/modem config

can anyone help me?
thanx a lot

---

### Post by marcopalla on 2009-07-09
.... some information more


i try to set both eth0 (wired connection) 
with classic parameter IP subnet etc. etc. 
but everything I set instead of **roaming mode** the card doesn't work anymore (no Internet too)
 ](*,)
I tried also ifconfig configuration, but nothing seems to happen...

some help my friends?
bump,
m.

---

### Post by Septicmadman on 2009-07-09
The first thing I would check is to make sure that your two computers are on the same LAN (if they are on the same modem they likely are but who know they might get separate public ips?). This can be done a couple of way I'd suggest finding the ip addresses of one of the computers (ifconfig) and it will be listed as ienet addr and then ping the the address from the other computer. If it is a LAN the ipv4 addr will be most likely be 192.168.x.xxx. You'll probably get a response but it never hurts to check. I assume you're past this setp though.

Assuming thats all done you could create a samba share like it seems you've been trying to do, which would work after you have setup the samba serve correctly. 

That being said if you are only trying to share files between to *nix based systems you are better off using a different transfer protocol such as ssh. You could then access the files via an ssh tunnel you setup. I believe there are several clients that present a gui but off hand I am not aware of any.

Here is a guide describing the process. 

[http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)

---

### Post by superprash2003 on 2009-07-09
since both can access the internet from the same router , i guess they successfully have an ip address.. go to the terminal and type ifconfig and you should be able ot see the local LAN ip , it mostly should be 192.168.1.x or 192.168.0.x , then note down this ip and try to ping the two pcs.. if ping is successfull then you can proceed to file sharing , if not you must first troubleshoot the ip address issue.

---

