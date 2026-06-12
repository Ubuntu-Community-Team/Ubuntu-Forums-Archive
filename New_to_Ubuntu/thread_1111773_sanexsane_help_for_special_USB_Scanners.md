---
title: "sane/xsane help for special USB Scanners"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by not_email@comcast.net on 2009-03-31
All,

I have an HP Scanjet 5370C (quite old by now), that doesn't have Vista drivers, (for my lone Vista laptop).  All my systems run Linux variants.  I just solved the secret for making this work in Ubuntu (or other variants):

After reading the manual (RTFM), I found a simple first attempt that works.

1) Look up your particular scanner in the SANE support page and determine WHICH libsane-extra driver is used by the scanner that you have.

2) Comment out ALL but the driver you will need in the /etc/sane.d/dll.conf file, (in my case I needed the 'avision' driver).

That solved my system lockup problem.

It's all in the configuration file.

Robin

---

