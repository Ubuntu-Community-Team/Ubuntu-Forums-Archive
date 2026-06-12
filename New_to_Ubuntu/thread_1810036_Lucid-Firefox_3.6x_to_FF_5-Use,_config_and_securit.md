---
title: "Lucid-Firefox 3.6x to FF 5-Use, config and security notes."
date: 2011-07-22
forum: New to Ubuntu
---

### Post by emarkay on 2011-07-22
Since it is obvious that in a few months we Lucid users will be forced into Firefox 5 or 6 or whatever it is then, I am asking those already migrated for assistance.

I had tested FF4 a while back and found it tolerable, but with no benefit to me at the time.  I was concerned with the "Services sync" addition as a potential security issue for poorly configured clients. But, since FF4 beta, what other issues have appeared that could impact users? 

IT people seem to be in a panic over this for their deployments, the "Rapid Release" issue, but since it's a fact, what needs to be done, changed, added or "about:config"d to False for maximum performance, security and stability? 

In otherwords, how to get any unessential dogs, ponies, bells and whistles disabled or removed, as would be required in a typical corporate environment - just as an Internet Browser, nothing more

---

### Post by Paddy Landau on 2011-07-22
I've converted to FF 5 and found no problems, with two exceptions.

[LIST=1]
[*]The [BBC News]("http://www.bbc.co.uk/news/") website sometimes has funny red lines on side comments.
[*]Google no longer supports Google Toolbar on Firefox. (There is a workaround for FF 5, but this is not guaranteed to always work.)
[/LIST]

---

### Post by lovinglinux on 2011-07-22
> **emarkay said:**
> Since it is obvious that in a few months we Lucid users will be forced into Firefox 5 or 6 or whatever it is then, I am asking those already migrated for assistance.

I had tested FF4 a while back and found it tolerable, but with no benefit to me at the time.  I was concerned with the "Services sync" addition as a potential security issue for poorly configured clients. But, since FF4 beta, what other issues have appeared that could impact users? 

IT people seem to be in a panic over this for their deployments, the "Rapid Release" issue, but since it's a fact, what needs to be done, changed, added or "about:config"d to False for maximum performance, security and stability? 

In otherwords, how to get any unessential dogs, ponies, bells and whistles disabled or removed, as would be required in a typical corporate environment - just as an Internet Browser, nothing more

There is nothing in terms of security that needs any different approach. Using [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/") is recommended as usual. Make sure to configure it to block flash as well or use [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/").

In terms of performance, Firefox 4, 5, 6, 7 and 8 [are a lot faster than 3.6]("http://picturepush.com/public/5939461"). However, you can read some optimization techniques in [my tutorials]("http://www.webgapps.org/tutorials/firefox/optimization").

The Sync feature is totally encrypted and disabled by default, so no need to worry about that.

The reason why corporate folks are freaking out is because of add-on compatibility, since many corporate environments use their own add-ons. You can learn how to deal with add-on in the [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

---

### Post by SpinningAround on 2011-07-22
To get hold of the latest stable firefox, can u use this ppa.
[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

If you are using an old computer might it be worth trying Chromium, I noticed that it's significantly faster then FF5.

---

### Post by mikewhatever on 2011-07-23
You can download the latest release of Firefox 3.6 and run it till the end of times. No one will ever bother forcing you to quit.
[ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/)

---

### Post by I2k4 on 2011-07-23
Not sure why anybody would be in love with FF 3.6 since it was unstable and slow in my experience both XP and Ubuntu.  I use a few extensions, notably NoScript, AdBlock Plus.  These are my about:config tweaks, which continue to work and seem to improve (no scientific validation) on the later FF versions:

network.http.pipelining - false to true
network.http.pipelining.maxrequests - 4 to 30
network.http.pipelining.ssl false to true
network.http.proxy.pipelining - false to true
network.http.max-connections 30 to 96
network.http.max-connections-per-server 15 to 32
network.http.max-persistent-connections-per-server 6 to 8
[new boolean] config.trim_on_minimize true (lower memory when minimized)
browser.sessionstore.interval from default 10000 ms (i.e. saves every 10 secs) to 500000
browser.sessionhistory.max_entries  from 50 to 5 
browser.sessionhistory.max_total_viewers  Value: 0
browser.urlbar.default.behavior from 0 to 49.
browser.search.suggest.enabled - from true to False
browser.sessionstore.max_tabs_undo from 10 to 3
browser.sessionstore.max_windows_undo 3 to 1
browser.cache.disk.capacity = 0 (runs FF in RAM only, best for Live USB)

---

