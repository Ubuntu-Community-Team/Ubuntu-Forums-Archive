---
title: "Help me install open source firmware on my router"
date: 2018-04-13
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2018-04-13
```
DIR 600 L 
H/W Ver B1 
F/W Ver.2.04 
 
```

Hi,

I own a DLINK DIR 600 L. 

I checked DD-WRT but they don't seem to support my router.

Please have a look and tell me if there is any opensource firmware 

available for my  router.

If I am posting in the wrong forum please move as needed.

Thanks.

---

### Post by linuxyogi on 2018-04-13
Bump

---

### Post by ajgreeny on 2018-04-13
I am not able to help with your query, but please do not bump a thread after only four hours; forum users are from all the world's timezones and it is possible someone from the opposite side of the world from you may have something to say, but it does take time.

---

### Post by linuxyogi on 2018-04-13
Hi,

I am using

```
DIR 600 L 
H/W Ver B1 
F/W Ver.2.04 
 
```

It is no longer supported and I cant install any open source firmware coz none support my device.

So the question is, is using an out of support router a security risk?

I am not asking about wireless security I am asking about WAN security.

Unfortunately I dont have the money right now to buy a new router.

I am really stuck.

---

### Post by QIII on 2018-04-13
Threads merged.

---

### Post by TheFu on 2018-04-13
> **linuxyogi said:**
>  
So the question is, is using an out of support router a security risk?

Yes.  In the last year, there have been 2 Linux kernel remote access bugs which apply to almost every Linux kernel out there.  That includes desktops, servers, IoT devices, networking equipment, Android, TVs, media players ... all of them.   I vaguely remember the last one from Oct 2017, so if the kernel being run on the router isn't newer than that, it almost certainly has the bug which allows remote access.

Plus, how many other bugs exist that aren't widely known? This is why layered security methods are very important.

---

### Post by linuxyogi on 2018-04-13
> **TheFu said:**
> Yes.  In the last year, there have been 2 Linux kernel remote access bugs which apply to almost every Linux kernel out there.  That includes desktops, servers, IoT devices, networking equipment, Android, TVs, media players ... all of them.   I vaguely remember the last one from Oct 2017, so if the kernel being run on the router isn't newer than that, it almost certainly has the bug which allows remote access.

Plus, how many other bugs exist that aren't widely known? This is why layered security methods are very important.

May be I am just wasting your time but the fact is I dont have the cash to buy a new router. I am really stuck.

Anything that you can think of that will improve the situation like an opensouce firmware?

Thanks a lot for your reply.

---

### Post by linuxyogi on 2018-04-13
Is there any test available to find if my router is secure ?

---

### Post by TheFu on 2018-04-14
It isn't possible to prove a negative.

Just saw this: [https://thewirecutter.com/reviews/best-wi-fi-router/](https://thewirecutter.com/reviews/best-wi-fi-router/)

I first met Jim (the author) at a Linux conference a few years ago where he was pushing the we should all use a limited, server, OS based on Linux or BSD for routers in order to be assured that software patches are continuous and available over long periods.

He convinced me this was the way for anyone running Linux to go.  

Getting firmware updates from aging routers after a few years is an issue. Creating your own router from from a PC or efficient, tiny, PC device is what I'd recommend.

[https://decentsecurity.com/routerwifi-configuration/](https://decentsecurity.com/routerwifi-configuration/) is the guide he recommends for securing routers.
[http://blog.jdpfu.com/pages/wifi-security](http://blog.jdpfu.com/pages/wifi-security) is my own router security checklist, but is it slightly dated. I just skimmed it. Seems relevant still.  Some ISPs in some countries block my blog, so use _thewaybackmachine_ or google cache if you have that issue. I have no idea why it is blocked.

---

### Post by linuxyogi on 2018-04-14
I read all the links you gave me. Very informative. I have already taken measures like disabling UPNP.

Remote management was already disabled by default. The only thing that I have no control over is 

the Firmware Update part. Dlink no longer supports this model. 

I will buy a DDWRT compatible router in a couple of months.

Thanks.

---

### Post by TheFu on 2018-04-15
dd-wrt doesn't maintain support forever.  I've had 3 routers lose support from dd-wrt over the years.

---

### Post by linuxyogi on 2018-04-15
> **TheFu said:**
> dd-wrt doesn't maintain support forever.  I've had 3 routers lose support from dd-wrt over the years.

Didn't know that. Thats bad news. Then I guess the best thing to do is install pfsense on a spare PC.

---

### Post by kurt18947 on 2018-04-15
If your device is a DLink DiR 600, OpenWRT supports it.
[https://openwrt.org/toh/start](https://openwrt.org/toh/start)

[TABLE="class: inline dataplugin_table"]
[TR]
[TD="class: leftalign rownumbers"]245[/TD]
[TD="class: leftalign brand"]D-Link[/TD]
[TD="class: leftalign model"]DIR-505[/TD]
[TD="class: leftalign version"]A1, A2[/TD]
[TD="class: centeralign supported_current_rel"][17.01.4]("https://openwrt.org/releases/17.01.4")[/TD]
[TD="class: align device_page"][dir-505]("https://openwrt.org/toh/d-link/dir-505")[/TD]
[TD="class: align device_techdata"][View/Edit data]("https://openwrt.org/toh/hwdata/d-link/d-link_dir-505")[/TD]
[/TR]
[TR]
[TD="class: leftalign rownumbers"]246[/TD]
[TD="class: leftalign brand"]D-Link[/TD]
[TD="class: leftalign model"]DIR-600[/TD]
[TD="class: leftalign version"]A1[/TD]
[TD="class: centeralign supported_current_rel"][17.01.1]("https://openwrt.org/releases/17.01.1")[/TD]
[TD="class: align device_page"][dir-600]("https://openwrt.org/toh/d-link/dir-600")[/TD]
[TD="class: align device_techdata"][View/Edit data]("https://openwrt.org/toh/hwdata/d-link/d-link_dir-600_a1")[/TD]
[/TR]
[TR]
[TD="class: leftalign rownumbers"]247[/TD]
[TD="class: leftalign brand"]D-Link[/TD]
[TD="class: leftalign model"]DIR-600[/TD]
[TD="class: leftalign version"]B1[/TD]
[TD="class: centeralign supported_current_rel"][17.01.4]("https://openwrt.org/releases/17.01.4")[/TD]
[TD="class: align device_page"][dir-300revb]("https://openwrt.org/toh/d-link/dir-300revb")[/TD]
[TD="class: align device_techdata"][View/Edit data]("https://openwrt.org/toh/hwdata/d-link/d-link_dir-600_b1")[/TD]
[/TR]
[TR]
[TD="class: leftalign rownumbers"]248[/TD]
[TD="class: leftalign brand"]D-Link[/TD]
[TD="class: leftalign model"]DIR-600[/TD]
[TD="class: leftalign version"]B2[/TD]
[TD="class: centeralign supported_current_rel"][17.01.4]("https://openwrt.org/releases/17.01.4")[/TD]
[TD="class: align device_page"][dir-300revb]("https://openwrt.org/toh/d-link/dir-300revb")[/TD]
[TD="class: align device_techdata"][View/Edit data]("https://openwrt.org/toh/hwdata/d-link/d-link_dir-600_b2")[/TD]
[/TR]
[TR]
[TD="class: leftalign rownumbers"]249[/TD]
[TD="class: leftalign brand"]D-Link[/TD]
[TD="class: leftalign model"]DIR-601[/TD]
[TD="class: leftalign version"]A1[/TD]
[TD="class: centeralign supported_current_rel"][17.01.1]("https://openwrt.org/releases/17.01.1")[/TD]
[TD="class: align device_page"][dir-600]("https://openwrt.org/toh/d-link/dir-600")[/TD]
[TD="class: align device_techdata"][View/Edit data]("https://openwrt.org/toh/hwdata/d-link/d-link_dir-601_a1")[/TD]
[/TR]
[TR]
[TD="class: leftalign rownumbers"]250[/TD]
[TD="class: leftalign brand"]D-Link[/TD]
[TD="class: leftalign model"]DIR-601[/TD]
[TD="class: leftalign version"]B1[/TD]
[TD="class: centeralign supported_current_rel"][snapshot]("https://openwrt.org/releases/snapshot")[/TD]
[TD="class: align device_page"][/TD]
[TD="class: align device_techdata"][URL="https://openwrt.org/toh/hwdata/d-link/d-link_dir-601_b1"]View/Edit data
[/URL]
[/TD]
[/TR]
[/TABLE]
I've messed with LEDE/OpenWRT a little. It doesn't seem as polished as DD-WRT but it supports many more devices.

---

### Post by linuxyogi on 2018-04-16
> **kurt18947 said:**
> If your device is a DLink DiR 600, OpenWRT supports it.
[https://openwrt.org/toh/start](https://openwrt.org/toh/start)

[TABLE="class: inline dataplugin_table"]
[TR]
[TD="class: leftalign rownumbers"]245[/TD]
[TD="class: leftalign brand"]D-Link[/TD]
[TD="class: leftalign model"]DIR-505[/TD]
[TD="class: leftalign version"]A1, A2[/TD]
[TD="class: centeralign supported_current_rel"][17.01.4]("https://openwrt.org/releases/17.01.4")[/TD]
[TD="class: align device_page"][dir-505]("https://openwrt.org/toh/d-link/dir-505")[/TD]
[TD="class: align device_techdata"][View/Edit data]("https://openwrt.org/toh/hwdata/d-link/d-link_dir-505")[/TD]
[/TR]
[TR]
[TD="class: leftalign rownumbers"]246[/TD]
[TD="class: leftalign brand"]D-Link[/TD]
[TD="class: leftalign model"]DIR-600[/TD]
[TD="class: leftalign version"]A1[/TD]
[TD="class: centeralign supported_current_rel"][17.01.1]("https://openwrt.org/releases/17.01.1")[/TD]
[TD="class: align device_page"][dir-600]("https://openwrt.org/toh/d-link/dir-600")[/TD]
[TD="class: align device_techdata"][View/Edit data]("https://openwrt.org/toh/hwdata/d-link/d-link_dir-600_a1")[/TD]
[/TR]
[TR]
[TD="class: leftalign rownumbers"]247[/TD]
[TD="class: leftalign brand"]D-Link[/TD]
[TD="class: leftalign model"]DIR-600[/TD]
[TD="class: leftalign version"]B1[/TD]
[TD="class: centeralign supported_current_rel"][17.01.4]("https://openwrt.org/releases/17.01.4")[/TD]
[TD="class: align device_page"][dir-300revb]("https://openwrt.org/toh/d-link/dir-300revb")[/TD]
[TD="class: align device_techdata"][View/Edit data]("https://openwrt.org/toh/hwdata/d-link/d-link_dir-600_b1")[/TD]
[/TR]
[TR]
[TD="class: leftalign rownumbers"]248[/TD]
[TD="class: leftalign brand"]D-Link[/TD]
[TD="class: leftalign model"]DIR-600[/TD]
[TD="class: leftalign version"]B2[/TD]
[TD="class: centeralign supported_current_rel"][17.01.4]("https://openwrt.org/releases/17.01.4")[/TD]
[TD="class: align device_page"][dir-300revb]("https://openwrt.org/toh/d-link/dir-300revb")[/TD]
[TD="class: align device_techdata"][View/Edit data]("https://openwrt.org/toh/hwdata/d-link/d-link_dir-600_b2")[/TD]
[/TR]
[TR]
[TD="class: leftalign rownumbers"]249[/TD]
[TD="class: leftalign brand"]D-Link[/TD]
[TD="class: leftalign model"]DIR-601[/TD]
[TD="class: leftalign version"]A1[/TD]
[TD="class: centeralign supported_current_rel"][17.01.1]("https://openwrt.org/releases/17.01.1")[/TD]
[TD="class: align device_page"][dir-600]("https://openwrt.org/toh/d-link/dir-600")[/TD]
[TD="class: align device_techdata"][View/Edit data]("https://openwrt.org/toh/hwdata/d-link/d-link_dir-601_a1")[/TD]
[/TR]
[TR]
[TD="class: leftalign rownumbers"]250[/TD]
[TD="class: leftalign brand"]D-Link[/TD]
[TD="class: leftalign model"]DIR-601[/TD]
[TD="class: leftalign version"]B1[/TD]
[TD="class: centeralign supported_current_rel"][snapshot]("https://openwrt.org/releases/snapshot")[/TD]
[TD="class: align device_page"][/TD]
[TD="class: align device_techdata"][URL="https://openwrt.org/toh/hwdata/d-link/d-link_dir-601_b1"]View/Edit data
[/URL][/TD]
[/TR]
[/TABLE]
I've messed with LEDE/OpenWRT a little. It doesn't seem as polished as DD-WRT but it supports many more devices.

My device is DIR 600 **[COLOR=#ff0000]L[/COLOR]**.

The **[COLOR=#ff0000]L[/COLOR]** is not supported by any of the open source firmware.

I went to openwrt's IRC and they confirmed it

---

### Post by kurt18947 on 2018-04-16
> **linuxyogi said:**
> My device is DIR 600 **[COLOR=#ff0000]L[/COLOR]**.

The **[COLOR=#ff0000]L[/COLOR]** is not supported by any of the open source firmware.

I went to openwrt's IRC and they confirmed it

Ah, sorry to hear that. Here in the U.S. Netgear WNDR-3700 series is pretty well supported by DD-WRT and they're plentiful and relatively inexpensive in the U.S. on Ebay. I don't know what the used router market is in your area.

---

### Post by TheFu on 2018-04-16
[https://arstechnica.com/tech-policy/2018/04/russian-hackers-mass-exploit-routers-in-homes-govs-and-infrastructure/](https://arstechnica.com/tech-policy/2018/04/russian-hackers-mass-exploit-routers-in-homes-govs-and-infrastructure/) - be careful which home router you buy.  I'd strongly suggest going with an x86-64 device that can run a lite-Linux or BSD OS and provide routing.  Then you'd have control over all patching and **know** it is current.   

If $100 is out of your budget for an x86-64 device (pfsense is 64-bit only now), Ubiquiti makes $35-$50 routers and so does Mikrotik for $55.  Those 2 vendors have a history of great support in their router software and patching issues very fast. They both were caught violating the GPL years ago, but don't anymore, though I'm not thrilled with their compliance methods, it does appear they meet it.

You can repurpose your current router to be a wifi-AP.  That would limit the risks to just those people within wifi range, so 300m or so rather than the entire world.

---

### Post by linuxyogi on 2018-04-16
> **kurt18947 said:**
> Ah, sorry to hear that. Here in the U.S. Netgear WNDR-3700 series is pretty well supported by DD-WRT and they're plentiful and relatively inexpensive in the U.S. on Ebay. I don't know what the used router market is in your area.

That market almost do not exists.

> **TheFu said:**
> [https://arstechnica.com/tech-policy/2018/04/russian-hackers-mass-exploit-routers-in-homes-govs-and-infrastructure/](https://arstechnica.com/tech-policy/2018/04/russian-hackers-mass-exploit-routers-in-homes-govs-and-infrastructure/)  - be careful which home router you buy.  I'd strongly suggest going  with an x86-64 device that can run a lite-Linux or BSD OS and provide  routing.  Then you'd have control over all patching and **know** it is  current.   

If $100 is out of your budget for an x86-64 device (pfsense is 64-bit  only now), Ubiquiti makes $35-$50 routers and so does Mikrotik for $55.   Those 2 vendors have a history of great support in their router  software and patching issues very fast. They both were caught violating  the GPL years ago, but don't anymore, though I'm not thrilled with their  compliance methods, it does appear they meet it.

You can repurpose your current router to be a wifi-AP.  That would limit  the risks to just those people within wifi range, so 300m or so rather  than the entire world.


Read [this]("https://www.mini-itx.com/2017/09/08/pfsense-to-require-aes-ni-from-25-how-it-affects-you") about pfsense[URL="http://pfSense to require AES-NI from 2.5: how it affects you"]
[/URL]


Kindly visit [https://www.amazon**[COLOR=#ff0000].in[/COLOR]**/]("https://www.amazon.in/")  and suggest me a router within Rs 2000. I will be buying it on June.

I want to buy a DDWRT compatible router.

My raspberry pi 2 is very slow. Its almost impossible to browse the web with Chromium otherwise I would have used my existing PC as a pfsense box and used the Pi as  my daily driver.

---

### Post by linuxyogi on 2018-04-17
I have installed Pfsense on my PC and presently using my Pi to surf the web. I will be buying another PC in June.

---

