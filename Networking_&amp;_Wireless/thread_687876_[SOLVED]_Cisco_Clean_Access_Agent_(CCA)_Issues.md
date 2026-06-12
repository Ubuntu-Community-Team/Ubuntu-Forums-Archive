---
title: "[SOLVED] Cisco Clean Access Agent (CCA) Issues"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by integr8e on 2008-02-04
I have an aggravating problem I need help with: my university uses Cisco's Clean Access Agent (CCA) to manage network connections - i.e. validate the user has permission to connect to the network.  To connect from a laptop, you must first connect to the wireless network via ESSID + HEX key (no problem), and then log into the network using your username and password before you can actually use the internet.  From Windows, this is done by way of CCA, and on Mac's and Linux PC's, you should just be able to enter your username and PW from a login screen that opens from a browser window.

The problem is, whenever I enter my username and PW from Firefox/Konqueror in Kubuntu, I'm redirected to a page explaining my university uses CCA ... and that I need to download and install it before I can connect to the network.  CCA is strictly Window$ based, and doesn't work in Linux (I unsuccessfully attempted using Wine, not really expecting it to work).  I found [**_this thread_**](http://ubuntuforums.org/showthread.php?t=599013) explaining how to modify my /etc/nsswitch.conf file to connect to the network, but still cannot get it to work.  The Help Desk at my university is unfamiliar with Linux, so if anybody has experience on the subject, please help; I'd really like to switch entirely to Kubuntu, and this is the only problem holding me back.

---

### Post by integr8e on 2008-02-05
Got it!!!  If you open a Konqueror window and change its browser identity to "Netscape Navigator version 4.76 on Mac PPC", the CCA server thinks I'm on a Mac and lets me log in (seems simple enough)!!!

*02/08/2008 - For those interested, [**_here is the HowTo I've posted_**](http://kubuntuforums.net/forums/index.php?topic=3091091.0) explaining the required steps.*

---

### Post by Twiggy003 on 2008-02-25
What about with Firefox? any idea on changing that identity?

---

### Post by integr8e on 2008-02-25
> What about with Firefox? any idea on changing that identity?

No, as far as I know, you can't change the identity of Firefox under normal circumstances - I'm sure you could with some serious hacking, but that's currently beyond my skill level.  Once you log in with Konqueror, however, you can browse freely with Firefox :)

---

### Post by The Cog on 2008-02-25
Firefox has an extension called "User agent switcher" which allows you to change the declared browser identity. Unfortunately, you cannot configure this identity on a per-web-site basis but if you don't mind using the same declared identity everywhere, it works just fine.

---

### Post by integr8e on 2008-02-25
Cool!  I didn't know about that one...unfortunately for me, as I've ventured into the vast, largely unknown frontier of the Kubuntu HH alpha5 + KDE 4.0.1, I will be unable to use this plugin until it's updated to support FF3 :P

---

### Post by Twiggy003 on 2008-02-25
Thanks for the responses.  I seem to have issues with connecting.  It claims to work with Linux (and Mac) but it redirects to the page where I have to download the client (after logging on in the main page).  Unless im missing something obvious on it I can't seem to connect.  Any ideas how you connected using Ubuntu?

Thanks

---

### Post by Twiggy003 on 2008-02-26
When using the agent to pretend it's IE it asks for ActiveX, would it work if i WINE activeX and IE for that matter?  I can't try it at the mo, but would that work?

---

### Post by Twiggy003 on 2008-02-29
Even pretending to be netscape doesnt work... any ideas?

Edit: even tried PrefBar as Netscape/Mac yet that caused a segmentation fault somehow.

Also WINE + IE + Cisco clean access doesnt work.

I think i'll see if computer services have got around to working out what linux is.

---

### Post by integr8e on 2008-03-14
> Also WINE + IE + Cisco clean access doesnt work.

I feel you :)  As I stated before, I use the Firefox 3 beta which isn't compatible with the plugin (so I can't play around with it to help you), but if you're not anti-KDE, why don't you give Konqueror a try?

---

### Post by Twiggy003 on 2008-03-15
Well, im not entirely pro-KDE.  I kinda gave up trying and ended up actually doing work on my laptop instead.  I could try konqueror, just that im limited to space, my harddrive is only 4GB (eeepc 701).

but recently I had to install qt anyway, so I  may just give konqueror a try.

---

