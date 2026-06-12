---
title: "Port 80"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by Hovercat on 2010-01-01
Does Ubuntu 9.10 (Server Edition) block port 80? If so, how to unblock? I've used iptables and no one outside of my LAN can view my website. My ISP is NOT blocking port 80.

[img]http://i47.tinypic.com/23k3ma0.jpg[/img]

---

### Post by AndThenWhat on 2010-01-01
You need to setup port forwarding on your router, or alternatively you could put your Ubuntu server in your router's DMZ.

---

### Post by Hovercat on 2010-01-01
I forgot to mention, I did that to. I also did DMZ. Still no luck. =\

---

### Post by bpalone on 2010-01-01
Are you sure that Apache is configured properly?  I just used port forwarding on my set up.  I use 8.04 and it has been a while since I set it up, so my memory of issues is a bit foggy.  But, from what you have said you did with your router, I would examine my apache config files to make sure they are correct.

---

### Post by Hovercat on 2010-01-01
> **bpalone said:**
> Are you sure that Apache is configured properly?  I just used port forwarding on my set up.  I use 8.04 and it has been a while since I set it up, so my memory of issues is a bit foggy.  But, from what you have said you did with your router, I would examine my apache config files to make sure they are correct.

Yes. I'm 205% sure my Apache files are correct. I spent 7 hours on the with one of my friends to set up the config.

---

### Post by iMisspell on 2010-01-01
> **Hovercat said:**
> I forgot to mention, I did that to. I also did DMZ. Still no luck. =\
Not sure if you know or not, but DMZ will remove one layer of protection for your computer, no matter what you end up doing, you should try and resolve your problem with out using DMZ.

A couple questions...
Are you (or another computer on *your local* network) trying to access your computer via your external IP or are the poeple trying to access your server completly out-side you local network ?
- The reason i ask, ive had a router in the past which would not let me (while in my LAN) access my LAN via my ISP assigned IP (was testing some things and found this out), but ive had other routers that would let me to this.

What error message are the people getting ?

_

---

### Post by Hovercat on 2010-01-01
> **iMisspell said:**
> Not sure if you know or not, but DMZ will remove one layer of protection for your computer, no matter what you end up doing, you should try and resolve your problem with out using DMZ.

A couple questions...
Are you (or another computer on *your local* network) trying to access your computer via your external IP or are the poeple trying to access your server completly out-side you local network ?
- The reason i ask, ive had a router in the past which would not let me (while in my LAN) access my LAN via my ISP assigned IP (was testing some things and found this out), but ive had other routers that would let me to this.

What error message are the people getting ?

_


I'm not sure what error they're getting. Also, I have a domain and some subdomains. My domain is [www.asskickersunited.com](www.asskickersunited.com) The ip is 173.2.183.98

---

### Post by iMisspell on 2010-01-01
To help narrow down your problem, it might be eazyer to have them test with only your IP. With a domian address you add more steps and the possibilty of dns problems.

I just seen your other thread (which makes thing confusing have posts spread between different threads), maybe try the proxy again, but this time use your extrunal IP and not the domian name.


Sorry, i cant offer more.

_

---

### Post by Hovercat on 2010-01-01
> **iMisspell said:**
> To help narrow down your problem, it might be eazyer to have them test with only your IP. With a domian address you add more steps and the possibilty of dns problems.

I just seen your other thread (which makes thing confusing have posts spread between different threads), maybe try the proxy again, but this time use your extrunal IP and not the domian name.


Sorry, i cant offer more.

_

I posted this thread because my other thread became inactive and no posts. I just don't know what to do. I've tried the external IP. No one can ping it.

---

### Post by AndThenWhat on 2010-01-01
Did you install Apache through the repos?  Maybe check that UFW or some other security-based programs aren't blocking port 80. And for some applications, like gaming, you need to forward UDP as well as TCP on your router.  Another thing that you can try, but only as a suggestion is to restart your computer.  Sometimes when I set up Apache, it will do strange things until I restart.

---

### Post by bpalone on 2010-01-01
For S&Gs I just tried pinging the ip you gave above. No Joy all five packets failed.  I then tried pinging one above your ip it worked and then I tried one below your ip and it all failed.

Maybe you should double/triple check your router.  There may something there not allowing the traffic.  Or, maybe your ISP has a certain block of addresses that they are blocking port 80 on?????

Good luck.

---

### Post by halitech on 2010-01-01
I know you say your ISP isn't blocking port 80 but have you confirmed that?

test it here to make sure

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by louieb on 2010-01-01
I just tried to ping 173.2.183.98 
Looks like there is a problem with the IP address.

```
lou@t30box:~$ ping -c3 173.2.183.98
PING 173.2.183.98 (173.2.183.98) 56(84) bytes of data.

--- 173.2.183.98 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms

```and```
lou@t30box:~$ ping -c3 www.asskickersunited.com
PING www.asskickersunited.com (173.2.183.98) 56(84) bytes of data.

--- www.asskickersunited.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms


```

---

### Post by mkoehler on 2010-01-01
No luck on the ping from my location either.  Obviously it's a problem with your ip not being accessible from outside your local network.

---

### Post by mkoehler on 2010-01-01
Your first two steps should be to make sure that your server is setup on your local network with a static IP address, then make sure that port 80 is being forwarded to that address.  If your ISP isn't blocking port 80, then you should be able to see your server from outside your local network then.  Seems like a valid external IP address though (traces you back to Cablevision Systems in North Babylon, NY?)

---

### Post by Hovercat on 2010-01-04
Don't worry about this topic any more, I discovered the problem. It was my Optimum Online modem. It was not able to support the Boost feature. It works a-ok now. :D

---

