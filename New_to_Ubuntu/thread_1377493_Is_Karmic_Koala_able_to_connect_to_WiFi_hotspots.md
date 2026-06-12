---
title: "Is Karmic Koala able to connect to WiFi hotspots?"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Salvia on 2010-01-10
Hey I just came back to Ubuntu a couple of months ago, after going back to Vista before the old sound issue in Hardy was fixed. I was wondering if Karmic can connect to the internet in places that require your browser to be redirected to their login page. Places like Barnes & Noble, Books-a-Million, Hampton INN ,etc. This something I wasn't able to figure out in Hardy.

---

### Post by QLee on 2010-01-10
salvia,
To answer your question, yes.

But, so was Hardy, so my answer is of dubious use to you.

If you want help, please give details about your system and what errors you see. Wireless hardware is varied and some of it is more difficult to get working, some works easily.

Interesting nick, you're not smoking that stuff, are you?

---

### Post by Salvia on 2010-01-10
QLee, I have an Acer 6390 with integrated *802.11*a/b/g/ WLAN. I have absolutely no problems getting on wifi connections at home or hotspots that don't require a login. However when I connect wirelessly at Books-a-Million, which in Windows and Mac OS will make your browser redirect to an html page to login or agree to their terms of service, in Ubuntu firefox will only try to open my home page. Without logging in you can't go to any sites so, I get a page not found error screen. 


 And, yes I do smoke that stuff, but now for no good reason it's illegal in North Carolina. So I won't smoking any until I leave the state. :(

---

### Post by sandyd on 2010-01-10
> **Salvia said:**
> QLee, I have an Acer 6390 with integrated *802.11*a/b/g/ WLAN. I have absolutely no problems getting on wifi connections at home or hotspots that don't require a login. However when I connect wirelessly at Books-a-Million, which in Windows and Mac OS will make your browser redirect to an html page to login or agree to their terms of service, in Ubuntu firefox will only try to open my home page. Without logging in you can't go to any sites so, I get a page not found error screen. 
 
 
And, yes I do smoke that stuff, but now for no good reason it's illegal in North Carolina. So I won't smoking any until I leave the state. :(
 are you using wicd?
ive found that was the app that was causing it.
 
its generally a DNS problem. I had it a while ago when trying to access my library's wifi.
 
It simply could not resolve the address spyders.local (which is the system that my library uses)

---

### Post by bodhi.zazen on 2010-01-10
> **Salvia said:**
> Hey I just came back to Ubuntu a couple of months ago, after going back to Vista before the old sound issue in Hardy was fixed. I was wondering if Karmic can connect to the internet in places that require your browser to be redirected to their login page. Places like Barnes & Noble, Books-a-Million, Hampton INN ,etc. This something I wasn't able to figure out in Hardy.

Yes, I do this all the time on y netbook.

---

### Post by QLee on 2010-01-10
salvia,
You don't by any chance have your browser optioned to not allow page redirections do you? ..or any plugin that disallows it.

---

### Post by steveneddy on 2010-01-10
I travel for a living and have no problems with redirection while logging into a company's wifi service.

I use FF 3.5 - I can't get it to work with Chrome. But after FF logs on Chrome works fine.

---

