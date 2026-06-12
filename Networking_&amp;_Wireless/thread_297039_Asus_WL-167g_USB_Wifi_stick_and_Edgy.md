---
title: "Asus WL-167g USB Wifi stick and Edgy"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by Herodotus on 2006-11-10
Hello all,

I have a fresh install of Edgy from the i386-desktop iso. My Asus WL-167g USB Wifi stick is not appearing in the Networking panel at all. I was under the impression that the drivers for this dongle were already installed this release... can someone point me to a howto for getting this up and running? should I switch to a different kernel first?

Thanks in advance for any help.

---

### Post by sebos69 on 2006-11-11
This stick works with the rt2570 module, but you have to build it yourself. The easiest thing to do is to use module-assistant

(sudo apt-get install module-assistant)

and install the rt2570 module sources from synaptic (the package is called rt2570)

I am shure there are howtos to build modules with module-assistant. Good luck :)

---

### Post by shaunbarlow on 2007-04-06
Hi all,
My ASUS wl-167g isn't showing up in the networking window.
I've followed the above steps and it's still not there.
Does anyone have a suggestion for getting the dongle going?
Thanks in advance for any help.
Cheers,
Shaun

---

