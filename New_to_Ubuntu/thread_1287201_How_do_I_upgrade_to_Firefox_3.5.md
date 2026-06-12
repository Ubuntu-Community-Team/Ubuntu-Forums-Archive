---
title: "How do I upgrade to Firefox 3.5"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-09
I thought I had upgraded (via Synaptics GUI) to Firefox 3.5 from 3.08, but checking showed Firefox was still 3.08.

I uninstalled (via Synaptics) both versions - as it was showing both versions installed, then installed V3.5 - It still shows up as 3.08. Any ideas?

For some reason prior to this I now have something called Shiretoko installed which looks exactly like 3.5 but says it's some sort of BETA.

Can I just get Firefox 3.5?

---

### Post by aheckler on 2009-10-09
[http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html](http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html)

From the comments: 

> Please do not mix things up. Users that installed ubuntu jaunty, get a really stable user experience. Our promise is to not get upgrade them automatically to new major upstream versions. So everyone except those tech savy folks that really want it now will stay with firefox-3.0 until they upgrade to karmic. Once they upgrade to karmic they will get firefox 3.5 using the proper firefox branding.

If its so important for you to get the official branding, just upgrade to karmic. The stability is probably similar to what you would get in a distro where you get always upgraded to the latest major versions. Try it and then decide if thats the stability you want. If it feels to you lik it might be unstable, then you are in fact someone who wants the stable user experience approach as we deliver it in ubuntu.

Once you understand that and understand why we dont upgrade users to new major upstream versions in a stable ubuntu release, you will understand why your complains and concerns about us not being user friendly are way off.

We are so user friendly because we do not update users to the next major versions of any major desktop component. That’s what distribution upgrades are for. When karmic gets out, users can upgrade to it and get a great and stabilized user experience for a properly branded firefox 3.5.

---

### Post by sandyd on 2009-10-09
```

sudo apt-get install firefox-3.5

```
or upgrade to karmic - 3.5 is installed by default.

p.s. the menu item will be calles shirekto.

---

### Post by smileyguy on 2009-10-09
Thanks Heckler - so once more for the dummies - Firefox 3.5 isn't officially supported yet for Ubuntu 9.04?

---

### Post by aheckler on 2009-10-09
Technically no, but *de facto* the situation is that you can use it if you want. I'd just wait, you have less than a month. :-)

---

### Post by lovinglinux on 2009-10-09
Keep in mind that the current installation of Firefox 3.5 in Jaunty (i.e. Shiretoko) uses a different profile folder. Firefox uses ~/.mozila/firefox while Shiretoko uses ~/.mozilla/firefox-3.5. When you first launch Shiretoko, it copies your profiles from ~/.mozila/firefox to ~/.mozilla/firefox-3.5. This is safety measure to avoid messing with Firefox settings if you just want to test Shiretoko. Nevertheless, Firefox 3.5 in Karmic is the default browser, so it uses the ~/.mozila/firefox as all other default versions. 

Bottom line, when you install Karmic after using Shiretoko in Jaunty you will have to copy the profile folder contents back to ~/.mozila/firefox, if you want to preserve your bookmarks, passwords, extensions and settings, otherwise you go back to the profile state used before Shiretoko installation.

I bet when Karmic comes out, there will be a lot of users complaining about their bookmarks.

---

### Post by vallvi on 2009-10-10
"I bet when Karmic comes out, there will be a lot of users complaining about their bookmarks."

But not from those that have Xmarks installed :)
Now, that's a plugin that should be defaulted in Firefox! 
[http://www.xmarks.com/](http://www.xmarks.com/)

---

### Post by lovinglinux on 2009-10-10
> **vallvi said:**
> "I bet when Karmic comes out, there will be a lot of users complaining about their bookmarks."

But not from those that have Xmarks installed :)
Now, that's a plugin that should be defaulted in Firefox! 
[http://www.xmarks.com/](http://www.xmarks.com/)

Yep, it solves the bookmark issue, but not the rest. I was a fan of Foxmarks, but I haven't used it since they re-branded it as Xmarks and changed the way it works. Now the syncing feature makes Firefox crawl, due to heavy database access.

---

