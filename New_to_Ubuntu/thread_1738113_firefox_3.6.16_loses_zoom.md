---
title: "firefox 3.6.16 loses zoom"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by DarinB on 2011-04-24
I have vision problems and firefox 3.6.16 does not remember zoom.
All previous versions once I zoomed with ctl + it would stay for every website and each time I opened firefox from scratch. 
Any help on this? Is it a history problem?

---

### Post by Frogs Hair on 2011-04-24
I'm using the Nightly build of FF 6 Alpha 1 and it does not store zoom settings from one site to another. My opera browser does , both browsers are set to never remember history. Changing history settings in Firefox makes no difference.

---

### Post by DarinB on 2011-04-24
I changed my history setting to save history but it still loses its zoom. 
these are my history settings. [ATTACH]189912[/ATTACH]

---

### Post by Irony on 2011-04-24
In the address bar type;

```
about:config
```

and set;

```
browser.zoom.siteSpecific
```

to

```
false
```

---

### Post by ub-newbie on 2011-04-24
This might be to simple, but I use the "NoSquint" add on to FF when browsing on my 47in TV.

---

### Post by DarinB on 2011-04-25
the about config above helped if I don't close firefox. 
once i reopen it is back to micro again. 
I don't know what I changed but it has become very difficult to browse. 
any ideas?

---

### Post by wolfen69 on 2011-04-25
Rename your ~/.mozilla file (to .mozilla2 or something) and open firefox. A new config file will be made and you can try to see if you can get it working again.

---

### Post by DarinB on 2011-04-25
I was thinking of recreating the .mozilla folder, but the nosquint works perfectly as good as new. 
I hate the idea of having to reenter all of my passwords again. 
so for now I am happy. 
thank you ub newbie

---

### Post by lovinglinux on 2011-04-25
> **DarinB said:**
> I was thinking of recreating the .mozilla folder, but the nosquint works perfectly as good as new. 
I hate the idea of having to reenter all of my passwords again. 
so for now I am happy. 
thank you ub newbie

Recreating the mozilla folder is kind of extreme. I would simply delete the *prefs.js* file first or start Firefox in safe mode. It could be an extension causing the problem.

See [http://www.webgapps.org/firefox/general-troubleshooting](http://www.webgapps.org/firefox/general-troubleshooting)

BTW, if you ever need to delete your profile, you can export your passwords using [Password Exporter]("https://addons.mozilla.org/en-US/firefox/addon/2848/") extension, you can Sync them using [Firefox Sync]("https://addons.mozilla.org/en-US/firefox/addon/firefox-sync/") (Firefox 4 has this built-in) or you can simply copy *signons.sqlite* and *key3.db* files from your old profile.

See [http://www.webgapps.org/firefox/fixing-corrupted-profiles](http://www.webgapps.org/firefox/fixing-corrupted-profiles)

---

