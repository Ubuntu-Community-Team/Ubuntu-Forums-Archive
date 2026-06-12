---
title: "Firefox 3.5?"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by dmaxel on 2009-10-11
Hi there! Sorry if this topic has been touched repeatedly, but all the topics veer right around my main question.

OK, so right now my system is running Firefox 3.0.14. I know that Firefox 3.5.3 is out. How come there isn't a full Firefox package for Ubuntu for 3.0.14 users to upgrade to? I know that Ubuntu has 3.5 in it's repositories, but then it's not the "real deal" and is branded with Shiretoko. Any help?

---

### Post by michael37 on 2009-10-11
> **dmaxel said:**
> Hi there! Sorry if this topic has been touched repeatedly, but all the topics veer right around my main question.

OK, so right now my system is running Firefox 3.0.14. I know that Firefox 3.5.3 is out. How come there isn't a full Firefox package for Ubuntu for 3.0.14 users to upgrade to? I know that Ubuntu has 3.5 in it's repositories, but then it's not the "real deal" and is branded with Shiretoko. Any help?

Yep, that's the real deal!  It's named Shiretoko just to differentiate from the Firefox 3. 

In next version, Karmic, Firefox 3.5 will be named "Firefox", but I can assure you that "Shiretoko" will be gracefully upgraded to the proper name soon.

---

### Post by coldReactive on 2009-10-11
Use ubuntuzilla. You'll have to reinstall flash for it though more than likely.

---

### Post by dmaxel on 2009-10-11
> **michael37 said:**
> Yep, that's the real deal!  It's named Shiretoko just to differentiate from the Firefox 3. 

In next version, Karmic, Firefox 3.5 will be named "Firefox", but I can assure you that "Shiretoko" will be gracefully upgraded to the proper name soon.
Awesome, then I'll just wait the few days until Karmic gets released. I'll update as soon as I can. :D

---

### Post by aysiu on 2009-10-12
If you prefer the Mozilla-branded binary, this will help you:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

If you use this method or UbuntuZilla, you do **not** need to reinstall Flash.

---

### Post by coldReactive on 2009-10-12
> **aysiu said:**
> If you prefer the Mozilla-branded binary, this will help you:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

If you use this method or UbuntuZilla, you do **not** need to reinstall Flash.

I had to on AMD64, the flash had to be copied to an opt directory. This won't happen in karmic though.

---

### Post by aysiu on 2009-10-12
64-bit may be a different procedure, granted. Yes.

---

### Post by Lunx on 2009-10-12
> **dmaxel said:**
> Awesome, then I'll just wait the few days until Karmic gets released. I'll update as soon as I can. :D

I upgraded to Karmic about a week ago and have had a few issues with 3.5.3 freezing and crashing on me. Also had trouble getting it to quit, would close window and it would still be running, needed to run killall firefox (I since worked out it was the greasemonkey add-on causing it, disabled greasemonkey and problem is sorted). I ran some system updates yesterday and now FF seems to be running more stable, no issues with it crashing again.

Having now mentioned the bad parts, I'll say that overall I'm very happy using this new version, it is very noticeable how much faster than the old version it is. I used to use FF all the time back in the v2 days, but then I switched to Opera a couple of years ago. I recently started an on-line university course and had compatability issues between Opera and the uni website, so I began using FF v3.0.14 and was more than happy (I found Zotero and now I can't live without it LOL). I still use Opera as it's great for handling my email and rss feeds, but find I'm using FF an equal amount or perhaps a little more of the time now. Old version of FF was comparable to Opera in speed on most sites, but no contest now, FF3.5 is quite a bit faster than Opera 10, no question.

---

### Post by mikechant on 2009-10-12
> How come there isn't a full Firefox package for Ubuntu for 3.0.14 users to upgrade to?
I don't think anyone has really addressed the 'why'.
The idea is that for a given release of Ubuntu, it has been extensively tested with a particular version of Firefox - in this case 3.0 - and this is the official release of Firefox for the entire lifetime of that version of Ubuntu. So the only official Firefox changes for that Ubuntu release will be the fixes (typically security/stability) for that version of Firefox i.e. 3.0.13->3.0.14 etc.

Keeping the new release seperate with a different name and not including it in the normal updates emphasizes that this is an unofficial change which would presumably not be supported (if you had a paid maintenance contract for example).

---

