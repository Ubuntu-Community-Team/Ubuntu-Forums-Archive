---
title: "No WPA using 7.04 CD"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by HerbOxley on 2007-07-25
I recently gave the Ubuntu 7.04 Live CD a try.
While it detected my Linksys WMP54G ver 4.0 wireless adapter
I wasn't able to get WPA to work.
Browsing reated WPA threads it seems to use WPA with the current version of Ubuntu you need to configure " wpa_supplicant".
How can this be done when you boot from a CD?

thanks, Herb

---

### Post by kevdog on 2007-07-25
Im not sure if it can be done.  You could tell me if this works.  What you need to do (with an internet connection -- obviously from a non-WPA network) is to type at command line:

sudo aptitude install wpasupplicant

If you can do this, then we can try to configure the interface.

---

### Post by lollipopsichord on 2007-08-03
I have the same problem. I'm a noob to ubuntu (though I have a basic understanding of linux, but still new) and I'm having a hell of a time trying to get wpa for my wireles. I've got the same card.

---

