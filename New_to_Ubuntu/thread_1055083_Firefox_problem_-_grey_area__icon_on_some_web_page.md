---
title: "Firefox problem - grey area / icon on some web pages"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by F W Adams on 2009-01-30
Using hardy 8.04
Firefox 3.0.5

Many pages are fine but many areas of web pages where a video should start, or flash, or other update is expected there is a rectangular area of various shades of grey. In every case where the error occurs there is a grey icon, two concentric circles with a triangle inside, If I click on these grey icons where a video should be the videos will start to play with sound for a few seconds and stop, Other grey areas tend to display properly after clicking.

I've tried lots of solutions / installs elsewhere but none worked.
I've tried deleting .mozilla with no result except the obvious, but no change to the error.
I've tried "apt-get remove firefox" followed by "apt-get install firefox" which changed nothing.

---

### Post by avtolle on 2009-01-30
Is Gnash installed? This could be a part of your problem. In the browser bar, type "about:plugins" without the quotation marks, of course, and see what comes up for flash.

Edit: that is "about: plugins" (without the quotation marks and the space after the colon).

---

### Post by F W Adams on 2009-01-30
Thanks for replying. Your suggestion returned about 120 plugins. I searched the screen for "nas", and it returned nothing so I think Gnash is not there.

---

### Post by F W Adams on 2009-01-31
ok, I've got a bit further, found this
[http://support.mozilla.com/en-US/kb/Troubleshooting+plugins](http://support.mozilla.com/en-US/kb/Troubleshooting+plugins)
certainly a good place to start with plugin problems

I stopped the grey problem by disabling "Shockwave Flash 9.0" in Firefox.
Now ( on another web page that just hung up before ) I get a message "Flash Plugin Not Detected", perhaps not unexpected. It redirects me to load "Adobe Flash Plugin 10". There is an 8.04+ version shown. This I already had loaded. If I re-install it makes no difference. Firefox doesn't seem to know it's there. How do I fix this?

---

### Post by F W Adams on 2009-01-31
Took about 3 hours to update from flash 9 to flash 10. Most of that time trying methods that didn't work. The problem seems to be removing flash 9 plugin from Firefox. When you start Firefox the fact that there is no nonfree[9] program on the machine and there is a version 10 isn't enough to remove the flash 9 plugin from Firefox. This seems to apply however you load flash 10, whether Firefox is running at the time or not, and whether the old nonfree program is there or not, or whether the plugin is disabled or not. Restarting firefox after renaming (mv) libswfdecmozilla.so finally removed it for me. Sorry these instructions are a bit rough and perhaps incomplete ( I'm tired ) but concentrate on removing the old flash 9 plugin and make sure it's really gone before wasting time on anything else.

This at least fixed it for me, all the solutions on the web seem only to work for a proportion of users and not everyone. This may be the same.

---

