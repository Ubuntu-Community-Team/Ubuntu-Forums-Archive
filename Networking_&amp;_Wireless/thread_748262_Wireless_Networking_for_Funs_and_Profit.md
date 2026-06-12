---
title: "Wireless Networking for Funs and Profit"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by huzzak on 2008-04-07
So, I was reminded of this website on the first that talks about messing with wireless internet thieves.

[http://www.ex-parrot.com/~pete/upside-down-ternet.html](http://www.ex-parrot.com/~pete/upside-down-ternet.html)

I have a cheap Belkin wireless router, and a spare desktop with a wireless internet card.  I've been wanting to try and set up my wireless network so that I'll have more control over it, maybe be able to access it from school and ... to play the games described in the link above.  I've tried to do some research into the subject, but I think it is one of the situations where I don't know anything and so I don't know how nor where to start so as to not be knowing nothing.

I found these two links that describe using Ubuntu Server to setup a wireless network.  Are they something like what would be useful in order to do what I described?  What are other good resources to get going on not being so ignorant?

[http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283)

[http://ubuntulinuxhelp.com/how-to-setup-a-wireless-ubuntu-router/](http://ubuntulinuxhelp.com/how-to-setup-a-wireless-ubuntu-router/)

Thanks.

---

### Post by pseudo-random on 2008-04-07
I did one of these for a laugh about two years ago when I was in an apartment block with everyone leeching wifi.
I wouldn't recommend linking it to the internet though. Keep it air-gapped IMO.
Setup your router as open, DHCP etc then plug it into a server running apache and a neat program called dnsspoof. Every name they type in: ebay.com, google.co.uk etc will all get sent to your apache server with the url reading the right name eg ebay. What you put on your webserver is up to you. I just had a silly message something to the effect of 'pay for it like everyone else. Or come give me £5 and I'll let you on my real network.' It worked. I had a guy knock on my door with a fiver.
Of course you could do naughty stuff like packet sniffing for passwords etc which although illegal on public networks is perfectly legal on your own network. ;)

---

