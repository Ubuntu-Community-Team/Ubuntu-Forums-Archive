---
title: "What the heck is this?"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by Vlad1 on 2010-02-21
Hello,
I tried everything, but I keep getting a message when I log into IRC chat that says the following:

AUTO [1] Infected with a virus or trojan, please clean your system. Cleaner @ [http://www.moosoft.com](http://www.moosoft.com) (P339).
* Closing Link: vlad1 by mesa.az.us.undernet.org (G-lined)
* Disconnected (Remote host closed socket).

....then kicks me out.

I installed many times (also tried Linux Mint), got same message thru live CD.  I installed add-on in Firefox and still same message.
I just bought a brand new computer, dowloaded Ubuntu ISO image, made live cd (all on the new computer) and installed Ubuntu on my old lap top.  I did not do a dual bootsystem, but installed on entire drive.  I was not aware of any virus issues on my old laptop as everything was current.  Currently Ubuntu 9.10 (most recent, just downloaded today- did not add any new programs to it, fresh out of the download you might say.)

Now, I thought that an install would remove any virus (assuming I had one), and also Linux was not prone to any viruses.  I tried the Clam thing, but nothing showed up (assuming i did it right)

Any ideas?

Thanks in advance!

---

### Post by Dougie187 on 2010-02-21
What are you using for irc? and what server are you connecting to?

Also, just so you know, you obviously don't have a virus, because the software you are referred to is regarding windows. So my guess is it's a server side thing.

---

### Post by 2hot6ft2 on 2010-02-21
Guess they have spread out from popup windows to IRC. Don't click on the link or you will most likely get a virus. Report it to the IRC servers head honchos (if there is such a thing, I've never used it). Theirs is what's infected if any.

---

### Post by Vlad1 on 2010-02-21
i am using xchat....trying to connect to Undernet

It's weird becuase if I boot the live cd, and try to connect, I get same message.

Did not have an issue before with the another lap top.

Thanks!

---

### Post by nos09 on 2010-02-21
is there any way to list channels ?
that are avilable on Quassel IRC .

---

### Post by Linux_junkie on 2010-02-21
I've just had a look at the web site the link points to and its for spyware.  My guess is that its not a virus you have but its just a viral advert advertising this spyware detector.

I'm surprised it closed down your IRC app though did you close it down yourself by clicking quit or something?

---

### Post by x33a on 2010-02-21
Take a look here:

[http://www.undernet.org/forum/viewtopic.php?f=9&t=11466](http://www.undernet.org/forum/viewtopic.php?f=9&t=11466)

A lot of people have complained of the same problem, though none were using linux.

quoting a user xplora from that forum:
> As for the "Your PC is infected" messages, it is possible another  infected PC has been connecting to undernet via the same IP address you  are connecting with, this can be because there is a problem with your  router, or there are multiple computers behind the same router  (including yours), your ISP could be doing some kind of IP address  sharing between multiple customers (basically multiple computers behind  same router including yours trick).

---

### Post by Vlad1 on 2010-02-21
i am using xchat because it seems much easier....still kind of new to this and not familiar w/ Quassel IRC .  I would think same result. but I'll give it a try.  I think you have to set  up Quassel w/ ports, etc, which I am not familiar with but I'll see what I can dig up.

---

### Post by Elfy on 2010-02-21
I had a similar issue recently when freenode was the subject of a bunch of spam - I stupidly :oops: clicked on one of the sly ones.

I was kicked and banned at the IP level - I reported it so that they could unban me, in the meantime rebooting my router got me a new IP address and I was able to get back on before they unbanned me.

---

### Post by 2hot6ft2 on 2010-02-21
> **Vlad1 said:**
> i am using xchat....trying to connect to Undernet

It's weird becuase if I boot the live cd, and try to connect, I get same message.

Did not have an issue before with the another lap top.

Thanks!
Looks like one of those things that tells you you're infected and to click their link at which point they will infect you and then you're in for it. Then they will offer a program to "fix it" for a nominal fee naturally. That ploy has been on windows for years.

You're not the one that's infected it's probably a bot on the server the IRC is using.

If you went there now on the other laptop you would most likely get the same message or one very similar.

---

### Post by 2hot6ft2 on 2010-02-21
> **x33a said:**
> Take a look here:

[http://www.undernet.org/forum/viewtopic.php?f=9&t=11466](http://www.undernet.org/forum/viewtopic.php?f=9&t=11466)

A lot of people have complained of the same problem, though none were using linux.

quoting a user xplora from that forum:
The mention of the router brings to mind a router exploit that I read about a while back affecting cisco based routers
Here's a quick search for more info
[Router Exploits]("http://www.google.com/search?q=router+exploits&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

EDIT: If that were the case then a hard reset 30/30/30 followed by a firmware update would be the best solution.

The 30/30/30 hard reset means with the router plugged in push and hold the reset button for 30 seconds.
While still holding the reset button in, unplug the routers power and continue holding the reset button for 30 seconds.
Still holding the button in plug the power back in and continue holding the reset button for 30 seconds.

So you have to hold the button in for at least 90 seconds while power is on/off/on

Release the button and let the router warm up for a minute.

That clears the routers configuration completely and it's like brand new and you have to set it up all over again to your configuration.

---

### Post by Vlad1 on 2010-02-21
true....but I can't get in at all; i bounce off different servers, but all say I have same issue.
My other older lap top is out of action, that's why we decided to buy another one. I like ubuntu quite a bit so i wanted to install in on the hand-me-down.  that's when all this came up.  Normally I would say, i was infected on the other laptop and something transfered w/ the image, etc, but i downloaded and burned the live cd on the brand new lap top.  just a few hrs old.  should have any viruses on it; and also that Linux does not have virus issues.  So needless to say, I am very surprised.  I tried several times to re-install, and also Linux Mint.
Probably try Fedora next, and see what happens. Mint is based on Ubuntu somewhat anyway, so if Ubuntu has issues, Mint could have the same.
Thanks!

---

### Post by x33a on 2010-02-21
Believe me this has nothing to do with your os. 

just to be sure, you can go to a friends place (preferably different isp), use your laptop with the live cd there, and see if the same error shows.

---

### Post by 2hot6ft2 on 2010-02-21
> **x33a said:**
> Believe me this has nothing to do with your os. 

just to be sure, you can go to a friends place (preferably different isp), use your laptop with the live cd there, and see if the same error shows.
+1 It's definitely not on your end (might add unless it's the router)

Routers these days can do an awful lot. Mine can be a router, AP, repeater, and so much more. Many can even be file servers.

---

### Post by ikt on 2010-02-21
> **forestpiskie said:**
> I had a similar issue recently when freenode was the subject of a bunch of spam - I stupidly :oops: clicked on one of the sly ones.


I was almost (out of curiosity) about to till I saw someone in one of the ubuntu channels got called out for spamming, wait a linux user infected with a virus or something o_O? Did anyone find out what that specific type of malware it was or was it just a generic javascript that joined irc and spammed the message?

---

