---
title: "DVDrip - Am I missing something?"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by MadsRH on 2009-06-24
Hi
I'm trying to rip a DVD, but there's something wrong with the image and the audio.

It looks like this:
[ATTACH]118786[/ATTACH]

I've tried both dvd::rip and OGMrip, both of them gives me this result. 


Can anyone help?

---

### Post by Therion on 2009-06-24
Try this tutorial; you'll need K3b and K9 Copy but they're both in the repo's:

[http://www.dvd-guides.com/content/view/213/59/](http://www.dvd-guides.com/content/view/213/59/)

---

### Post by Hospadar on 2009-06-24
Do you have libdvdcss2 installed?
You'll need to get it from the medibuntu repositories (there are other places to get it, but medibuntu is by far the easiest and most streamlined)

libdvdcss2 is what decrypts css-encrypted (i.e. almost all commercial dvds) so you can make your fair-use backup copies.

[http://www.medibuntu.org/](http://www.medibuntu.org/)
Go to the "repository howto"
they run their own software repository, once you get it setup as per the instructions, you can install libdvdcss2 as a package with your favorite frontend (synaptic, apt-get, etc)

---

### Post by MadsRH on 2009-06-24
Thanks for the fast reply both of you :-)

I'll give **libdvdcss2** a try first. I seems to be available in *restricted-extras* from Synaptic.

---

### Post by HavocXphere on 2009-06-24
Broken codecs. Not sure how to fix that, but I'd try to reinstall the restricted packages.

---

### Post by MadsRH on 2009-06-24
libdvdcss2 didn't do the trick :(

---

