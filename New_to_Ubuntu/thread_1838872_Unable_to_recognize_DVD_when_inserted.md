---
title: "Unable to recognize DVD when inserted"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by mfkevinking on 2011-09-04
Hey all, I've been using Ubuntu since 10.04, but I'm still a 'green' user, :).

Here is my problem: I cannot get my DVD to play when I insert it into my DVD drive. The CD/DVD drive appears when I insert the DVD but no action is taking place. That is, the drive does not spin up or anything. I've been browsing the forums for awhile, but no immediate solutions have been relevant.

I installed:

libdvdcss

     Code: sudo /usr/share/doc/libdvdread4/install-css.sh

And: restricted/ugly/bad formats.

     Code: sudo aptitude install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly 

As this seemed to be a common solution when recognizing and playing a DVD, however I still cannot get it to work, :(. I also have VLC installed, so I don't know if it's still a codec issue.

What may I do to better facilitate help in fixing this problem? Thanks.

---

### Post by snip3r8 on 2011-09-04
Welcome to the forum green user...

First of all have you made sure that the DVD actually works in other devices?
My second question is ,have you installed ubuntu using wubi? if so then that may be the problem because ive experienced disc reading issues with wubi installed distos.

---

