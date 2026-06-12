---
title: "Spyware"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Quarkrad on 2009-01-07
I'm a newbie to Linux/Ubuntu. I have asked a number of questions re virus ad spyware attacks and all have come back with a '.....don't worry....' theme.  This morning I logged out of my TalkTalk (AOL) web mail account and noticed it was taking a long time to get back to the [http://www.aol.co.uk/talktalk](http://www.aol.co.uk/talktalk) log-in screen page.
At the bottom of the screen I looked to see where the browser was trying to go to and instead of [www.aol.co.uk/talktalk](www.aol.co.uk/talktalk) it was trying something like  .adfarm.mediaplex........

I closed down the browser and googled as I have never heard of this site.  It appears it is spyware.   In win mode I would d a virus check and fire up Spybot to do a spyware scan.
what do I do in Ubuntu?   Am I blissfully unaware my nice Linux install is infected with spyware/mailware etc?

Ubuntu 8.10
Firefox 3.0.5

Rds...

---

### Post by mikewhatever on 2009-01-07
It's funny, cause I just googled 'adfarm.mediaplex' too, and here is a quote from one of the results:
> [http://answers.google.com/answers/threadview/id/397086.html](http://answers.google.com/answers/threadview/id/397086.html)

I am hainvg problems with spyware I have run adaware and spybot the
most current versions and I cannot get rid of these popups.

Apparently, the very program you mentioned was unable to rid that poster of the spyware. Scanning your disk for malware, hearing it grind and being unable to use the computer for a while may be providing some piece of mind, but aren't very helpful after all.
Is there any substantial evidence that you are infected with spyware? Do you see unwanted popups? Do you get redirected randomly to various web sites?

---

### Post by SteveDee on 2009-01-07
Take a look at this article: [http://www.linuxplanet.com/linuxplanet/tutorials/6620/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6620/1/)

I use the NoScript Firefox add-in, and have a firewall on my router, but do little else to protect my Intrepid based computers.

---

### Post by 3rdalbum on 2009-01-07
The "adfarm.mediaplex" address is not necessarily what page the browser is trying to load into the main frame; it could be (and probably is) a page or image that it is trying to load into an inline frame. Trying to load this image on the current page is probably why it's taking longer to go to a new page. Webmail services are financially supported by advertising, and the advertising is always out-sourced to other companies who have their own servers.

If you ran a spyware check every time your browser showed it loading an address other than the main page, then you would be running spyware checks after every single website.

In short: Nothing to worry about on any operating system. And especially nothing to worry about on Linux.

---

### Post by Quarkrad on 2009-01-07
Thank you all - I see the point(s) you have made.  Now installing clamav for piece of mind.

---

### Post by scorp123 on 2009-01-07
> **Quarkrad said:**
> it was trying something like  .adfarm.mediaplex........ That's an advertisement server. Pretty much standard on many web sites. Annoying maybe, yes. But nothing illegal. :D

---

