---
title: "KTorrent doesn't download"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by gigenieks on 2011-07-23
Hi all. 


I am new in Linux world. A few years ago used a little Ubuntu (maximum 2 weeks), but now I have Kubuntu 11.04 installed today.

Before posting this tried to google my problem. [googlubuntu doesn't give anything useful...]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=KTorrent&as_qdr=all&sa=Google+Search&lang=en")
Also in these forums have only few topics named "KTorrent" 


My problem is that I can't download anything! 
If I download from _private trackers_ (where you have to register) I get:
Status: [COLOR="DarkOrange"]**Stalled**[/COLOR]

If I download f.e. from _thepiratebay.org_ I get:
Status: [COLOR="Black"]**Queued for downloading**[/COLOR]


How can I fix this? What is the issue?

---

### Post by TeoBigusGeekus on 2011-07-24
Do you have a firewall that's preventing ktorrent from functioning correctly?

---

### Post by gigenieks on 2011-07-27
I just installed Kubuntu. So, as far as I know - no.

I noticed, that KTorrent _does not_ download from **private trackers** (both are from my country), but it _does_ download from public trackers (for example thepiratebay.org).

Check also pictures in attachments! This is not good, because 98% of torrents I download from private trackers:
[LIST]
[*][http://www.inperil.net/]("http://www.inperil.net/")
[*][http://newoutlaw.org/index.php]("http://newoutlaw.org/index.php")
[/LIST]

If I could get to KTorrent work that would be just fantastic.

---

### Post by StephanG on 2011-07-27
I don't know about private trackers, but I can help with the queued for download thing.

Ktorrent has a default setting of only downloading three torrents at once.  If you click on Setting > Configure KTorrent > Queue Manager you can increase the number of maximum simultaneous.  Although, I have found if you try to set it too high, it can get slow.  

Personally, I have it set to 4, but I rarely download torrents.  You'll just have to figure out what works best for you.

Hope you figure out how to solve the private trackers problem.  All I can suggest is that it may help to enable DHT checkbox in 'BitTorrent' section of the configuration menu.

Best of luck,

---

### Post by gigenieks on 2011-07-27
> 
Ktorrent has a default setting of only downloading three torrents at once.

Changed to 6.
> 
All I can suggest is that it may help to enable **DHT checkbox** in 'BitTorrent' section of the configuration menu.

Enabled or not did not change anything.. :/
Thank you for trying help.

> 
Hope you figure out how to solve the private trackers problem. 

I just need some _suggestions_ what to do, what to try..
I don't really know how torrents work etc.. I just know how to use them. :biggrin:

Googled nothing useful came up...

Additional info: when I used Windows and [COLOR="DarkGreen"]**uTorrent**[/COLOR] everything was fine. (maybe helps someone)

Posted also [KTorrent forums]("http://ktorrent.org/forum/viewtopic.php?f=2&t=4195") only 2 views yet...


UPDATE --->

Found solution in [Kubuntu Forums]("http://kubuntuforums.net/forums/index.php?topic=3117755.0")

Just had to change port from 6801 to something different xxxxx.

---

