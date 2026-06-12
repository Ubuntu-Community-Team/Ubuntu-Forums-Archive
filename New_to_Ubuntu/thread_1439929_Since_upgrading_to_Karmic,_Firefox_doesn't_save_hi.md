---
title: "Since upgrading to Karmic, Firefox doesn't save history"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by tarahmarie on 2010-03-26
Hi!

Since I upgraded my distro, Firefox won't save my history. This is my home machine, so it's seriously irritating to have to login to all six of my tabs (gmail, RTM, etc) every single time I close my browser and reopen it.  FF is set to remember history; this has never happened before.  Is there some setting that I need to change in Karmic? I'm running the same FF version on a Windows box, and I don't have this problem there.

---

### Post by mkvnmtr on 2010-03-26
Open up the preferences and set the history the way you like it. Might have to restart the browser for it to take effect.

---

### Post by tarahmarie on 2010-03-26
> **mkvnmtr said:**
> Open up the preferences and set the history the way you like it. Might have to restart the browser for it to take effect.

I may not have emphasized enough in my original post that Firefox is already set to remember history.

---

### Post by asmoore82 on 2010-03-26
are you talking about remember history, remember tabs, or remember passwords?

---

### Post by tarahmarie on 2010-03-26
> **asmoore82 said:**
> are you talking about remember history, remember tabs, or remember passwords?

Specifically, remembering passwords, usernames, etc.  I have changed no settings in FF since upgrading, yet now, each and every time I close and reopen a browser, I have to re-input my un and pw to every site. That includes this one; it's quite annoying.  

Cookies are being set; i.e. there is an ubuntuforums.org cookie in my browser.

Konqueror DOES save my history, but it's a crappy browser and I like my dev plugins in FF.

---

### Post by lovinglinux on 2010-03-27
Make sure you don't have the option "Clear History when Firefox closes" or at least that the "Passwords" option is not selected. If that isn't the problem, then close Firefox and move the files signons.sqlite and key3.db from your Firefox profile folder (~/.mozilla/firefox/something.default/) then start Firefox.

For additional info see [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by tarahmarie on 2010-03-30
Neither of those two solutions worked. I also don't find any information elsewhere online; I've tried editing each of the about:config options concerning clearing history, and nothing seems to prevent Firefox from failing to sign me into all my tabs when I reopen it.

---

### Post by lovinglinux on 2010-03-30
> **tarahmarie said:**
> Neither of those two solutions worked. I also don't find any information elsewhere online; I've tried editing each of the about:config options concerning clearing history, and nothing seems to prevent Firefox from failing to sign me into all my tabs when I reopen it.

Create a new FF profile and check if the problem persists.

---

