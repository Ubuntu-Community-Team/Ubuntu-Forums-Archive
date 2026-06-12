---
title: "Broadband Speed and Performance testing"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by Chappy7777 on 2008-02-05
I am new to Broadband and also the company is also new to the area. It is flakey to say the best.

I was at my neighbour's house yesterday (he is a MS guy all the way, about 15 different certificates pinned over his desk, from all the courses he has taken over the years). Point: he is not into Linux at this time. Tho I keep working at him. 

We were discussing our mutual disgust and dismay over the new cable broadband that we both signed up for. I waited a couple months to see what he said. Then I got it.

He showed me a program he is using to measure his speed and traceroutes, pings, etc. He told me it would work w/Linux so I went there:

[http://www.broadbandspeedtest.net/](http://www.broadbandspeedtest.net/)

And it does not work w/Linux as far as I can see. I would appreciate it if someone can tell me of a similar program that will work w/Ubuntu. If you are running MS and are looking for this type of program, it seems great. 

I am presently getting download speeds of around 125K. That seems slow compared to what I expected, but blazing fast compared to what I had w/dialup. I can now download an MP3 in 30 secs instead of 20 minutes, so that seems like a giant leap for me. 

Thoughts, ideas?

---

### Post by Het Irv on 2008-02-05
I just tried [Speedtest.net]("http://www.speedtest.net") and it has been the most reliable for me in the past.  It is browser based, and therefore OS independent.

---

### Post by Chappy7777 on 2008-02-05
Yes, this works. The problem I am having is figuring out how I enter my location, or IP address.

I live in Canada, about 200 miles NE of Toronto (shown on the speedtest map). They default me to Bell Canada thru VIC Communications. VIC is the company that supplies my broadband. But not thru Bell Canada, and hop, skip and or so from Toronto. 

Does this thing read from my connection to my ISP. and then run the test from there? 

Obviouly, I don't understand how they are reading the info for the download and upload speeds.

One thing for sure, my speeds are really bad. Download speed of 450 kbps. Is that as slow as I think it is? Like 45K. 

More input please, and thnx,

---

### Post by Het Irv on 2008-02-06
It looks to see who owns the IP address that is assigned to you and determines a general location for you.  In your case Bell Canada might the IP address you are using.  450kbps is the same as 450k, for broadband you are doing on the lower end of very good.

---

### Post by Liet_Kynes on 2008-02-06
Speedtest prints results in kbps which is not the same as KB/s if i understand correctly.

Divide kbps by 8 to get KB/s.

450kbps is not a speed I would expect from a cable connection (don't know much about it though I'm in South africa and use ADSL). It seems slow cos I get a result of 3447kbps with speedtest. I thought cable was blindingly faster than that.

[[IMG]http://www.speedtest.net/result/231220849.png[/IMG]](http://www.speedtest.net)

And this is it in KB/s

[[IMG]http://www.speedtest.net/result/231223508.png[/IMG]](http://www.speedtest.net)

---

### Post by Chappy7777 on 2008-02-06
Any chance of some more opinions? of the 2 I got, 1 said "lower end of very good".

The second reply says I am getting lousy results. The fastest I've seen is about 950kbps. Person
 2's screen shot shows 3500kbps. So at my highest speed, I am getting 1/3rd person 2's result.

What can I do to up my speed? I read somewhere, before I had hispeed. something about going into Firefox and using about:ipconfig change Network something something from Ipv4 tp ipv6.
Is this something I should do?

Help needed. 

It seems like just as I get a slight grasp of Ubuntu, something new comes along and so I am really thankful for these forums.

---

### Post by Liet_Kynes on 2008-02-06
> **Chappy7777 said:**
> Any chance of some more opinions? of the 2 I got, 1 said "lower end of very good".

The second reply says I am getting lousy results. The fastest I've seen is about 950kbps. Person
 2's screen shot shows 3500kbps. So at my highest speed, I am getting 1/3rd person 2's result.

What can I do to up my speed? I read somewhere, before I had hispeed. something about going into Firefox and using about:ipconfig change Network something something from Ipv4 tp ipv6.
Is this something I should do?

Help needed. 

It seems like just as I get a slight grasp of Ubuntu, something new comes along and so I am really thankful for these forums.

I'm not sure about the whole IPv4 IPv6 thing but could you maybe post your results from speedtest.net. Maybe the whole kbps KB/s thing will be sorted out. 

If its 950KB/s that would be quite fast I think.

---

