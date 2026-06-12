---
title: "How do you secure the chromium browser?"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by JOOBIE on 2011-08-17
First off, let me say hello and thanks for having me on the ubuntu help forums. I am an almost complete novice, so I appreciate the help & overall sense of community found here & other forums as well.

Now then, how do you truly secure the chromium browser? I love chromium and it is lightening fast, but it doesn't have a NOSCRIPTS equivalent (in fact, my other browser is Opera and it is the only one I know of that has the NOTSCRIPTS equivalent.)

So since linux is pretty much safe in all respects for your comp, but no OS can make your browser secure (the place where you get hit the hardest by malware) what should I do if I want to use chromium?

Thanks in advance for any helpful feedback.:)

---

### Post by Neoncamouflage on 2011-08-17
Hmm, could [AdBlock]("https://chrome.google.com/webstore/detail/gighmmpiobklfepjocnamgkkbiglidom") be what you're looking for?

I use Chrome, replaced Firefox with it not 2 minutes after starting Ubuntu, and have never had a problem with it.

---

### Post by SavageWolf on 2011-08-17
I feel like things like NoScript are overkill, JavaScript can't access any files on your computer or even make cross site requests (Google.com can't access facebook.com, for example). There are XSS attacks, which use security flaws in the server, but they can only get anything you actually send (or create) on/to the site; only "small" sites are vulnerable to them.

What I do is use GPass and generate a 15 char password for every new site. See [http://xkcd.com/792/](http://xkcd.com/792/)

---

### Post by JOOBIE on 2011-08-17
Lololol!!!

You've certainly peeked my interest in gpass.

---

### Post by kerry_s on 2011-08-17
i use this: [https://chrome.google.com/webstore/detail/npldlchgpnaooionoepgcgmhcocclgnf](https://chrome.google.com/webstore/detail/npldlchgpnaooionoepgcgmhcocclgnf)

i only use a few add ons

---

### Post by Dangertux on 2011-08-17
> **SavageWolf said:**
> I feel like things like NoScript are overkill, **JavaScript can't access any files on your computer or even make cross site requests (Google.com can't access facebook.com, for example)**. There are XSS attacks, which use security flaws in the server,** but they can only get anything you actually send (or create) on/to the site; only "small" sites are vulnerable to them.**

What I do is use GPass and generate a 15 char password for every new site. See [http://xkcd.com/792/](http://xkcd.com/792/)


Umm...I don't mean to sound condescending so please don't take offense, but the bolded parts of what I quoted are COMPLETELY false.

First off, JavaScript can and frequently will access things it's not supposed to. Sure you have the whole same origin argument but that can be manipulated see my next point.

Secondly, one of the MAIN purposes for cross site scripting and cross site request forgery are to bypass the same origin control. 

Third, only if sites that get 250,000+ pageviews per day are considered small...

On a side note, funny comic ;-)

---

### Post by JOOBIE on 2011-08-18
The link you submitted says that the item is no longer available. It does look promising, maybe I can find it somewhere in their store.

---

### Post by bodhi.zazen on 2011-08-18
See:

[https://chrome.google.com/webstore/detail/odjhifogjcknibkahlpidmdajjpkkcfn](https://chrome.google.com/webstore/detail/odjhifogjcknibkahlpidmdajjpkkcfn)

and for further advice 

[http://bodhizazen.net/Tutorials/Privacy#Chrome](http://bodhizazen.net/Tutorials/Privacy#Chrome)

---

### Post by kerry_s on 2011-08-19
> **JOOBIE said:**
> The link you submitted says that the item is no longer available. It does look promising, maybe I can find it somewhere in their store.

sorry, looks like they pulled it.
[http://theultimateaye.blogspot.com/2011_08_01_archive.html](http://theultimateaye.blogspot.com/2011_08_01_archive.html)

guess i'll have to look for something new that's supported.

okay, switched to scriptno:
[https://chrome.google.com/webstore/detail/oiigbmnaadbkfbmpbfijlflahbdbdgdf](https://chrome.google.com/webstore/detail/oiigbmnaadbkfbmpbfijlflahbdbdgdf)

it just takes a while to white list the sites you do want.
you can go into the options & turn on adblocking.
ps: make sure you remove only on the option page, pressing clear will lock the browser.

---

### Post by trozamon on 2011-08-19
If chromium doesn't ship with an App Armor profile, you could make one or enhance the current profile.

---

### Post by JOOBIE on 2011-08-22
No problem. I did find an app that allows whitelisting & I like it except for the fact that it shuts things out when I surf on to a page that hasn't been approved. I like to use noscripts with WOT on FF, maybe i will use the white list along with WOT on Chromium. That should be sufficient to protect privacy along with private browsing-I hope.

---

