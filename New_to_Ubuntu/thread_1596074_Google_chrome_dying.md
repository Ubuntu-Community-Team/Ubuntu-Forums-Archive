---
title: "Google chrome dying"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by oregonbob on 2010-10-13
For nearly a year I've been using Google Chrome and finally made the browser my default, but now I have had to abandon it completely and go back to using the slower Firefox on my Lucid 10.04 64bit machine. Chrome on Windows seems to still function. What is strange is the bugs seemed to cascade and gradually multiply until it finally quit altogether and fails to display a single page. I have a nvidia card and heard rumors that Chrome's flash on 64bit with nvidia may be the combination that sends Chrome into fits.

It all started with those "Ah Snap" errors, then pages would fail to display while loading without any error messages.

Anyone else having similar chrome errors or possibly a solution?

---

### Post by Ctrl-Alt-F1 on 2010-10-14
I'm not having any errors that I'm aware of.  I'm using Chrome 6.0.472.63 on Ubuntu 10.04 x64.

As for Chrome's flash, I don't use it.  It's not enabled by default in the Linux version so I'm just using whatever flashplugin-installer downloads, which I presume is 32bit flash.

---

### Post by tom.swartz07 on 2010-10-14
> **oregonbob said:**
> For nearly a year I've been using Google Chrome and finally made the browser my default, but now I have had to abandon it completely and go back to using the slower Firefox on my Lucid 10.04 64bit machine. Chrome on Windows seems to still function. What is strange is the bugs seemed to cascade and gradually multiply until it finally quit altogether and fails to display a single page. I have a nvidia card and heard rumors that Chrome's flash on 64bit with nvidia may be the combination that sends Chrome into fits.

It all started with those "Ah Snap" errors, then pages would fail to display while loading without any error messages.

Anyone else having similar chrome errors or possibly a solution?

I was having very similar problems and I was able to fix it.

Navigate to the .config folder hidden in your home folder. (press CTRL H to see it) and look for the folder that says chrome or chromium. Delete it.

Granted, this will effectively 'reset' all of your options, but it will also clear the things that are causing the problem.


Hope this helps!

---

### Post by amjjawad on 2010-10-14
> **oregonbob said:**
> For nearly a year I've been using Google Chrome and finally made the browser my default, but now I have had to abandon it completely and go back to using the slower Firefox on my Lucid 10.04 64bit machine. Chrome on Windows seems to still function. What is strange is the bugs seemed to cascade and gradually multiply until it finally quit altogether and fails to display a single page. I have a nvidia card and heard rumors that Chrome's flash on 64bit with nvidia may be the combination that sends Chrome into fits.

It all started with those "Ah Snap" errors, then pages would fail to display while loading without any error messages.

Anyone else having similar chrome errors or possibly a solution?

I suggest to have a look here: [http://www.google.com/support/forum/p/Chrome?hl=en](http://www.google.com/support/forum/p/Chrome?hl=en)

Last time I was using Chrome on Windows XP, it was crashing even before I type the address of any website. I used google to find out what's going on and it happened that IDM (Internet Download Manager) is the reason of these crashes. After that, never had any problem at all. Point is, check the Chrome's forum, I guess you could find the answer there.

---

