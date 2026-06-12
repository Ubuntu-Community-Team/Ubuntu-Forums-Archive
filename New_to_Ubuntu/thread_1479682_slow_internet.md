---
title: "slow internet"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by jackdm on 2010-05-10
new to this--give me some room--
just updated from 9.10 to 10.04--my internet is slow now
why?
jackdm

---

### Post by Ozymandias_117 on 2010-05-10
More likely your browser is slow. Try a different one and see if you have any changes. A lightweight, yet functional, browser I like is Chromium (The open-source project Google Chrome is based off of). To install it, just open a terminal and type: ```
sudo aptitude install chromium-browser
```

---

### Post by flyfishingphil on 2010-05-11
> **jackdm said:**
> new to this--give me some room--
just updated from 9.10 to 10.04--my internet is slow now
why?
jackdm
Mine seemd pretyy slow at first too. Using Firefox. It took a few trips alomng the "internet highway", on and off a few times and I noticed it seemd to be working a little faster. I have noticed, on some game sites, that I will see the Sun java loading, but that's about the only slow down I even notice now.

Maybe something to do with the "recall" in FF is my first thought. Something may have changed a little bit with the upgrade to 10.04. (I'm pretty new to this so I'm still doing a lot of "What happens if I....")

---

### Post by fuzZzball on 2010-05-11
Yea, setting these options did it for me though,

type in the url about:config, press the button 'I'll be carefull, I promise!'. 

Now set the following to **true** by just double clicking it (changes states from true to false, and the other way around).

network.dns.disableIPv6 = true
network.http.pipelining  = true
network.http.proxy.pipelining = true

and set network.http.pipelining.maxrequest to 8.

This should help, I installed 10.04 on 3 different machines, they all suffered the same problem, this solved it. For iceCAT, it's the same procedure.

Though Opera 10.5 Beta is off the chart, none of the similar settings help, shame though ;(

---

### Post by b1llyboy on 2010-05-11
It's probably not the browser. I had the same issue, and it has something to do with the way 10.04 uses IPv6. I think if your DNS doesn't handle IP6 then Lucid just sits and waits a while before using the older system. So what you end up with is a very long pause whenever you click on a link, and then a reasonably quick load once it finds the domain.

The above fix should work. I moved from my ISP DNS to Open DNS and that also did the trick.

Best of luck,

Billy.

---

### Post by fuzZzball on 2010-05-12
IPv6 is definitely the problem, disabling it did the trick already, but not for my netbook though. Second, when changing DNS, change to one not resolving IPv6's. That's prolly what did the trick for you.

---

### Post by Struggling1 on 2010-06-01
> **fuzZzball said:**
> IPv6 is definitely the problem, disabling it did the trick already, but not for my netbook though. Second, when changing DNS, change to one not resolving IPv6's. That's prolly what did the trick for you.

I also have a slow connection - not the ISP; I phoned them to check.  The screen keeps going grey, and I'm wasting a lot of time waiting for pages to load.  So what do you mean by changing the IP6 and DNS.  What do I actually have to do to fix this problem?  Please explain the process as you would to a child - I really do not understand computer speak - just a simple person here, trying to use the internet.  Would appreciate any advice.  Thanks.

---

### Post by XubuRoxMySox on 2010-06-01
Post Number Two in this thread explains it pretty well.

Open your Firefox browser, and in the field where you would normally type a web address (like [http://www.ubuntu.com](http://www.ubuntu.com)), type

**about: config**

It'll display a warning about messing around with the configuration. Answer by clicking on the button that says, "I'll be carefull, I promise!"

Now scroll down that list of settings until you find the one that says, 

"network.dns.disableIPv6 = false" and just double click on that line. It will darken and then read,

"**network.dns.disableIPv6 = true.**"

Do the same thing on the lines that say

"network.http.pipelining = false" and
"network.http.proxy.pipelining = false."

That will convert those settings to "true."

Then lastly, find the line that says

"network.http.pipelining.maxrequest" and set that number to 8.

That should hugely speed up Firefox for you. Let us know if it worked, and if it does, be sure to mark your original post SOLVED by clicking on Edit and changing the Subject line.

Hoping this helps,
Robin

---

### Post by texla on 2010-06-29
> **dixiedancer said:**
> Post Number Two in this thread explains it pretty well.

Open your Firefox browser, and in the field where you would normally type a web address (like [http://www.ubuntu.com](http://www.ubuntu.com)), type

**about: config**

It'll display a warning about messing around with the configuration. Answer by clicking on the button that says, "I'll be carefull, I promise!"

Now scroll down that list of settings until you find the one that says, 

"network.dns.disableIPv6 = false" and just double click on that line. It will darken and then read,

"**network.dns.disableIPv6 = true.**"

Do the same thing on the lines that say

"network.http.pipelining = false" and
"network.http.proxy.pipelining = false."

That will convert those settings to "true."

Then lastly, find the line that says

"network.http.pipelining.maxrequest" and set that number to 8.

That should hugely speed up Firefox for you. Let us know if it worked, and if it does, be sure to mark your original post SOLVED by clicking on Edit and changing the Subject line.

Hoping this helps,
Robin

Nice fix, Robin - thanks!  Only tiny typing change for someone who doesn't know this - you don't want a space between about:config - type it like this about:config and follow the rest exactly as above, it worked really well for me.  Also using opendns achieved the speed I wanted but I'm trying to see if my internet can go on it's own for a while... so far so good...

peace  :p

---

