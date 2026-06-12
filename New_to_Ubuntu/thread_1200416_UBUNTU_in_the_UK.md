---
title: "UBUNTU in the UK"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Archie69 on 2009-06-30
Now this may sound like a stupid question but I'll ask anyway.  I've been running ubuntu 8.04 for about a year and its fantastic.  My question is this, is there anything I should know about ubuntu running in london england?

Is it all the same as here in Canada?  For example, at times when I try to connect to a wireless network here it wont let me.  It just tries to connect continuously but wont.  I know this a vague question but if anyone has any help/advice id appreciate it.  

Thanks

---

### Post by Elep.Repu on 2009-06-30
Some people block requests from linux distributions. 

Can you explain what you mean?

---

### Post by Archie69 on 2009-06-30
My main question really has to do with the capabilities of ubuntu to recognize a wireless signal in the UK (London specifically).  I Ask this because, as stated earlier perhaps un-clearly, when I try to connect to a wireless network here in Canada (unsecure of course) it wont let me.  I don't know why.  So my main concern is with me moving to London in the near future, will I encounter similar problems?

---

### Post by Paqman on 2009-06-30
> **Archie69 said:**
> My main question really has to do with the capabilities of ubuntu to recognize a wireless signal in the UK (London specifically).

Wifi is based on an international standard ([IEEE 802.11]("http://en.wikipedia.org/wiki/802.11")), it's the same everywhere.

---

### Post by redbook4574 on 2009-06-30
> **Paqman said:**
> Wifi is based on an international standard ([IEEE 802.11]("http://en.wikipedia.org/wiki/802.11")), it's the same everywhere.

Correct me if I'm wrong but don't different countries allocate different channels to wifi, so therefore although they all use the 2.4ghz band they do not all use channels 1-14, this may be the problem.

---

### Post by AnimalMagic on 2009-06-30
When I was last in Vancouver I was able to connect to wifi with UK spec portable, albeit running that other OS :-) Never played with wifi & ubuntu.

---

### Post by lisati on 2009-06-30
> **redbook4574 said:**
> Correct me if I'm wrong but don't different countries allocate different channels to wifi, so therefore although they all use the 2.4ghz band they do not all use channels 1-14, this may be the problem.
I concur that differences can sometimes occur: I've noticed that my Netgear router chooses channels differently according to where I tell it that I am.

---

### Post by Jedimaster007 on 2009-06-30
I'm running Ubuntu 9.04 on my laptop and I am amazed at how easy it was to connect to wireless.  Previously I had Vista installed (which I hated) and since running Ubuntu connecting to wireless is a breeze. 

Incidentally I'm using a Huawei 156G dongle/modem (on the 3 network) which Ubuntu found and set up with no difficulty.

And I've never lost connection or had any wireless issues at all.

---

### Post by Paqman on 2009-06-30
> **redbook4574 said:**
> Correct me if I'm wrong but don't different countries allocate different channels to wifi, so therefore although they all use the 2.4ghz band they do not all use channels 1-14, this may be the problem.

No, the channel that your wifi uses is pretty arbitrary. All 802.11 devices are the same (well, technically it's several specs but the upshot is that all 802.11b devices are compatible, for example)

---

### Post by Mornedhel on 2009-06-30
> **Paqman said:**
> No, the channel that your wifi uses is pretty arbitrary. All 802.11 devices are the same (well, technically it's several specs but the upshot is that all 802.11b devices are compatible, for example)

My regulatory domain is France. dmesg says :

```
[   77.497697] cfg80211: Calling CRDA for country: FR
[   77.500715] cfg80211: Current regulatory domain updated by AP to: FR
```

Regulatory domains (aka. "countries") do have an influence on how wireless is handled. Different countries allow different channels, for instance. redbook4754 is correct on this. However, there is no reason Ubuntu should have more trouble with a channel than another.

---

### Post by Paqman on 2009-06-30
> **Mornedhel said:**
> 
Regulatory domains (aka. "countries") do have an influence on how wireless is handled. Different countries allow different channels, for instance. redbook4754 is correct on this. However, there is no reason Ubuntu should have more trouble with a channel than another.

Yes, but all 802.11 devices can use any channel, so they're going to be compatible.

---

### Post by Mornedhel on 2009-06-30
> **Paqman said:**
> Yes, but all 802.11 devices can use any channel, so they're going to be compatible.

Yes they do, and yes they are. Which was the point of my last sentence, "there is no reason Ubuntu should have more trouble with a channel than another", which was a roundabout way of saying "it won't affect you anyway".

---

### Post by Paqman on 2009-06-30
> **Mornedhel said:**
> which was a roundabout way of saying "it won't affect you anyway".

Indeed, which answers the OP's question. I'm wondering if we can help him with his wifi performance in general though. Can you supply a bit more info about your system Archie69? What model is your router? What type of wifi card? What OS & network manager? Are you trying to connect through walls/over long distance, etc?

---

### Post by Archie69 on 2009-07-02
I have no problem connecting to wifi in my house, and for the most part anywhere else.  But on occasion I run into difficulty connecting in certain areas.  For example, my gf's house is a problem.  It is a secured network, and she is running the same set up as I have at my place, but I cannot connect there (she has obviously given me the password). Another similar instance happened at another friends house, while I had no trouble in my apartment in the same area using the same internet provider.  

That was largely in part why I asked if I'd have trouble in the UK.  My concern are the problems I'm having here, albeit not that big a deal cause it works at my house, but when I move to London I'd like to be able to ease right into using it.

Thanks for all the responses, and excuse the delayed reply, I've been away

Archie

---

