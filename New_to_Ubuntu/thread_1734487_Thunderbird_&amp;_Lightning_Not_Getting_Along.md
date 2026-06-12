---
title: "Thunderbird &amp; Lightning Not Getting Along"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Kartari on 2011-04-20
Hi All,

Hope this is a good place for this.  Mozilla's support forum... leaves much to be desired.  So I thought I'd ask here first.

So I finally bit the bullet and installed Ubuntu 10.10 as my primary OS.  I am having trouble with Mozilla Thunderbird's add-on Lightning   (calendar), and I am presently unable to retrieve my calendar that I RELY on!  Unless of course I spend an hour reversing the hardware changes I made and get my Windows hard disk back in this computer (it's a very tight case, and my Win hd is in an external enclosure now) and pass on Ubuntu.

I had no problem installing Thunderbird 3.1 and migrating my profile and emails.  But the calendar showed up blank and was not functioning properly.  So I uninstalled it and tried reinstalling it a few times, to no avail.  I downloaded the Lightning .xpi add-on file from Mozilla's own add-on site, clicked Install as instructed in Thunderbird's add-on manager, but I get this message every time:

[I][FONT="Verdana"]Incompatible Extension:
"Lightning" could not be installed because it is not compatible with your Thunderbird build type (Linux_x86_64-gcc3). Please contact the author of this item about the problem.[/FONT][/I]

I noticed on [Mozilla's Lightning Project Home]("http://www.mozilla.org/projects/calendar/lightning/") site, while x64 is not specifically mentioned as being incompatible, Linux x86 is specifically mentioned (not x64) as being supported.  And I did install the x64 version of Ubuntu.

I also found on [Lightning's system requirements page]("http://www.mozilla.org/projects/calendar/lightning/system-requirements.html") that there are several packages that are needed for Lightning to work.  I ran Synaptic Package Manager and only found one of the five mentioned packages even listed, libstdc++5.  It was not checked on, so I installed it with Thunderbird closed, restarted it and tried installing Lightning again to no avail.

I am still very new to Ubuntu, and do not even know how to reliably find these other packages, let alone know if it is even a) advisable for my particular Linux version (Ubuntu 10.10) or b) worthwhile to try since I am wondering if x64 is simply not supported?  Anybody know about this, and what I can try?  Otherwise, I'll have to try to figure out why I can't get VirtualBox to work properly with my Windows CDs (another story, for another day).  Thanks!

---

### Post by f1r3br4nd on 2011-04-21
Hi. You've made the same move I have a few years ago, and I mostly don't regret it. However, you've stumbled onto one of the problems that the developers (of both Ubuntu and of Lightning) don't give a damn about and it will be a long time, if ever, before this is fixed. This has been an issue at least since 2008 and there STILL isn't a proper Lightning package available. 

In unrelated news, there are several hundred different types of MP3 players, BitTorrent clients, Tetris clones, RSS readers, and desktop clock widgets to choose from. Welcome to Ubuntu and to Linux in general.

Anyway.

You may find the following links useful as well for migrating your data after the extension is installed:
[http://brizoma.wordpress.com/2010/05/04/sunbird-and-lightning-removed-from-ubuntu-10-04-lucid-lynx/](http://brizoma.wordpress.com/2010/05/04/sunbird-and-lightning-removed-from-ubuntu-10-04-lucid-lynx/)
[http://brizoma.wordpress.com/2010/10/13/sunbird-and-lightning-removed-from-ubuntu-10-10-maverick-meerkat/](http://brizoma.wordpress.com/2010/10/13/sunbird-and-lightning-removed-from-ubuntu-10-10-maverick-meerkat/)

Here is a lightning version that might work for you:
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/)

Good luck. Please message back and let us know if this works for you with the latest version of Thunderbird-- I've been holding off on upgrading because once I found a combination of Thunderbird and Lightning versions that work well together, I've been afraid to mess with it.

---

### Post by Kartari on 2011-04-21
f1r3br4nd,

Thank you!  Works perfectly.  All my calendar data came right up, no need to do anything but install the add-on in 5 seconds.  I got VirtualBox to run correctly last night (nothing a few settings changes couldn't fix) and thought I'd have to resort to running Thunderbird in virtual Win7 for Lightning.  This is much more convenient though.

And thanks for the Linux welcome.  I've actually been toying around with Ubuntu very infrequently for years, preparing to switch by using Firefox, Thunderbird, OpenOffice.org, etc.. and I even setup my laptop to dual boot Win7 and Ubuntu 9 last year.  But I wound up not using it very often, as everything I use was still in Windows on my laptop and desktop, and coming from Windows, I expected many unforeseeable problems and lots of time wasted.  So far I'm very impressed with the very few problems, Lightning being the only major issue so far.  But this is the first time I'll be using it regularly as my main OS (with Win7 via VirtualBox for what won't run on Linux).  Hope my daily dose of BSODs are all in the past now, lol. :D

---

### Post by Kartari on 2011-04-21
Btw, I'm actually using Thunderbird version 3.1.8, not 3.1.9.  For some reason, I cannot find the update settings... no time to try this now, but I'll try updating Thunderbird and see if all is well.

---

### Post by collisionystm on 2011-04-21
> **Kartari said:**
> Hi All,

Hope this is a good place for this.  Mozilla's support forum... leaves much to be desired.  So I thought I'd ask here first.

So I finally bit the bullet and installed Ubuntu 10.10 as my primary OS.  I am having trouble with Mozilla Thunderbird's add-on Lightning   (calendar), and I am presently unable to retrieve my calendar that I RELY on!  Unless of course I spend an hour reversing the hardware changes I made and get my Windows hard disk back in this computer (it's a very tight case, and my Win hd is in an external enclosure now) and pass on Ubuntu.

I had no problem installing Thunderbird 3.1 and migrating my profile and emails.  But the calendar showed up blank and was not functioning properly.  So I uninstalled it and tried reinstalling it a few times, to no avail.  I downloaded the Lightning .xpi add-on file from Mozilla's own add-on site, clicked Install as instructed in Thunderbird's add-on manager, but I get this message every time:

[I][FONT=Verdana]Incompatible Extension:
"Lightning" could not be installed because it is not compatible with your Thunderbird build type (Linux_x86_64-gcc3). Please contact the author of this item about the problem.[/FONT][/I]

I noticed on [Mozilla's Lightning Project Home]("http://www.mozilla.org/projects/calendar/lightning/") site, while x64 is not specifically mentioned as being incompatible, Linux x86 is specifically mentioned (not x64) as being supported.  And I did install the x64 version of Ubuntu.

I also found on [Lightning's system requirements page]("http://www.mozilla.org/projects/calendar/lightning/system-requirements.html") that there are several packages that are needed for Lightning to work.  I ran Synaptic Package Manager and only found one of the five mentioned packages even listed, libstdc++5.  It was not checked on, so I installed it with Thunderbird closed, restarted it and tried installing Lightning again to no avail.

I am still very new to Ubuntu, and do not even know how to reliably find these other packages, let alone know if it is even a) advisable for my particular Linux version (Ubuntu 10.10) or b) worthwhile to try since I am wondering if x64 is simply not supported?  Anybody know about this, and what I can try?  Otherwise, I'll have to try to figure out why I can't get VirtualBox to work properly with my Windows CDs (another story, for another day).  Thanks!


I am not sure what mail host you are using, but I would not user thunderbird or evolution...etc.

Check this out

```
 

http://www.zimbra.com/products/desktop.html


```


Free, Opensource, and awesome. I have google mail and it automatically syncs my contacts and calendar flawlessly. Looks better to.  :)

---

### Post by Kartari on 2011-04-26
Hi collisionystm,

Thanks for the suggestion.  Looks cool, but I've grown very fond of Thunderbird and it's working fine now.

---

### Post by Kartari on 2011-04-26
> **Kartari said:**
> Btw, I'm actually using Thunderbird version 3.1.8, not 3.1.9.  For some reason, I cannot find the update settings... no time to try this now, but I'll try updating Thunderbird and see if all is well.

Huh, is it my imagination or is Thunderbird supposed to autoupdate like Firefox does?  I could swear it did this when I was using Windows, though I am not 100% sure.  I cannot find any update settings except one in Edit > Preferences > Advanced, and it just asks if I want to autocheck for updates to add-ons.  I'm still at 3.1.8 and 3.1.9 has been out for a while now...

---

### Post by Azdour on 2011-04-26
Hi,

Updates for Thunderbird and Firefox come through Ubuntu's Update mechanism rather than through an update menu item that you are used to in Windows.

If you are looking for newer versions just check System | Administration | Update Manager.

---

### Post by Kartari on 2011-04-27
Hi Azdour,

Hmmm, I don't see anything that refers to Thunderbird or Firefox in the Update Manager.  I can understand why Firefox is not in there (I have 3.1.16, the latest version of 3.6... 4 would be a major update that I would usually do manually on Windows anyway).  But I have Thunderbird 3.1.8 and 3.1.9 is the latest version.

Must I change some settings to get Thunderbird to autoupdate?  I do have Independent and Independent (Source Code) checked on in Other Software inside Update Manager's Settings.  Not sure what else to look for.

---

### Post by alphacrucis2 on 2011-04-27
> **Kartari said:**
> Hi Azdour,

Hmmm, I don't see anything that refers to Thunderbird or Firefox in the Update Manager.  I can understand why Firefox is not in there (I have 3.1.16, the latest version of 3.6... 4 would be a major update that I would usually do manually on Windows anyway).  But I have Thunderbird 3.1.8 and 3.1.9 is the latest version.

Must I change some settings to get Thunderbird to autoupdate?  I do have Independent and Independent (Source Code) checked on in Other Software inside Update Manager's Settings.  Not sure what else to look for.

Ubuntu don't often backport stuff other than security fixes. If you want Firefox 4, read Loving Linux's megathread stickied at the top of the absolute beginners forum. Basically you add the moz stable ppa to your repos.

---

