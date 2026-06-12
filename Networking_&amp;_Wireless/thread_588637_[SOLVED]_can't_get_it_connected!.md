---
title: "[SOLVED] can't get it connected!"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by eel on 2007-10-23
I'm staying with a friend of mine for 3 weeks and i'm installing ubuntu on her old laptop, and so far it worked (gutsy on compaq m700) but i can't get it connected to the internet. 
I have no idea what her ip adress and i'm not exactly sure to find out. I tried "route" and "route -n" to 
discover the gateway but all i got was respectively "  *   " and " 000.000.00.00 " 
I can't copy/past any code because, well, i don't have internet on that laptop. 

I plugged in this computer (mac) to the same internetsource and i got an ip adress which i used but to no avail, maybe because i don't have a gateway adress. 

Using the beforementioned ip adress, plus the standard 255.255.00.00 subnet mask i did ifconfig,
which resulted in giving me another (?) ipadres in the inet adress line

Sorry if this all sounds completely unintelligible! 
Help!

thx.

---

### Post by eel on 2007-10-23
and.....

according to the site of the cable company ([www.home.nl](www.home.nl)) there is no static ip adress possible, so i put things back in roaming mode but that doesn't seem to do the trick either. 
damn.

---

### Post by pomalley on 2007-10-23
I'm having a similar problem. DHCP isn't giving me a gateway. I've tried adding one with ```
sudo route add default gw xxx.xxx.xxx.xxx
``` but that returns ```
SIOCADDRT: No such process
``` which I've googled much but to no avail. I've configured it for static ip, giving it the ip, gateway, and netmask I know it should have (gotten from Windows) but that dies with ```
SIOCDELRT: No such process
``` When I restart network from the command line (and it's using dhcp) with ```
sudo /etc/init.d/networking restart
``` it also gives a ```
SIOCADDRT: No such process
``` (I assume when it's trying to set the gateway.)

This is on a Dell laptop using a D-Link pcmcia network card (wired, the onboard ethernet port died), with a fresh Gutsy install, but I'm having the same problem with my desktop which has been upgraded from Feisty, which worked fine.

So, I'm stumped!

Also I didn't specify in there but DHCP is giving me an ip address and a netmask.

---

### Post by eel on 2007-10-23
hm. you've outweirded me :)

---

### Post by pomalley on 2007-10-23
Haha... I was just trying to be specific. Didn't mean to thread hijack, but I thought it might be the same problem. But I really don't know what's going on.

---

### Post by eel on 2007-10-24
oh dear.
it was the standby-switch on the modem. 
i have to crawl in a corner and feel stupid now for a while :)

---

