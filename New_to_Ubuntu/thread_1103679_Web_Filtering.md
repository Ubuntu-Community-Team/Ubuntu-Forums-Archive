---
title: "Web Filtering"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by bbourdet on 2009-03-22
Hello All -

I am new to linux world, but have been thoroughly impressed! The thing that has impressed me the most, is the people that are a part of this community. The knowledge that people have here, and the willingness to share it with everyone and anyone who will listen is encouraging.

On to my question:

I am currently running a Ubuntu Server 8.04, and I am using IP cop on a separate machine that is used for my URL filtering and routing and DHCP server and the like. I am currently an Admin for a small international school in Cambodia and one of our main issues is bandwidth here. We do not have a lot of bandwidth. We are paying $5-600 per month for unlimited 512k bandwidth, and we have around 70 users.

In light of this, we have to severely limit what is available for people to use, and what is not. And in doing so there are a few sites like face book or these video sites that just KILL our bandwidth to the point of people not even being able to browse web pages. I am using IP cops URL filter, but have not been that impressed. I have told it to custom block facebook, and it does, however, it does not block iphone.facebook.com or new.facebook.com. So that is the first problem, how do I fix that?

Secondly, I am currently using the command iftop to see some of our traffic on the network. However, I am not able to actually see what URL's people are going to. This is very important to me, I need to be able to see where people are going on this network. We used to use a proxy and had squidguard, which allowed me to use squidview which was perfect! But for a few reasons we have done away with the proxy, and now I do not have a way to do this! I have also looked into putting squid on IP cop, but I have not been able to do this. Any thoughts?

---

### Post by crjackson on 2009-03-22
Sounds like you might be interested in [www.openDNS.com]("http://www.opendns.com") - I use this for all my filtering needs and it just can't be beat in my opinion.

---

### Post by bbourdet on 2009-03-22
I would like to do the filtering in house if possible, so that I would be able to see where people are going on the web. I do not believe that OpenDNS offers anything like that. But I could be wrong...

---

### Post by llamabr on 2009-03-23
[http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)

---

### Post by Chemical Imbalance on 2009-03-23
I've never had a need for web filtering, but I've heard lots of good things about this:

[http://dansguardian.org/](http://dansguardian.org/)

---

### Post by crjackson on 2009-03-23
> **bbourdet said:**
> I would like to do the filtering in house if possible, so that I would be able to see where people are going on the web. I do not believe that OpenDNS offers anything like that. But I could be wrong...

Yes it does, I do it every day when I'm at work (or any place else) to see where the kids are going. That's another thing that makes it better than "in house" for me. I can check the stats and adjust the settings from anywhere.

---

### Post by hyper_ch on 2009-03-23
opendns will solve a lot of the issues you have - maybe you then also need additional working on iptables for things that are no good with OpenDNS.

---

### Post by billgoldberg on 2009-03-23
> **bbourdet said:**
> Hello All -

I am new to linux world, but have been thoroughly impressed! The thing that has impressed me the most, is the people that are a part of this community. The knowledge that people have here, and the willingness to share it with everyone and anyone who will listen is encouraging.

On to my question:

I am currently running a Ubuntu Server 8.04, and I am using IP cop on a separate machine that is used for my URL filtering and routing and DHCP server and the like. I am currently an Admin for a small international school in Cambodia and one of our main issues is bandwidth here. We do not have a lot of bandwidth. We are paying $5-600 per month for unlimited 512k bandwidth, and we have around 70 users.
I have told it to custom block facebook, and it does, however, it does not block iphone.facebook.com or new.facebook.com. So that is the first problem, how do I fix that?



Nexto to facebook.com and [www.facebook.com](www.facebook.com) also block

*.facebook.com

That should work, but I'm not sure.

But yes, OpenDNS would be easier and better.

I'm sure there are tools to keep things inhouse, but OpenDNS is just so easy.

---

