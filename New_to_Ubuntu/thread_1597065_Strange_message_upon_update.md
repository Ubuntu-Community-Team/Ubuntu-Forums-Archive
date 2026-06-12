---
title: "Strange message upon update"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by Roger Gundberg on 2010-10-14
Hi all!
I have an issue that just popped up in Synaptic Packager. When I do a customarily update (morning and night) I get this argument as follows:

E: /var/cache/apt/archives/app-install-data-partner_12.10.10.3_all.deb: trying to overwrite '/usr/share/app-install/icons/skype.png', which is also in package app-install-data-medibuntu 0.2. These updates are important to me. How do I resolve this issue?

This is happening in Meercat. Really nice OS by the way. Good work!
Warmest Regards,
Roger Gundberg

---

### Post by matt_symes on 2010-10-15
Hi,

Your problem is the same file is defined in more one package. You can force the package manager to perform the overwrite.

Never had to do this myself, but the general technique is outlined here

[http://shreevatsa.wordpress.com/2006/04/16/dpkg-error-trying-to-overwrite-x-which-is-also-in-package-y/](http://shreevatsa.wordpress.com/2006/04/16/dpkg-error-trying-to-overwrite-x-which-is-also-in-package-y/).

The comments below seem to suggest this technique sorts it out. Please understand though, i had _never_ tried this myself.

Kind regards.

---

