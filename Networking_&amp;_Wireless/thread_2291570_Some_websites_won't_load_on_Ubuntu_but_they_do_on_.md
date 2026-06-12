---
title: "Some websites won't load on Ubuntu but they do on microsoft windows!!!"
date: 2015-08-21
forum: Networking &amp; Wireless
---

### Post by Cosmas_M. on 2015-08-21
Hello guys,
Ive been using linux for a couple years now, I've managed to tackle most problems by searching for solutions on google. However, lately I've encountered a problem that I can't seem to find an answer anywhere online.

I have about 10 computers running on Ubuntu and the rest on windows, I have two internet connections from different ISPs, one is for backup. Both connections have been working flawlessly then all of a sudden a problem started which is affecting only connection from one ISP. The problem is, I can't access some websites on any computer running on linux especially yahoomail, hotmail, bbc and others but I  can access all these websites on a windows machine! I keep on getting the error "secure connection failed" on firefox and "No data received" on chrome. I've never come across this type of problem before...

Why would an internet connection work on microsoft windows machines only?, how come the other connection from a different ISP is working on both linux and windows machines? could it be something with the ISP in question?

Kindly anyone advice me on this matter

Regards

Cosmas.

---

### Post by wyliecoyoteuk on 2015-08-21
sounds like an SSL issue.
Maybe the ISP in question has dropped a particular encryption method, and the Linux machines are still trying to connect with it.
Try flushing the cache on one of the browsers, and check any certificates.
Also check that the time is correct on the Linux machines, minor setting, but it can have implications for secure connections.

---

### Post by Cosmas_M. on 2015-08-21
Thanks [COLOR=#000000]wyliecoyoteuk,

I did clear cache on the browsers (chromium & firefox), I also confirmed  time & date and all is correct.
I did a traceroute for yahoo.com on a linux machine and it times out after the 12th hop and just keeps on timing out to the end, when I do the same on a windows machine the traceroute completes successfully on the 13th hop. I've attached the two screenshots.

[/COLOR]

---

### Post by wyliecoyoteuk on 2015-08-21
Try changing your DNS, I use Google's 8.8.8.8 when testing.
I think it is most likely a change of encryption settings at your ISP though.
Some ISPs have dropped RSA keys.
Or it could be the other way around, the maybe the browsers are refusing to accept deprecated SSL keys.

---

### Post by The Cog on 2015-08-21
I think it's because the Ubuntu browsers have been updated and are being more thorough about checking SSL certificates. You may find the windows boxes also have problems when fully updated.

I notice that your traceroutes on Ubuntu and Windows are going to different addresses (46.228.47.115 vs 46.228.47.114). When trying to debug with traceroute, it's best to use the same target address for both. It's possible that .115 is down a the moment, which could explain why Ubuntu says there's no data received. I guess the cause of the different addresses is yahoo DNS servers using round-robin to spread the load.

It would be better to use .png insteat of .jpg for screen captures - .png doesn't go all blurry.

---

### Post by wyliecoyoteuk on 2015-08-21
[http://arstechnica.com/security/2015/04/new-firefox-version-says-might-as-well-to-encrypting-all-web-traffic/](http://arstechnica.com/security/2015/04/new-firefox-version-says-might-as-well-to-encrypting-all-web-traffic/)

---

### Post by Cosmas_M. on 2015-08-21
I've tried with different DNS servers, infact I use google's 8.8.8.8 on all my networks.
I've tried different browsers on different linux boxes.
I've tried traceroute for same IP address (46.228.47.114) on both windows and linux, windows completes the traceroute successfully, it times out after the 12th hop on linux boxes.

Like I mentioned in my first post, these same linux boxes are working flawlessly on a different ISP connection, traceroutes to affected sites are completing successfully and I can access the sites without any issue. its only on this particular ISP, it used to work before that means something has changed somewhere, I didnt change any settings on any of these linux boxes, they just stopped working all at once.

---

### Post by matt_symes on 2015-08-21
Hi

Is it possible for you to switch two of the computers, one connected to each ISP, just for a quick test to 100% eliminate anything on your side ?

I expect you will have the same problem but if you don't then that'll be very revealing.

Kind regards

---

### Post by matt_symes on 2015-08-21
Hi

Is it only on https connections you are getting the errors ? Your Firefox error message would suggest so.

If so then there is a tool that may help you diagnose the problem.

```
s_client
```

I have never used it but have read about it and it could help you out.

Kind regards

---

### Post by The Cog on 2015-08-21
I can't work it out. 
If you were using tracepath, I would have an idea - tracepath uses 1500 byte packets and sets DontFragment which might cause packet loss on some links, but traceroute only uses small packets.

Traceroute uses UDP by default, which may be being firewalled. Try using ```
traceroute -I www.yahoo.com
``` to tell it to use ICMP. But that doesn't explain the loss of the SSL HTTP connections.

Sorry, I'm running out of ideas.

---

### Post by Cosmas_M. on 2015-08-21
thanks matt_symes, I've tried your suggestions but I'm still experiencing the same problem.

> [COLOR=#000000][FONT=Ubuntu Mono]traceroute -I [www.yahoo.com](www.yahoo.com)[/FONT][/COLOR] when I use this command as The Cog suggested the traceroute completes successfully with 13 hops.

---

### Post by Cosmas_M. on 2015-08-22
I'm still trying to work my head around this problem, even the ISP doesnt seem to understand why their connection would not load some websites on linux systems. I've even tried with my neighbor's internet connection which is from the same ISP and it has exactly the same problem, he wouldn't have noticed anything because he doesnt use linux.

---

### Post by The Cog on 2015-08-22
Well, we can rule out the traceroute problem - that seems to be just firewalling of the Linux tracerout's default UDP packets.

As a last ditch, can you use 
```
sudo tcpdump -np -v
```
in a console window to trace what's happening on the network while you try the connection in the browser? 

Also, how do you switch between ISPs? Just in case there's something odd going on there.

---

### Post by Cosmas_M. on 2015-08-22
the switch from one ISP to another is manual, no automatic failover or load balancing, both connections are always in use on two different networks with two different routers but with same LAN IP subnet so when one ISP is down we disable the router then loop the two switches so both networks share one conneciton. I know its alot of work but we are getting a dual WAN router soon.

---

### Post by The Cog on 2015-08-24
I wasn't expecting thousands of packets. Or a screenshot image.

I can't make much out of that screenshot. I can see a brief connection to 192.168.0.1:80 that seems to finish normally, an ongoing connection to 192.168.0.1:443 is sending you data, and three ongoing connections to 62.8.89.6:80 (somewhere in Kenya) that don't pass any data.

I see that you linux box is always setting the DF DontFragment flag on outgoing packets. Although I don't think it is the problem, it may be worth reducing your MTU (max packet size) to see if your packets are being dropped on a small-packet link somewhere. Try this command to reduce the MTU to 1200 and then try the connection again:
```
sudo ifconfig eth0 mtu 1200
```
Change it back to 1500 after the test.

---

### Post by Cosmas_M. on 2015-08-24
yahoo on 1200 mtu                       yahoo on 1500 mtu

[ATTACH=CONFIG]264027[/ATTACH][ATTACH=CONFIG]264028[/ATTACH]

> [COLOR=#000000]I see that you linux box is always setting the DF DontFragment flag on outgoing packets. Although I don't think it is the problem, it may be worth reducing your MTU (max packet size) to see if your packets are being dropped on a small-packet link somewhere. Try this command to reduce the MTU to 1200 and then try the connection again:[/COLOR]
[COLOR=#000000]Code:
[/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]sudo ifconfig eth0 mtu 1200[/FONT][/COLOR]

Woah!...the websites are loading with mtu set to 1200. what does that mean? should I set it permanently to 1200 or will this affect other things?

Thanks so much The Cog

---

### Post by The Cog on 2015-08-24
Hey, that's good. You know what the problem is - your ISP is losing big packets. You should tell them.

Reducing your MTU is generally regarded as not a good idea. I think 1500 is *supposed* to be supported throughut the internet. It would be worth trying 1400, and messing 'till you find what the actual problem size is.

I don't have time to look up other possible fixes now (changing MTU, MSS, removing DF flag etc) at the moment, sorry.

---

### Post by Cosmas_M. on 2015-08-25
Thank you so much The Cog, you've been of great help. I will get intouch with my ISP about this but for now I'm just going to set the MTU to 1200 temporarily until they resolve the issue.
I'm so grateful. How do I mark this thread as "SOLVED" I'm sure someone else will be facing this problem sometime.

---

### Post by The Cog on 2015-08-25
In the Thread Tools pull-down menu at the top of the thread is an option to mark the thread solved.

---

