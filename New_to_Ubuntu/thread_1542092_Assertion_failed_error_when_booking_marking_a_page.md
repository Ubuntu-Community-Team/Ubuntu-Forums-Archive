---
title: "Assertion failed error when booking marking a page in Firefox"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by Clever_Username on 2010-07-30
Does anyone know what this assertion failed error means? I'm running FF 3.6.8 on Lucid 10.0.4.
I am able to create a bookmark, but only after clicking through the error.
Thanks so much

---

### Post by lovinglinux on 2010-07-30
Where exactly are you creating the bookmark? Inside Firefox or on your desktop?

---

### Post by Zorgoth on 2010-07-30
I do not know, but I used to get Assertion Failed errors when I hadn't restarted firefox after updating it.

---

### Post by jonnytango on 2010-07-31
I had the same issue - currently running Ubuntu 10.04 and Firefox 3.6.8.  Check your Firefox add-ons to see if you have one called "webfav", which saves web favorites (bookmarks) into Ubuntu's Netbook Remix (UNR) Launcher.  I initially installed Ubuntu with UNR, but subsequently removed it.  However, I discovered the webfav add-on was not removed along with UNR (possibly a bug?), which I figured was causing the problem.  Disabling it seems to have fixed the issue for me.

---

