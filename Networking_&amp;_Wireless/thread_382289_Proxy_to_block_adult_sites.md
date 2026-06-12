---
title: "Proxy to block adult sites"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by lduperval on 2007-03-11
Hi,

Is there a proxy server that can be used in order to block unwanted sites? Specifically, my children are learning to use the Internet and I want to prevent them from accessing inappropriate content (they are aged 5 to 9). Ideally, I want something that is already configured or something that can access a list of known (or recognizable) sites.

Does this exist anywhere? Something like NetNanny, I guess.

Thanks,

L

---

### Post by SuSUntu on 2007-03-11
Seems like DansGuardian is the most often mentioned software of this type for Linux.

I've never used it, but it seems to be good enough for the Christians who use the Ubuntu CE. See here:

[Ubuntu Christian Edition Edgy Features]("http://www.whatwouldjesusdownload.com/christianubuntu/2007/02/ubuntu-ce-v2x-edgy-features.html")

If you're not a Christian, DansGuardian is flexible enough to be configured to block the site I just linked to. :)

It's in the Edgy Universe repos. You'll also have to install a caching proxy such as squid according to the info I've seen, so this isn't  a quick-n-easy set-up ... you may have to do some reading and configuring. 

I am not aware of any install and forget solutions, so you'll have to wait to see what others may know about that in follow-up posts.

---

### Post by SuSUntu on 2007-03-12
I was doing a little early morning browsing and noticed a HOWTO for DansGuardian:

[http://www.ubuntuforums.org/showthread.php?t=237355](http://www.ubuntuforums.org/showthread.php?t=237355)

The thread has been going long enough to have weeded out a lot of the issues, and the process doesn't look too daunting. However, it generated plenty of questions along the way (which may be viewed as a good or bad thing).

It is interesting to note that the author of the above HOWTO recommends this link if you want a GUI to configure DansGuardian (his HOWTO linked above does not include the GUI):

[http://www.ubuntuforums.org/showthread.php?t=237355](http://www.ubuntuforums.org/showthread.php?t=237355)

While the first link is a step-by-step manual installation (my preference generally), the link / thread immediately above (which seems to have been authored by someone connected with the Ubuntu Christian Edition) relies upon a script for installation.

I recommend reading through both threads and the DansGuardian website docs before deciding which approach to take, if you decide to use DansGuardian at all.

If DansGuardian seems too much to deal with (though better solutions often take more effort), you may try the simplistic approach of blocking sites directly from the web browser, assuming you use FireFox. Two extensions that block (explicit) content are:

ProCon Predator- [https://addons.mozilla.org/firefox/1803/](https://addons.mozilla.org/firefox/1803/)

BlockXXX - [https://addons.mozilla.org/firefox/226/](https://addons.mozilla.org/firefox/226/)

ProCon seems to be the higher rated of the two, for what that might be worth.

Good luck.

---

### Post by lduperval on 2007-03-12
Thanks for the info. I like the Firefox approach for now, however, I don't want to install the extension over and over again (though if I need to, I will).

Does anyone know if an extension can be installed for all users at once? 

I'll be looking at Guardian also.

THanks!


L

---

