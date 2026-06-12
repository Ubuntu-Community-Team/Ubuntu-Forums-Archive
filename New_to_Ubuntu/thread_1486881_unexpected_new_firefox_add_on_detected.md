---
title: "unexpected new firefox add on detected?"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by robulus on 2010-05-18
Hi folks,
I'm using 9.04 - and firefox 3.0.19  I was browsing some webpages about mysql today and for some reason the a pop up displayed itself saying that my computer may be infected.
I couldn't interact with the browser, so I had to use kill -9 to get rid of the firefox process.

However the next time i opened firefox the add-ons window said that '1 new add on has been installed'  - and I'm pretty sure I haven't added on anything for a good few days. 

Is there a way to tell what actually was installed - are there any logs etc to give me peace of mind?
cheers,
Rob.

---

### Post by sydbat on 2010-05-18
> **robulus said:**
> Hi folks,
I'm using 9.04 - and firefox 3.0.19  I was browsing some webpages about mysql today and for some reason the a pop up displayed itself saying that my computer may be infected.
I couldn't interact with the browser, so I had to use kill -9 to get rid of the firefox process.

However the next time i opened firefox the add-ons window said that '1 new add on has been installed'  - and I'm pretty sure I haven't added on anything for a good few days. 

Is there a way to tell what actually was installed - are there any logs etc to give me peace of mind?
cheers,
Rob.Have you checked your "add-on" list (Tools > Add-ons) to see if there is something different there?

Also, I think you could tell by typing in the address line ```
about:plugins
``` and see if there is anything unusual there.

And you should upgrade to the latest Firefox if you can. That should help with security concerns.

---

### Post by the.phantom on 2010-05-18
if ff said you have one new addon have you looked at the list of addons and see any new ones?
and in ff settings
edit/preferences click the security tab
do you have
"warn me when sites try to install adons" checked?

---

### Post by muteXe on 2010-05-18
No idea but FF is now on something like 3.6.2, after a security flaw was found.
I might be wrong, but using such an old version of FF isn't completely safe.

---

### Post by robulus on 2010-05-18
Hi guys, 
cheers for the ideas :)  I've eyeballed the list, and those entries that are displayed seem fine - both on the plugin/addon list and using the about:plugins

I do have the "warn me when sites try to install adons" checked - so I'm surprised to see the message.  and as soon as I saw the popup i just turned to the commandline and killed the process.

I never updated the version of FF since I tend to rely on the update manager for  updates, and it's never prompted me with an update option for firefox. (And the 'check for updates' option is greyed out - I'm assuming this is becase I'm not running it as root')

I'll try and update FF now.  But I'd still be curious as to what actually happened 8-/

---

### Post by robulus on 2010-05-18
oh and just an update - running it as root does enable the 'check for updates' option - but running it returns no results.  I think it must be down to the version of ubuntu I'm using...maybe time to update to the latest and greatest (gulp) :-p

---

### Post by cpplinux on 2010-05-18
go to .mozilla/firefox/xxxxx.default/extensions under your home directory, do you see something you did not install?

---

### Post by robulus on 2010-05-18
Hi - I checked out that location on disk, but everything listed here matches what I can see on the add on list...apart from something called 'Ubuntu Firefox Modifications 0.7'  Which I assumed was just provided by default - though to be honest I never noticed it before, since i never looked.

Saying that - there is no folder in the extensions directory that corresponds to that extension. 8-/  Does everyone else here have it?

---

### Post by Chesamo on 2010-05-18
The warning you got is a virus that's infecting GoDaddy hosts. It's a set of PHP instructions dropped onto the files. I had to clean it out on another server. It doesn't affect you -- the client -- but I'd personally clean my cookies and cache to be safe.

---

### Post by lovinglinux on 2010-05-18
> **robulus said:**
> oh and just an update - running it as root does enable the 'check for updates' option - but running it returns no results.  I think it must be down to the version of ubuntu I'm using...maybe time to update to the latest and greatest (gulp) :-p

If you started Firefox with sudo instead of gksudo, then you need to fix permission issues you just created. Is not a good idea to start the browser with root permission and you should never use sudo for that.

See the first item from [here](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html).

> **Chesamo said:**
> The warning you got is a virus that's infecting GoDaddy hosts. It's a set of PHP instructions dropped onto the files. I had to clean it out on another server. It doesn't affect you -- the client -- but I'd personally clean my cookies and cache to be safe.

I would suggest creating a new Firefox profile, copy only the files you need from the old one and delete it.

See [[COLOR="Sienna"]**Profiles**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/profiles.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

