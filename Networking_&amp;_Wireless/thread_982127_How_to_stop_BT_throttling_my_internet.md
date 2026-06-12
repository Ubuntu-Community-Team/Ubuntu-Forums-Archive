---
title: "How to stop BT throttling my internet?"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by SlickRick on 2008-11-14
I'm really getting sick of it. I'm paying £25 a month for a 8Mb/s connection and my maximum download speed is 60kb/s and at peak times it's slower than that. Should I complain or try to work around it?
When I go to the support website, it tries to tell me that there's equipment problems but on speed tests i get anything between 500kb/s and 4Mb/s.
I have a good mind to phone them up and call the wan**rs and demand to stop slowing my speed down.:)
However, I want to know if there's a more civilized way of doing this. I heard people can get around it by using SSH tunnels.

---

### Post by Kevbert on 2008-11-14
The problem in the UK is that the service providers such as BT, Sky, Tiscali etc advertise broadband with speeds of **up to 8Mb/s**. In practice this is very unlikely due to distance from exchange, number of users, the quality of the switch that broadband is routed through.  Personally I've had problems getting any more than 2Mb/s as I'm at the end of an exchange (yet I live just outside London).  The other thing you may want to take into account is that they quote Megabits and your speed may actually be quoted in Kilobytes, so your actually getting 60 x 8 = 480 kilobits. If it is 60 kilobits I would complain. Before you do this it would be worth browsing [http://news.bbc.co.uk](http://news.bbc.co.uk) (as the BBC website is always quite fast) and take a few measurements.

---

### Post by SlickRick on 2008-11-14
Regardless if it's kilobits or kilobytes, 60 isn't 8000. If it was like 1Mb I would be happy but atm I'm not able to watch youtube videos without having to wait a while which is annoying.
Whenever I try to get a speed test from the BT website, the servers are down and when I tried just now, it caused so much lag that my computer actually froze for a while. With Linux. Can you believe it?

So, is there anything I can do apart from waiting 10 months until the end of my CONtractc and getting a different ISP.

---

### Post by Kevbert on 2008-11-15
One thing you haven't taken into account and is probably one of the most important factors is that your connection is probably by copper cable which is subject to noise and losses. If you do change providers your best bet is to go over to cable (fibre optic) as this won't be much of a problem.
Do you get crackly noise, background hiss and loads of interference on your voice calls. Unplug the ADSL filter, plug the phone directly into the socket, and make a local voice call and see if this occurs. If it does then you have a very noisy line which you can report and at least get BT to test.
Another thing you could try is unplug the router overnight and plug it in the next morning and see if that helps.
Here's a [link]("http://www.moneysavingexpert.com/phones/cheap-broadband") that may be of interest. There's links from there that may help or go to the website's Broadband Forum. 
I know it's frustrating as I've been through a similar situation (even trying to get broadband) and it took two years to sort out. I started out with BT and now use Sky.

---

### Post by broadband57 on 2008-11-24
Personally I've had problems getting any more than 2Mb/s as I'm at the end of an exchange (yet I live just outside London).

---

### Post by Tom--d on 2008-11-24
If you suspect the are throttling your DL, change ports and enable encryption on bittorrent (It just helps).

Also, I get a "8Mbps" line.. The highest I've seen is 1100kb/s...

---

### Post by Swagman on 2008-11-24
> **SlickRick said:**
> Regardless if it's kilobits or kilobytes, 60 isn't 8000. If it was like 1Mb I would be happy but atm I'm not able to watch youtube videos without having to wait a while which is annoying.
Whenever I try to get a speed test from the BT website, the servers are down and when I tried just now, it caused so much lag that my computer actually froze for a while. With Linux. Can you believe it?

So, is there anything I can do apart from waiting 10 months until the end of my CONtractc and getting a different ISP.

I'm using the same ISP and sounds like the same package as you.

[IMG]http://i261.photobucket.com/albums/ii45/Outcast_Aussie/BT.jpg[/IMG]

So it DOES sound like you might be quite far away from the exchange or have a deteriorated line... Good luck trying to get that fixed though.

My brother was a BT engineer for 30 years before taking early retirement and starting up on his own.... He has had to demand engineers be sent out for line tests for customers  ( I believe you have to agree to pay if there is no fault) and then met the engineer in person and had a "chin wag" before issue is sorted... free of charge (a fiver donated into engineers beer fund)

---

### Post by SlickRick on 2008-11-26
[[IMG]http://www.speedtest.net/result/362786766.png[/IMG]](http://www.speedtest.net)

[[IMG]http://www.speedtest.net/result/362788089.png[/IMG]](http://www.speedtest.net)

[[IMG]http://www.speedtest.net/result/362789394.png[/IMG]](http://www.speedtest.net)

If I got speeds like that, I wouldn't be complaining too much.

---

### Post by SlickRick on 2009-04-14
Five months later and still 60kb/s at all times
I finally phoned up BT customer service and they told me my problems is that I live to far from the exchange.

That's quite a reasonable answer, but why is it that I get ~500kb/s on speed tests (even the bt speed tester) and my actual line is stuck on that exact number give or take a couple of kb.

The guy also insisted after hearing my speed results that I AM getting 500kb/s and failed to understand that the system monitor tells me what's my download speed and that it's nothing to do with cookies or cache as it's not a temporary problem. He said that there's nothing he can do on his end except to send a "Home IT Expert" which is a paid service.

Can it be my network setup or something?

Any ideas?

BUMP

---

### Post by talsemgeest on 2009-04-17
> **SlickRick said:**
> Five months later and still 60kb/s at all times
I finally phoned up BT customer service and they told me my problems is that I live to far from the exchange.

That's quite a reasonable answer, but why is it that I get ~500kb/s on speed tests (even the bt speed tester) and my actual line is stuck on that exact number give or take a couple of kb.

The guy also insisted after hearing my speed results that I AM getting 500kb/s and failed to understand that the system monitor tells me what's my download speed and that it's nothing to do with cookies or cache as it's not a temporary problem. He said that there's nothing he can do on his end except to send a "Home IT Expert" which is a paid service.

Can it be my network setup or something?

Any ideas?

BUMP
Well, I must say, it really does sound like bits vs bytes. 500kb/s = 62.5kB/s. I know it doesn't settle what you have with your isp, but it does explain why the speed test says something 8 times bigger than what you are getting.

---

### Post by tarps87 on 2009-04-17
I would suggest requesting that if BT can't actually provide you with the possibility of a 8Mb/s connection at some point, that they change you contract to one that matches the highest possible speed it can achieve taking into account the hardware. I don't think there is a legal obligation to do this but suggesting changing providers after you contract end if they don't do something may help.
When we first got broadband access in the village I live in we got 512kb/s broadband with about 500kb/s speed they broadband provider has now upgraded the connection for free (it is now about 4Mb/s) and the download speed is still 512kb/s :(

---

### Post by SlickRick on 2009-04-17
> **talsemgeest said:**
> Well, I must say, it really does sound like bits vs bytes. 500kb/s = 62.5kB/s. I know it doesn't settle what you have with your isp, but it does explain why the speed test says something 8 times bigger than what you are getting.

I tried running a speed test whilst downloading a game from the repos at 60kb/s and the test came-up with ~380kb/s during the download. I also tried running 3 simultaneous downloads and they were going at 40kb/s each

> **tarps87 said:**
> I would suggest requesting that if BT can't actually provide you with the possibility of a 8Mb/s connection at some point, that they change you contract to one that matches the highest possible speed it can achieve taking into account the hardware. I don't think there is a legal obligation to do this but suggesting changing providers after you contract end if they don't do something may help.
When we first got broadband access in the village I live in we got 512kb/s broadband with about 500kb/s speed they broadband provider has now upgraded the connection for free (it is now about 4Mb/s) and the download speed is still 512kb/s :(

They only do 3 packages for home users and the only notable difference between them is download allowance plus some useless extras like McAfee security. I got the third one which is unlimited. However, all of them offer up to 8Mb/s

I think I'll just sit it out until July 17 when I'm going on holiday for a couple of months ;) and during that time the contract should end. I can then switch to another provider, although you're never sure which one's are any good.

---

### Post by tarps87 on 2009-04-17
You're right, the last time I looked there were speed options as well. I'm currently using metronet (I think it's still called that), it is pay as you go but they cap the price a £25. While I was at uni we were using virgin media, if you can get a cable connection I would recommend it.

---

### Post by pewterbot9 on 2009-04-17
> **SlickRick said:**
> wan**rs

News flash: "wankers" is not a dirty word.

---

### Post by lisati on 2009-04-17
> **pewterbot9 said:**
> News flash: "wankers" is not a dirty word.

News flash: "wankers" is in a gray area: we all get the "not very nice person" meaning. Maybe it's the pedantic/autistic side to my make-up making a nuisance of itself, but the word can also refer to someone who ........ (family show!)

---

### Post by SlickRick on 2009-04-18
> **tarps87 said:**
> You're right, the last time I looked there were speed options as well. I'm currently using metronet (I think it's still called that), it is pay as you go but they cap the price a £25. While I was at uni we were using virgin media, if you can get a cable connection I would recommend it.

Unfortunately, I can't get cable in my area since it's a village.
I friend of mine who's with virgin recommends it a lot.
I may be moving into the same town as him during autumn, so cable should be available but if it's not, I'll probably go with virgin regardless.

> **pewterbot9 said:**
> News flash: "wankers" is not a dirty word.

> **lisati said:**
> News flash: "wankers" is in a gray area: we all get the "not very nice person" meaning. Maybe it's the pedantic/autistic side to my make-up making a nuisance of itself, but the word can also refer to someone who ........ (family show!)

Who cares. That is off-topic and your posts aren't really helping me.
I use wanker as an insult, so I naturally censored it because this is a public forum

---

### Post by doas777 on 2009-04-18
in short, there is no answer except perhaps to change ISPs. policital action may be useful, but considering the dismal response to Phorm, I can't imagine the current UK govt altering telco policy at the second. hopefully it will be better in the future.

---

### Post by tarps87 on 2009-04-20
> **SlickRick said:**
> Unfortunately, I can't get cable in my area since it's a village.
I friend of mine who's with virgin recommends it a lot.
I may be moving into the same town as him during autumn, so cable should be available but if it's not, I'll probably go with virgin regardless.


If you move close enough to him you could always 'borrow' his internet connection ;)

---

### Post by SlickRick on 2009-04-21
> **tarps87 said:**
> If you move close enough to him you could always 'borrow' his internet connection ;)

I meant I'm moving to the area around where he lives but I'm sure the neighbours would be more than obliged to lend me some interwebz. Just until I get around to getting my own contract...honest.:P

---

### Post by Mehashi on 2009-04-22
[COLOR=magenta]Konban wa[/COLOR]!
 
Hello if you are still reading this (Original Poster). 
 
I have been with bt for about 6 months now and have on speed tests between 6 and 7 meg connection (I live right in city centre near exchange!). 
 
If I download even 1 Gb between 4pm and 9pm I see my connection slowed to around 512k for rest of day and next day (even though this is not what they profess on their site) until around 9pm. 
 
If however, I only game or browse until 9pm, then do all my downloading at night I have seen speeds of 1400k on bittorrent and I never seem to be capped at all.
 
I do not know your circumstances, but I would recommend doing your downloading at night for a few nights and see if the speed picks up as you may stop being capped.
 
Also lastly, use peerguardian2 (or equivalent program)! This is essential as bt themselves say on their site that they can detect the type of file and protocol and if appropriate they will cap you for what they call 'non speed essential services' eg torrents, p2p, anything really apart from gaming or browsing. Since using peerguardian2 and leaving downloads till late my p2p and torrents have not been capped and I can play all day worry free with a ping of around 15 on steam and stream media very quickly.
 
It really depends on what, how and when you are downloading that will affect your speed. And before you say it - 'thats stupid'. I know! That is British services!
 
Good luck with this, I hope that maybe this helps you somehow!
[COLOR=magenta]^_^[/COLOR]
[COLOR=magenta]Ja mata[/COLOR]!

---

### Post by SlickRick on 2009-04-22
> **Mehashi said:**
> [COLOR=magenta]Konban wa[/COLOR]!
 
Hello if you are still reading this (Original Poster). 
 
I have been with bt for about 6 months now and have on speed tests between 6 and 7 meg connection (I live right in city centre near exchange!). 
 
If I download even 1 Gb between 4pm and 9pm I see my connection slowed to around 512k for rest of day and next day (even though this is not what they profess on their site) until around 9pm. 
 
If however, I only game or browse until 9pm, then do all my downloading at night I have seen speeds of 1400k on bittorrent and I never seem to be capped at all.
 
I do not know your circumstances, but I would recommend doing your downloading at night for a few nights and see if the speed picks up as you may stop being capped.
 
Also lastly, use peerguardian2 (or equivalent program)! This is essential as bt themselves say on their site that they can detect the type of file and protocol and if appropriate they will cap you for what they call 'non speed essential services' eg torrents, p2p, anything really apart from gaming or browsing. Since using peerguardian2 and leaving downloads till late my p2p and torrents have not been capped and I can play all day worry free with a ping of around 15 on steam and stream media very quickly.
 
It really depends on what, how and when you are downloading that will affect your speed. And before you say it - 'thats stupid'. I know! That is British services!
 
Good luck with this, I hope that maybe this helps you somehow!
[COLOR=magenta]^_^[/COLOR]
[COLOR=magenta]Ja mata[/COLOR]!

I'm quite sceptical about this working because when I first started with BT, I only downloaded at night and did browsing and stuff by day. When I started noticing that my speed is so low, I made sure I use the most out of my bandwidth. Say I watch a film, so I would turn on torrents.
Your suggestions do seem quite reasonable and I will give them a try.

And I'll be sure to give peerguardian a try after installing jaunty

---

### Post by Mehashi on 2009-04-22
I do not blame your scepticism. I am kind of person who reads TOS and other boring things and have noticed that a lot of what BT profess on their website is in fact not the case (usually worse) eg they say if you are capped because of usage it is only for rest of day, but if I get capped I am always capped the next day too. 
 
I do not know others with BT as my friends use Virgin (but they say my house does not exist!!!) so this is just what I have experienced. Unfortunately BT seems to suffer greatly from the distance to the exchange (moreso than virgin for example) so maybe they are actually telling the truth?? 
 
I don't trust them though (they monitor data transfers - evil!) and when my contract runs out I will try again for virgin (no monitoring!) optical.
 
Good luck either way! 
[COLOR=magenta]^_^[/COLOR]
 
(ps I have read about many faulty home hubs if you use one, apparently they are as glitchy as an original xbox, maybe try a different router, netgear or something)

---

