---
title: "Reset password and no google"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by twodayslate on 2007-12-14
Every time I restart my computer I have to retype my network password. Otherwise I can not go onto the internet. 

Using wireless internet on 7.10.

Also for some strange reason I can't view pages owned by google (no search or email).

Thanks for the help.

Also my internet has seemed really slow since this has happened.

---

### Post by mellowd on 2007-12-14
What kind of PC do you have? What kind of network card do you have?

Has it ever worked properly before?
You say internet has been slow since this happened, what exactly happened?

Are you able tp ping google.com? Can you trace to it?

---

### Post by twodayslate on 2007-12-14
> **mellowd said:**
> What kind of PC do you have? What kind of network card do you have?

Has it ever worked properly before?
You say internet has been slow since this happened, what exactly happened?

Are you able tp ping google.com? Can you trace to it?
My internet was working fine. 
I have a T6524 emachine computer with a belkin card (broadcom driver worked).

I am at 94% wireless connectivity so my speed should be good. 

How do I do this ping thing? 
It is starting to not just be google, just random sites now (google ads are on most sites?).

---

### Post by mellowd on 2007-12-14
> **twodayslate said:**
> My internet was working fine. 
I have a T6524 emachine computer with a belkin card (broadcom driver worked).

I am at 94% wireless connectivity so my speed should be good. 

How do I do this ping thing? 
It is starting to not just be google, just random sites now.

open a terminal and type this

```
ping google.com
```


then trace to it. this isn't installed by default so you'll need to install it first:

```
aptitude install traceroute
```

once installed type this

```
traceroute www.google.com
```


Paste your results here

---

### Post by mellowd on 2007-12-14
Also for a speedtest, cancel any other internet activity you have and go to [www.speedtest.net](www.speedtest.net). That gives a reasonably accurate test of your internet speed

---

### Post by twodayslate on 2007-12-14
> **mellowd said:**
> open a terminal and type this

```
ping google.com
```


then trace to it. this isn't installed by default so you'll need to install it first:

```
aptitude install traceroute
```

once installed type this

```
traceroute www.google.com
```


Paste your results here

```
administrator@54C:~$ ping google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
        

--- google.com ping statistics ---
71 packets transmitted, 0 received, 100% packet loss, time 70009ms
```
```

administrator@54C:~$ traceroute www.google.com
traceroute to www.google.com (64.233.167.147), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```

---

### Post by mellowd on 2007-12-14
my bad

```
sudo aptitude install traceroute
```


also could you ping a few others? like yahoo, msn or whatever?

---

### Post by twodayslate on 2007-12-14
> **mellowd said:**
> my bad

```
sudo aptitude install traceroute
```


also could you ping a few others? like yahoo, msn or whatever?

out of 40 requests:
yahoo 0, msn 0, digg.com 100%, wordpress.com 100%, twodayslate.com 100%, ubuntuforums.org 100%

That is using the network options tool, not the command line, that took to long.

---

### Post by mellowd on 2007-12-14
> **twodayslate said:**
> out of 40 requests:
yahoo 0, msn 0, digg.com 98, wordpress.com 98, twodayslate.com 98, ubuntuforums.org 100%

That is using the network options tool, not the command line, that took to long.



I need the command line so I can see where the packets get to

---

### Post by twodayslate on 2007-12-14
> **mellowd said:**
> I need the command line so I can see where the packets get to

still loading.

How long does this usually take?

---

### Post by mellowd on 2007-12-14
> **twodayslate said:**
> still loading.

How long does this usually take?

usually a max of 30 hops. takes a while if it doesn't get any response along the way. let it run through

---

### Post by twodayslate on 2007-12-14
```

administrator@54C:~$ ping google.com
PING google.com (64.233.167.99) 56(84) bytes of data.
--- google.com ping statistics ---
3073 packets transmitted, 0 received, 100% packet loss, time 3074007ms

```
```
traceroute to yahoo.com (66.94.234.13), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```
```
traceroute to msn.com (207.68.172.246), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```
Still waiting for pings

---

### Post by mellowd on 2007-12-14
That's odd. Looks like you getting nowhere, not even your gateway. Are you posting this from the machien in question?

---

### Post by twodayslate on 2007-12-14
> **mellowd said:**
> That's odd. Looks like you getting nowhere, not even your gateway. Are you posting this from the machien in question?

I am posting on two machines. My brothers (XP) and mine (7.10). The stats/pings/fetches are from mine.

---

### Post by mellowd on 2007-12-14
Are you able to get anything at all on the net on the ubuntu box?

Open a terminal and type this:

```
ifconfig
```

You should see your ip address on your network device. Are you getting an IP?

---

### Post by twodayslate on 2007-12-14
> **mellowd said:**
> Are you able to get anything at all on the net on the ubuntu box?

Open a terminal and type this:

```
ifconfig
```

You should see your ip address on your network device. Are you getting an IP?
worried about posting this. don't quote

I am on the eth1 network

---

### Post by mellowd on 2007-12-14
Hmm, this shows me that you are getting an IP address: 

eth1      Link encap:Ethernet  HWaddr 00:11:50:12:38:A2  
          inet addr:192.168.0.152  Bcast:192.168.0.255  Mask 255.255.255.0


I assume probably your gate (router) has an internal address of 192.168.0.1 or something similar. Can you ping the router? Can you bring your brothers machine?

---

### Post by twodayslate on 2007-12-14
> **mellowd said:**
> Hmm, this shows me that you are getting an IP address: 



I assume probably your gate (router) has an internal address of 192.168.0.1 or something similar. Can you ping the router? Can you bring your brothers machine?

How do I ping the router?
bring machine?

---

### Post by mellowd on 2007-12-14
No. run a trace from the xp machine to see what your first hop is. probably 192.168.0.1 but it could be different.

open up a command prompt on the xp machine and type

```
tracert www.google.com
```

you'll notice it's worded slightly differently on xp

Once you get the address for the first hop, try and ping that from your linux box

---

### Post by twodayslate on 2007-12-14


What? Did I do that right?
```
administrator@54C:~$ traceroute 192.168.0.1
traceroute to 192.168.0.1 (192.168.0.1), 30 hops max, 40 byte packets
 1  192.168.0.1 (192.168.0.1)  7.223 ms  7.287 ms  7.600 ms
administrator@54C:~$ traceroute  64.233.167.147
traceroute to 64.233.167.147 (64.233.167.147), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```

---

### Post by mellowd on 2007-12-14
You doing it right. This is what I am seeing. Your linux machine can get to your router. Your xp can get to both the router and the internet. 

First of all your linux machine took 7.600 ms to get to your router. That's increadibly slow. Almost 8 seconds to reach a local device? There is definately something wrong there.

What kind of setup do you have on your router?

---

### Post by twodayslate on 2007-12-14
I have the d-link DIR-655 router. I am using WPA Personal. I guess WPA Personal 2 is better so I might get my dad to switch later tonight. I do not have direct access to the router, my dad does. He is running Vista. 

Thanks for the help so far.

---

### Post by twodayslate on 2007-12-15
My dad fixed it today!

Thanks for the help. 
Is there a rep type of sytstem on this site?

I may still have the problem that when I turn off my computer my network address password is reset.

---

### Post by mellowd on 2007-12-15
You mean you need to keep entering your wireless password?

---

### Post by twodayslate on 2007-12-17
Yes. When I restart my computer I have to re-enter my network password.

---

### Post by mellowd on 2007-12-18
Are you using NetworkManager?

---

### Post by twodayslate on 2007-12-18
I am using the default Networking tool.

System -> Administration -> Network

I might have NetworkManager installed.

---

### Post by twodayslate on 2007-12-20
Anyone know how to get the password saved?

---

