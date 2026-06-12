---
title: "Connection problems"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by jyzackoh on 2007-11-27
Hi everybody, im totally new to ubuntu.

just installed gutsy gibbon two days ago. 

I realised that my connection sort of has a problem.

1) When i am using Pidgin messenger, it suddenly disconnects me and im no longer connected to the internet. When i try to reconnect, it doesnt work. The connection comes back on only after some time.

2) When i am surfing the web, it occasionally stops loading. when i look at my pidgin messenger, it is also disconnected. Same as the above, the connection comes back only after some time.

Could anybody enlighten me about this topic? 

i have a router(aztec) and im having a pacific.net connection.

Sorry if i haven't provided you with any information about my hardware. Im sort of a computer illiterate. If you require some information about my hardware, please tell me what you need to know and how can i know my hardware. 

Thank you! (:
Zack

---

### Post by moyazes on 2007-11-27
Hi

How does your PC/laptop connect to your router ?

Is it wireless or wired ?

If it is wired try using a different cable or different port on your router if it has a hub. If your pc has a NIC (network card it may be faulty) or has a problem negotiating a link with your router. I would suggest possibly replacing this (they are cheap enough to buy)

If it is wireless then try an check to see if there are any wireless conflicts and other wireless networks around that seem to cause conflict. Maybe your PC is trying to roam onto another network that it can not associate with. I would also say best channels to use are 1,6, and 11 on 802.11b/g.

Hope this helps.

moyazes

---

### Post by jyzackoh on 2007-11-27
i'm trying one of your methods now moyazes. thx. i'll see how it goes. 

i'm using a laptop with a wired connection.

somthing to add, my brother also connects to my same router. We are both connected to the router via a  wired connection. He's using windows xp while i'm using ubuntu 7.10 gutsy gibbon. He is experiencing the same phenomenon.

Could the cause of this be that i have just changed my OS to ubuntu? If yes i would change back to windows (but i love ubuntu) =( because my comp feels kinda screwed now with other problems.

thanks.

---

### Post by moyazes on 2007-11-28
If your brother is experiencing the same problem with a XP laptop and you are both using a wired connection then I would not say it is a OS issue.

Have you checked your router/gatweay configuration ?

Have you been able to run any ping tests ?

$ ping <ipaddress of gateway>

If you see no loss then ping something on the internet like

$ ping [www.bbc.co.uk](www.bbc.co.uk)

and check to see if you see any loss/latency.

moyazes

---

### Post by jyzackoh on 2007-11-28
ehhh..

i'm still a noob and i dont know how to do the things you're telling me to =X

i've tried it out and when my computer is not connected to the router, it does not experience any disconnections.

Disconnection is my main problem. i can access the internet but i will get disconnected frequently.

Any help?

thx..

---

### Post by moyazes on 2007-11-28
What concerns me is that you said your brother's laptop had the same problem.

Now if this is the case then you must rule out the fact that it is your pc/laptop and could possibly be your internet connection. 

try to do this, On your ubuntu desktop go to

Applications -->Accessories and select Terminal

Then at the prompt of the terminal window type 

ping <address of your gateway>

you should see something along the lines of (but with a different ip address)
 
$ ping -c 20 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=62 time=12.5 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=62 time=36.5 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=62 time=30.1 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=62 time=53.9 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=62 time=78.1 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=62 time=13.4 ms

If you see that any of the icmp_seq are missing then you have a connectivity problem on your LAN. If they are all in order (1-20) then all will be okay but run this a few times and check.

Now if all that is okay try the same but with a host on the internet something like

$ping -c 20 news.bbc.co.uk

You should see something like

PING newswww.bbc.net.uk (212.58.226.33) 56(84) bytes of data.
64 bytes from nolmedia01.thdo.bbc.co.uk (212.58.226.33): icmp_seq=1 ttl=57 time=18.6 ms
64 bytes from newslb13.thdo.bbc.co.uk (212.58.226.33): icmp_seq=2 ttl=57 time=23.1 ms
64 bytes from nolmedia01.thdo.bbc.co.uk (212.58.226.33): icmp_seq=3 ttl=57 time=12.1 ms
64 bytes from newslb13.thdo.bbc.co.uk (212.58.226.33): icmp_seq=4 ttl=57 time=40.1 ms
64 bytes from nolmedia01.thdo.bbc.co.uk (212.58.226.33): icmp_seq=5 ttl=57 time=95.2 ms
64 bytes from newslb13.thdo.bbc.co.uk (212.58.226.33): icmp_seq=6 ttl=57 time=16.5 ms
64 bytes from nolmedia01.thdo.bbc.co.uk (212.58.226.33): icmp_seq=7 ttl=57 time=41.1 ms
64 bytes from newslb13.thdo.bbc.co.uk (212.58.226.33): icmp_seq=8 ttl=57 time=15.3 ms

Hope this helps

moyazes

---

### Post by jyzackoh on 2007-11-28
thx (:

ive sorta found out the cause of the problem. cos its onli when i'm using pidgin messenger that i experience such stuff. i changed to aMsn messenger and all is fine.

thanks for helping me!! i've learnt a new command xD

---

