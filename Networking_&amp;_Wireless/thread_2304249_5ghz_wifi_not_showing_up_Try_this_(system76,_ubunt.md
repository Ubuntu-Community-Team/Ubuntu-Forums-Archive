---
title: "5ghz wifi not showing up? Try this (system76, ubuntu 15.04)"
date: 2015-11-25
forum: Networking &amp; Wireless
---

### Post by ManiacDan on 2015-11-25
Hey all, I got this answer already from system76 tech support but I wanted to (a) share it with the community for those intrepid googlers and (b) post a positive s76 story since the horror stories nearly drove me away and I'm glad now that I didn't.

Anyway, the problem:
**symptoms:**  I have a wirelessAC (5ghz) card in my laptop but I was not seeing 5ghz networks.  The network was working fine (verified with multiple other devices).  

**Solution:**  At the bottom of file `/etc/default/crda` is a variable called REGDOMAIN.  On my system, for some reason, it was blank.  Changing 'REGDOMAIN=' to 'REGDOMAIN=US' and rebooting immediately solved my issue.

**mini review:**  I can't help but crow a bit about my System76 Gazelle.  It had every feature that I wanted (and at least one that I didn't even think of putting on my requirements list) and the only thing I'm disappointed in at all is the keyboard.  It's a bit unresponsive despite me smacking the hell out of the keys, and it's not lit in any way.  I didn't think they still made not-backlit keyboards, I've had one in my last 6-7 machines.  I can tough-type, obviously, but the navy-blue-on-black that must manufacturers use for their function key designations isn't exactly easy to see in low light.  Other than "I didn't think to check for a backlight" and "the keyboard is alright but not great" the rest of the machine gets a 10/10.

---

### Post by chili555 on 2015-11-25
Excellent recommendation.

Of course, all you searchers, substitute your country code, if not US. Find it here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

---

