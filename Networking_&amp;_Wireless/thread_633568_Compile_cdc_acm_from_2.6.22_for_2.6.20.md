---
title: "Compile cdc_acm from 2.6.22 for 2.6.20"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by bismark on 2007-12-06
So I was able to compile the cdc_acm modules for 2.6.20-16-generic & 2.6.20-16-lowlatency from the 2.6.22 source.  I figured I'd share and post them here for other people if they need them.

**Original Question**
Okay I'm trying to use a Motorola Q as an EVDO modem.  It use to work before a system update on the phone with the cdc_acm module.  Unfortunately it does not now.

From my testing I've figured out that something changed between 2.6.20 and 2.6.22 in the cdc_acm and usb-serial modules that have fixed it. The question I have is how can I backport those changes to 2.6.20?  I don't want to upgrade to Gutsy (I have an ATI equipped laptop).

I did this once before and unfortunately like an idiot I didn't write the steps down.  Any help would be much appreciated.

---

