---
title: "slow internet"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by laloruelas on 2009-06-04
Hi, Until recently, my Internet has had a normal speed, but two days ago the Internet started to load very slowly, I'm not sure if it is Firefox 3.5's fault or if something changed in network network configuration. If you friendly people on the forums can help me it would be great. I'm on jaunty

---

### Post by Celauran on 2009-06-04
Unless the same internet connection is quick on another machine/OS, I don't think it's a Linux-related problem. The internet is slow sometimes.

---

### Post by SunnyRabbiera on 2009-06-04
Indeed, do you have like cable/DSL?
Sometimes you have to reset your modem/router, I personally need a reset at least one or two times a month.
This is in both windows and linux, there is no difference there.

---

### Post by laloruelas on 2009-06-04
i have dsl, i used pppoeconf in the terminal to set it up, i heard that if i use dhcp it willbe faster but the network manager says it doesn't manage eth0, in windows the internet significantly faster.

---

### Post by freeediver on 2009-07-23
For the past week or so my Comp has been very slow, so slow that I am forced to click Stop then re-select the link I want and try to reconnect. Whats up?
I am having trouble with my favorites now as well, when I select one it is taking forever to load if it loads at all. I am forced
to use the same procedure, click stop and try again, sometimes
I will try the reload option and it might or might not work.
Any ideas how to fix these issues?
I had the same problem trying to connect here as well.
Thanks

---

### Post by kdetech on 2009-07-23
Install opera 10 beta 2 has turbo boost that compresses data on its server before you receive. [http://my.opera.com/desktopteam/blog/2009/07/16/more-than-beta-2](http://my.opera.com/desktopteam/blog/2009/07/16/more-than-beta-2)
Only flaw is that image quality is reduced slightly

---

### Post by bowens44 on 2009-07-23
> **laloruelas said:**
> Hi, Until recently, my Internet has had a normal speed, but two days ago the Internet started to load very slowly, I'm not sure if it is Firefox 3.5's fault or if something changed in network network configuration. If you friendly people on the forums can help me it would be great. I'm on jaunty

For me firefox 3.5 is horribly slow. I run 3.0 and everything is fine. In 3.5 finding the page after clicking a link  takes about twice as long as 3.0. Although the difference is only a couple of seconds, it's very noticeable.

---

### Post by LewRockwell on 2009-07-23
I'm running Firefox 3.5 on XP, OSX, Ubuntu, and several *nix distros and the last couple of days I have also experienced slow responsiveness in several ways

Seems to me this is NOT an Ubuntu problem

Hopefully whatever Mozilla did...they will fix it in an update soon!

.

---

### Post by freeediver on 2009-07-23
This is really getting to be a big problem, my internet or at least my ability to connect to pages and links is getting to be so slow as to be unusable.
Just now to connect to this forum I had to reload 5-6 times, it must have taken me 5 min. for the first page/thread to open. The second thread I had no real problem with but getting the forum
to start working was a real chore.
I just noticed the little connection status bar in the lower rt of my screen.
It looks like cookies for ea. site are not fully/completely loading, my computer
thinks it is still trying to complete a connection.
Any ideas?

---

### Post by jack_harper2007 on 2009-07-25
I'm having the same problem... i think it started after i installed Firefox 3.5 but I'm not sure, anyway i removed Firefox 3.5 and I'm using my old Firefox 3.0 but the Internet connection is still slow I've tried to restart the modem but the problem continues.

Any ideas on how to fix this?

---

### Post by freeediver on 2009-07-25
Per instructions in a different thread I tried a fix, changing
a Firefox setting from false to TRUE but it did not help.

Type "about:config" in your url bar in Firefox. Search for "ipv6" It should say something like "network.dns.disableIPv6" set it to "true"

---

### Post by jack_harper2007 on 2009-07-28
Thanks Freeediver i did what you suggested but it didn't work :(
I think it's an Ubuntu problem and not a firefox problem because i've tried to use the browser Epiphany and it's also slow.

I don't know why this happened it's a problem that started without me doing anything i'm a bit annoyed because i'm not the only one using this computer and sometimes the internet connection is so slow that is nearly unusable (just needed to rant a bit about it ;) )

Thank's anyway and if someone has any ideas on how to solve this problem they are more that welcome :)

---

### Post by halitech on 2009-07-28
to see if its your computer or the internet, see if your ISP has an internal speedtest site adn check the speeds there, then test it at [http://speedtest.net](http://speedtest.net) and see if the numbers are close to the same. If the numbers are higher at the ISP site then speedtest.net then the issue is the net. If they are the same then probably a computer issue.

---

### Post by starcannon on 2009-07-28
Keep in mind that lately it has been in vogue to attack internet infrastructure.
[http://news.google.com/news?sourceid=navclient&rlz=1T4TSHB_enUS277US277&q=cyber%20attacks%20news&um=1&ie=UTF-8&sa=N&hl=en&tab=wn](http://news.google.com/news?sourceid=navclient&rlz=1T4TSHB_enUS277US277&q=cyber%20attacks%20news&um=1&ie=UTF-8&sa=N&hl=en&tab=wn)
 
Thats what I've been chalking the recently snail pace of my interwebs to.
/shrug, or it could be that my equipment and OS have all just mysteriously quit working correctly...

---

### Post by Papa-san on 2009-07-28
Try this for starters:
Do a traceroute to yahoo. Make sure all of your browsers are closed when you do it:
System>Administration>Network Tools
The fourth tab is traceroute. Put [www.yahoo.com](www.yahoo.com) in the address box and trace it. I'm interested in how many milliseconds it takes for each 'Hop' Number 1 is within your own system. #2 is within your router, and #3 is the first one to your ISP. You really don't need to run it for too many more hops, so stop it at 4 or 5. If you can post a screenshot it would be nice...

That will at least let us know where the bottleneck is...

---

### Post by jack_harper2007 on 2009-07-29
> **halitech said:**
> to see if its your computer or the internet, see if your ISP has an internal speedtest site adn check the speeds there, then test it at [http://speedtest.net](http://speedtest.net) and see if the numbers are close to the same. If the numbers are higher at the ISP site then speedtest.net then the issue is the net. If they are the same then probably a computer issue.

Hi Halitech unfortunately my ISP doesn't have an internal speed test. But i went to the site that you recommended and did a speed test there the results where: Download: 1.39 Mb/s Upload: 0.65 Mb/s wich is much slower than my connection use to be :(

---

### Post by jack_harper2007 on 2009-07-29
> **Papa-san said:**
> Try this for starters:
Do a traceroute to yahoo. Make sure all of your browsers are closed when you do it:
System>Administration>Network Tools
The fourth tab is traceroute. Put [www.yahoo.com](www.yahoo.com) in the address box and trace it. I'm interested in how many milliseconds it takes for each 'Hop' Number 1 is within your own system. #2 is within your router, and #3 is the first one to your ISP. You really don't need to run it for too many more hops, so stop it at 4 or 5. If you can post a screenshot it would be nice...

That will at least let us know where the bottleneck is...

I did what you suggested the results are in the screenshot (attachment)

---

### Post by halitech on 2009-07-29
> **jack_harper2007 said:**
> Hi Halitech unfortunately my ISP doesn't have an internal speed test. But i went to the site that you recommended and did a speed test there the results where: Download: 1.39 Mb/s Upload: 0.65 Mb/s wich is much slower than my connection use to be :(

what is the rated speed of your connection? I'm on a 15mb cable connection and here is mine

[[IMG]http://www.speedtest.net/result/527817638.png[/IMG]](http://www.speedtest.net)

---

### Post by freeediver on 2009-07-29
It looks Like the fault was with my provider.
After about a half hour on the phone the issue has been resolved.

---

