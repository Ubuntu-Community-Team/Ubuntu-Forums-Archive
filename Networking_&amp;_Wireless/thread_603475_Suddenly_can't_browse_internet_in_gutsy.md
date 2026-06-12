---
title: "Suddenly can't browse internet in gutsy"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by karlhm76 on 2007-11-05
This afternoon Gutsy decided to stop being able to browse the internet for no apparent reason after working flawlessly for about 2 weeks.

the router was unplugged from the phone line but wireless was still up and running. (My girlfriend had taken the phone out which also disconnected the router from the internet)

When I discovered I couldn't browse I checked the router and saw it was unplugged from the wall. I plugged the internet back in while everything was running and it seemed to work ok, except I was unable to browse from then on.

Its not the wireless, I can browse to the router config page.
Its not the connection, my XP laptop which I'm using to write this is working fine with the Gateway and DNS server both the IP of the router.

strangely enough I can ping by IP or name in a terminal window. If I type an IP address of a website into firefox it will work.

It seems like DNS, but only limited to internet, email and aMSN.. terminal still works.

is there any way to flush DNS, or check it to make sure its set up ok?

---

### Post by sharke on 2007-11-05
> **karlhm76 said:**
> This afternoon Gutsy decided to stop being able to browse the internet for no apparent reason after working flawlessly for about 2 weeks.

the router was unplugged from the phone line but wireless was still up and running. (My girlfriend had taken the phone out which also disconnected the router from the internet)

When I discovered I couldn't browse I checked the router and saw it was unplugged from the wall. I plugged the internet back in while everything was running and it seemed to work ok, except I was unable to browse from then on.

Its not the wireless, I can browse to the router config page.
Its not the connection, my XP laptop which I'm using to write this is working fine with the Gateway and DNS server both the IP of the router.

strangely enough I can ping by IP or name in a terminal window. If I type an IP address of a website into firefox it will work.

It seems like DNS, but only limited to internet, email and aMSN.. terminal still works.

is there any way to flush DNS, or check it to make sure its set up ok?
I agree sounds like a dns problem take a look at /etc/resolve.conf and see if nameserver are correct. if not edit to correct may work. it could also be your router is handling the dns which has to be changed in the router config page.
Regards
Sharke

---

### Post by sergm on 2007-11-05
You may try restarting your network using the following command:
sudo /etc/init.d/networking restart

AFAIK, linux is not caching DNS by default but I could be wrong, there is a special daemon for that:
nscd but I couldn't find it on my Ubuntu, so, probably it's not there by default and you may install it manually.

---

### Post by karlhm76 on 2007-11-05
> **sharke said:**
> I agree sounds like a dns problem take a look at /etc/resolve.conf and see if nameserver are correct. if not edit to correct may work. it could also be your router is handling the dns which has to be changed in the router config page.

Thanks for the reply

/etc/resolve.conf doesn't exist. Should I create it?

As for the router setup, well it seems to be working with no problems on XP and XP is set up with gateway and DNS set to the router's IP. DNS forwarding is set up on the router, and it has found DNS servers. I've never had any problems before now with this setup of the router.

In network manager information screen, I have this:
IP: 10.1.1.3
Broadcast address: 10.255.255.255
Subnet Mask: 255.0.0.0
Default Route: 10.1.1.1 <- address of the router
Primary DNS: 10.1.1.1 <-          "        "
Secondary DNS: 0.0.0.0

The problem also persists after a reboot, however I'll try manually restarting the network to see if it makes any difference.

---

### Post by sipickles on 2007-11-05
Using openDNS sovled my DNS worries:


[www.opendns.com](www.opendns.com)

or

208.67.222.222 and 208.67.220.220.

;)

---

### Post by karlhm76 on 2007-11-05
Thanks everyone for your help.

I have fixed the problem, I used a combination of DHCP and DNS to fix it up

I have disabled my router handling DNS, because while it does work (for XP) it just doesn't seem to work for Gutsy, maybe this is a bug? 

Anyway, I simply hardcoded servers found from openDNS into the DHCP config in my router. I restarted the network and lo and behold my DNS in networkmanager is now a "proper" value and not 10.1.1.1

XP still works, and I don't know why it worked before and not Gutsy, but that is a mystery left for another day.

So I guess this is sort of a workaround, but it seems to work ok.

Thanks again.

---

### Post by sharke on 2007-11-05
> **karlhm76 said:**
> Thanks everyone for your help.

I have fixed the problem, I used a combination of DHCP and DNS to fix it up

I have disabled my router handling DNS, because while it does work (for XP) it just doesn't seem to work for Gutsy, maybe this is a bug? 

Anyway, I simply hardcoded servers found from openDNS into the DHCP config in my router. I restarted the network and lo and behold my DNS in networkmanager is now a "proper" value and not 10.1.1.1

XP still works, and I don't know why it worked before and not Gutsy, but that is a mystery left for another day.

So I guess this is sort of a workaround, but it seems to work ok.

Thanks again.
No this is not a bug it is called freedom the ability to set the computer the way you like it to work not the harsware or windows.
Spickles 
Not an ideal situation to be using open dns servers as maybe a lot more traffic but if all works well and no issues go for it.
Regards
Sharke

---

### Post by sipickles on 2007-11-05
> **sharke said:**
> 
Spickles 
Not an ideal situation to be using open dns servers as maybe a lot more traffic but if all works well and no issues go for it.
Regards
Sharke


maybe, but see

[http://www.pcworld.com/article/id,127129/article.html](http://www.pcworld.com/article/id,127129/article.html)

---

