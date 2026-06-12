---
title: "set up the ubuntu server"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by rockymaxsource on 2007-06-22
Hey,

I installed the latest Ubuntu. The system is up and running. I installed Apache2, and openssh-server. The problem is I could not use my another  debian box with ssh-server installed ssh to it. 

2 of the cumputers are in same LAN. Both can get on to the internet to browse the webpages. My ubuntu box can ssh to my debian box. I can ping the ubuntu box with its IP. but from Debian box I could not ssh to Ubuntu box neither can I browse the webpages in ubuntu box's apache server directory. With the ubuntu box itself I can do the following> user1@machineName$ ssh user2@192.168.1.19  

Within the ubuntu box itself I can use firefox to browse the webpages in apache2 directory by using the below url> [http://192.168.1.19/](http://192.168.1.19/) 

Can any of you help me out please?

Thanks a lot in advance!

Blessings,
Rocky

---

### Post by tux821 on 2007-06-22
Hmm can you check if on your Ubuntu server a firewall is running ?
Just install on your Ubuntu box the package 'Firestarter' and select the 'Events' tab.

Keep that open and try, from your Debian box:

ssh  -v   user1@192.168.1.19

1) What output do you get from the ssh command ?
2) Are there any messages in the Firestarter events tab that you are blocked ?

Note: If you do not have X installed on your Ubuntu server (what is good ;), you can, as root, also check your firewall rules with:
# iptables -L

---

### Post by rockymaxsource on 2007-06-24
Hey,

Thanks very much for your reply!

I followed your instruction and the firestarters evernt list says the just tried ssh connection from Debian was rejected. Therefore I enabled it by right click on the event and select "Allow inbound service from everone" and it work good now.

Thanks again!

Blessings,
Rocky

---

### Post by tux821 on 2007-06-25
ok, great you made it work!

You can also configure specific ports with Firestarter, like only port 22/SSH ;)

---

