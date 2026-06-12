---
title: "Internet Connection"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by sven1976 on 2008-02-09
hello everybody......

Thirst of all all i have to admitt that i'm a total newbee in linux...

now my problem is : I have a old presario 724 laptop with a netgear WPN511 wireless card and i had xubuntu installed and everything was working fine.
yesterday i installed ubuntu 7.10 and when i tried to connect to the internet it didn't work. all i can do is connect to my router .the same thing is happening when i'm connected with the network cable.

what can i do??? the netgear card looks like is working as i can connect to my router parameters ....

Thanks in advance 

sven

---

### Post by squenson on 2008-02-09
Sven,

I would go to System > Administration > Network and check that your DNS server is set up to your router address. Let us know whether it solves your issue.

Stephane.

---

### Post by sven1976 on 2008-02-09
ok i'm gonna try this out and let you know in about 1 hour when i get home ......
thanks alot 
sven

---

### Post by sven1976 on 2008-02-09
i've checked the DNS settings and they look fine ...but still its not working...
I just get into the router but can,t open any site on the internet

Any suggestions PLEASE !!!!!!!

thanks 
sven

---

### Post by squenson on 2008-02-09
OK I am back on line just in time I think... So can you tell us what are the parameters you see in the network application:
1. Tab Connections, select the proper entry then click the button Properties
2. Tab DNS, then the entry(ies) for DNS Servers
3. IP address (192.168....) of your router
4. In Applictions > Accessories > Terminal, ping your router IP, then ping [www.oceane.fr](www.oceane.fr)

Sorry I am too detailed with my instructions, I do not know your proficiency with computers in general.

---

### Post by sven1976 on 2008-02-09
ok i think my problem is that i change the dns address but somehow i can't "make it stay there"..ping is working fine ...is there a total newbee guide how to install a wireless card on ubuntu so i can try to do it from the beginning????? its sure that i'm doing something wrong here.

thanks sven

---

### Post by squenson on 2008-02-09
Re-reading your initial post, it seems that your problem is not with the wireless card as you get the same issue with the cable connection. I would really look into the network configuration: if you can ping outside your LAN, then you are very close!

As I am also fairly new to Ubuntu and have a working network, I do not know any good guide for what you describe.

---

### Post by sven1976 on 2008-02-09
thanks for ypur help anyway....i know it has to be something really stupid as i can get a connection to my router
the internet is working fine as i,m sitting with my other laptop(windows) here and its fine

hope to find it soon otherwise will try to put xubuntu back on

thanks sven

---

