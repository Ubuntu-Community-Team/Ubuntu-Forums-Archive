---
title: "no networking with new install"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by vitdoc on 2007-01-09
I am a long time Linux user.  I just set up a new computer with Ubuntu.
It dual boots with Windows XP.  I had no trouble with the installation but there is no active networking.  I use a router with a direct connection to the network card.  Ubuntu does not seem to recognize it.  I have no problems with the same computer using Windows with normal internet connections.
Any great ideas?  I am using my Windows partition to make this connection.

---

### Post by ppl on 2007-01-10
I got the exactly the same problem in here, except instead of install a new PC, I am switching my ISP and the ADSL modem/router as well. 
I get this information from dmesg I think could be the reason:
eth0: no IPV6 routers present.

---

### Post by ppl on 2007-01-10
Hello there,I solved my problem follow this thread: [http://www.ubuntuforums.org/showthread.php?t=333853&highlight=internet+connection]("http://www.ubuntuforums.org/showthread.php?t=333853&highlight=internet+connection")
hope it will work for you as well,good luck!

---

### Post by mips on 2007-01-10
> **vitdoc said:**
> 
Any great ideas?

Yes, maybe some more information ?

lspci -v
ifconfig
cat /etc/network/interfaces

Does windows use a static or dhcp ip configuration, or from windows in a dos prompt type ipconfig /all and post the output here.

---

### Post by dac10 on 2007-01-10
im having the same problem, i have a dlink router which windows recognises immediately, but ubuntu doest. im not familiar with the OS at all, so am rather limited in where menu's are etc. i found the network menu which displayed my ethernet cards but that was it.

ps. i too am using xp partion to post.

---

### Post by mips on 2007-01-10
> **dac10 said:**
> im having the same problem, i have a dlink router which windows recognises immediately, but ubuntu doest. im not familiar with the OS at all, so am rather limited in where menu's are etc. i found the network menu which displayed my ethernet cards but that was it.

ps. i too am using xp partion to post.

Hmm, maybe you should provide more info as mentioned above, we cannot read minds.

Do a search here for D-Link or Dlink as there is a known issue with some dlink routers. Hint, do an advanced search witk keyword: dlink and userid:mips

---

### Post by ppl on 2007-01-10
I am using a D-link rounter/modem as well(Xtra anyone?), the solution for my problem is in my previous reply. If you can ping your router and even ping [www.goole.com](www.goole.com) or some sites in internet in terminal, you probably got the same problem: The D-link rount/modem from Xtra need input ISP's DNS in your netwoing setting for your ethnet card, and in my case I assign a static IP for my PC to get it working.

---

