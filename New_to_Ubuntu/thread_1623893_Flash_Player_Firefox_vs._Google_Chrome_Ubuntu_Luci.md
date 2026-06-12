---
title: "Flash Player Firefox vs. Google Chrome Ubuntu Lucid"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by JosephPaul on 2010-11-17
New to the forum and Ubuntu,

I am wondering why Flash in Firefox is much slower than Flash in Google Chrome.  Also, according to the Adobe website, Google Chrome has a newer version of Flash installed than Firefox.  Why the difference in versions and performance?  ookla with Firefox is exactly 1/2 as fast as Google Chrome.  Hulu with Firefox sets video to 360p and with Chrome it sets to 480p.  I have tried everything on Google to fix Flash in Firefox, some even claim it is a Kernel problem, but how can that be if Chrome is not affected?  Shouldn't chrome have the same problems as Firefox?  I want to use Firefox because of the Totem, VLC, and Mplayer plug-ins, but Flash is a killer.

Thanks,

JosephPaul

---

### Post by kaldor on 2010-11-17
> **JosephPaul said:**
> New to the forum and Ubuntu,

I am wondering why Flash in Firefox is much slower than Flash in Google Chrome.  Also, according to the Adobe website, Google Chrome has a newer version of Flash installed than Firefox.  Why the difference in versions and performance?  ookla with Firefox is exactly 1/2 as fast as Google Chrome.  Hulu with Firefox sets video to 360p and with Chrome it sets to 480p.  I have tried everything on Google to fix Flash in Firefox, some even claim it is a Kernel problem, but how can that be if Chrome is not affected?  Shouldn't chrome have the same problems as Firefox?  I want to use Firefox because of the Totem, VLC, and Mplayer plug-ins, but Flash is a killer.

Thanks,

JosephPaul

Can you post your computer's specs? 

I have found Flash in Firefox tends to be laggy compared to Chrome (especially on youtube HD videos) and I switch between Chrome and Firefox often.

Google Chrome has Flash built in. That's why it's more up to date than Firefox's plugin which is OS specific.

---

### Post by TBABill on 2010-11-17
One thing that slows Flash is if you are on a 64 bit install but then install ubuntu-restricted-extras. That comes with the 32 bit flash. I always use Lovinglinux's Flash-Aid extension because it detects your OS (32 or 64 bit) and installs from Adobe the correct and most up to date version...and it re-checks every time you open Firefox to see if there is a new version of Flash to install. Takes all the guess work out and flash just works so much better now in 64 bit than 32 bit on a 64 bit Ubuntu install.
 
If that isn't your issue there is also a Flash optimization and Firefox optimization thread on the forum to walk you through various issues so that Firefox works as well as any other browser.

---

### Post by JosephPaul on 2010-11-17
> **kaldor said:**
> Can you post your computer's specs? 

I have found Flash in Firefox tends to be laggy compared to Chrome (especially on youtube HD videos) and I switch between Chrome and Firefox often.

Google Chrome has Flash built in. That's why it's more up to date than Firefox's plugin which is OS specific.
Thanks for the quick reply.  I did notice that the Flash version in Chrome did not match the current version shown on the Adobe website.  Following the numerical sequence, the flash plug-in for Chrome appears much newer than the version Adobe suggests for Linux.  I don't know if they have "wrapped" the windows plug-in, of if they have tweaked it in some way.  Anway, I digress..... my system specs are 

Dell Inspiron 518
Intel Core 2 Quad 2.66
3 GB DDR2 SDRAM
ATI Radeon HD 3450 @ 256MB

---

### Post by JosephPaul on 2010-11-17
> **TBABill said:**
> One thing that slows Flash is if you are on a 64 bit install but then install ubuntu-restricted-extras. That comes with the 32 bit flash. I always use Lovinglinux's Flash-Aid extension because it detects your OS (32 or 64 bit) and installs from Adobe the correct and most up to date version...and it re-checks every time you open Firefox to see if there is a new version of Flash to install. Takes all the guess work out and flash just works so much better now in 64 bit than 32 bit on a 64 bit Ubuntu install.
 
If that isn't your issue there is also a Flash optimization and Firefox optimization thread on the forum to walk you through various issues so that Firefox works as well as any other browser.
Thanks for pointing me in that direction, but I already tried everything relevant on that page.  I did install the "Flash Helper" plug-in to purge and re-install the flash plug-in several times, and then to purge before installing the Flash 10 plug-in from the repositories.  I did notice some marginal improvement after running the Terminal commands to disable Hardware Acceleration, but not much else worked.  I have a 32 bit system, and am glad I don't have to worry about "wrappers" ect. on top of everything else.  

Thanks!

---

### Post by Old_Man_Unix on 2010-11-17
No mystery here.
 
 
This is merely due to a 'special relationship' between Google Chrome (but *not *Chromium) and Adobe Flash. Chrome automatically updates itself - via its own 'repository' - as soon as Adobe *announces* a new version of Flash. This may be before the new version is posted on the Ubuntu repository or even on the company website.
 
Note that the Flash player is integrated into the Chrome browser- it is not an add-on or a plug-in. You can, however, disable the integrated player and use the plug-in if you need to, e.g., for website development purposes. This is one of the reasons why Chrome is *not* an open-source candidate. 
 
I would not be surprised if in turn Chrome served as one of the test beds for Flash. So the version may have already been tested by Chrome before its release. This is often how these special relationships play out behind the scenes although not for public consumption.
 
You can read it here [http://kb2.adobe.com/cps/839/cpsid_83950.html](http://kb2.adobe.com/cps/839/cpsid_83950.html)
 
BTW, Adobe just released a security update for Flash which prompted an update in Chrome - I don't know if that update has made it into the general updating channels as of yet. It is pretty important so you should install it as soon as you can.

---

### Post by JosephPaul on 2010-11-17
Thank you to everyone who responded to my question, I really appreciate your help resolving this in my mind.  My mistake was assuming Firefox and Chrome were playing on an even field with Flash performance in Ubuntu, but it appears Google has used it's corporate clout to "cheat" and claim superiority (sounds a lot like MS?).  It's just another example of Google using open-source to their advantage (Chromium Browser) and then crapping all over the open-source community when they are done.  I loaded Chrome in Ubuntu to see how it handled Flash, and I am now going to remove it because I don't believe their mindset should be supported.

Thanks all,

JosephPaul

---

