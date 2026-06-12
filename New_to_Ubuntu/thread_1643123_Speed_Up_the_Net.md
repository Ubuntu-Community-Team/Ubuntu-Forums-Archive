---
title: "Speed Up the Net"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by penguinplus on 2010-12-11
Is there a way to speed up the internet? And does Nosript add-on for firefox make it faster? And lst is there a way to speed up downloads? thanks.


[CENTER]-Penguinplus
[/CENTER]

---

### Post by amjjawad on 2010-12-11
> **penguinplus said:**
> Is there a way to speed up the internet? And does Nosript add-on for firefox make it faster? And lst is there a way to speed up downloads? thanks.


[CENTER]-Penguinplus
[/CENTER]


What exactly do you mean by "speed up the interent"?
The speed that has been given to you by your ISP is fixed and can't be changed, obviously.
Speeding up download? again, you can't download more than the downloading speed you have but ... I've noticed that with Ubuntu, the download rate is almost fixed, unlike Windows. With Windows, it's not stable and keep changing. With Ubuntu, it's almost fixed. I'm talking about the speed.

I have 256 bps which means MAX 30KB/Sec.
When I download normally, form Firefox for example, it's almost 30KB/Sec all the way.

With Windows, I need a Download Manager to make it happen and still not fixed speed all the way.

---

### Post by Rubi1200 on 2010-12-11
NoScript won't make your general Internet speed faster.

However, I have noticed that pages definitely load faster without all the junk that it filters out.

---

### Post by coffeecat on 2010-12-11
> **Rubi1200 said:**
> NoScript won't make your general Internet speed faster.

However, I have noticed that pages definitely load faster without all the junk that it filters out.

+1 to that. Plus the better security it affords.

@penguinplus, as far as speeding up the internet, I think you'd need to talk to the various backbone providers, telcoms and ISPs involved. :wink:

Speeding up downloads. Are you thinking of those utilities in Windows that rely on opening up several connections to the download server at once? I don't know of any for Linux, but many consider them to be very anti-social. If the download server is not under stress it will usually deliver close to your maximum possible speed anyway. If the server is under stress, or throttled, why should one person take precedence over others using the service?

---

### Post by zaphodbblx on 2010-12-11
well it may seem faster because flash movies and animations wont automatically load

---

### Post by I2k4 on 2010-12-11
Obviously there is a difference between "speeding up the internet" and speeding up FireFox, which seems to be what you want.  

I use NoScript for safety, not performance - it doesn't seem to slow anything down apart from the time it takes to give permissions when you actually want a script that it is blocking.  There is another add-on called FasterFox you can try - didn't do much for me.

I've had good success with several FireFox "about:config" tweaks to speed up the browser's operation - applying them there is not much difference between FireFox and Google's Chrome, though Chrome certainly is a faster browser overall.  I don't use Chrome as default only because of privacy concerns with Google.  

Here are my personally tested FireFox "about:config" tweaks, you can easily search to confirm they work and to learn how to play with FireFox "under the hood" - it's fun, but of course one never takes anybody's chat room word for anything without double checking other sources:

network.http.pipelining - false to true 
network.http.pipelining.maxrequests - 4 to 30 
network.http.pipelining.ssl false to true 
network.http.proxy.pipelining - false to true 
network.http.max-connections 30 to 96 
network.http.max-connections-per-server 15 to 32 
network.http.max-persistent-connections-per-server 6 to 8
browser.cache.disk.enable  = False (runs FireFox in RAM only - needs about 100MB)
[new boolean] config.trim_on_minimize true (lower memory when minimized)

---

### Post by A_M_S on 2010-12-11
You can use a caching web proxy like [Polipo]("http://www.pps.jussieu.fr/~jch/software/polipo/")

You can also try Chrome that is faster than Firefox in rendering web pages.

---

### Post by Geoff918 on 2010-12-11
You can't really "speed up the net" as there are bottlenecks beyond your control.

However, you may find that changing a DNS server may create better/faster responsiveness.

There are OpenDNS servers, and I personally use Comodo SecureDNS because my local Verizon DNS servers can't even resolve Google about 1/4 of the time. After that, I got fed up and changed my settings to great results. Plus, no ads when I mistype an Internet address. :)

---

### Post by JustinR on 2010-12-11
You can use the Opera Web Browser - it has a feature called 'Turbo Boost', on slower network speeds, it can double your current speed.

[Opera Web Browser]("www.opera.com")

[Opera Turbo Boost Technology]("http://www.opera.com/browser/turbo/")

And, +1 on ComodoDNS servers - it works great.

---

