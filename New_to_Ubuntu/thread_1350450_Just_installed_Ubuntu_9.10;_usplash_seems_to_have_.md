---
title: "Just installed Ubuntu 9.10; usplash seems to have a problem &amp; I can't log in"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by rainjam on 2009-12-09
Just installed Ubuntu 9.10 on my wife's laptop, as Windows XP had got bogged down with crap, and I thought I'd give Ubuntu a try rather than try to wipe everything and reinstall Windows. It's on its own partition - the computer is a Dell Latitude D620 laptop, 2GB RAM, dual core thingy.

It ran fine directly from the CD and during installation, but now it's installed I can't log in. I get a login prompt which flickers and flashes, and only seems to recognise about one keypress in every 4 or 5, so as I can't tell how many characters it thinks I've typed into the password field it keeps rejecting me. At the top of the screen is the message

usplash: Setting mode 1152 x 864 failed
usplash: Using mode 1024 x 768

I don't know if it's a graphics issue. The card is an Nvidia 1600M I think, and ran fine at 1440 x 900 under Windows.

---

### Post by rainjam on 2009-12-09
BTW I've tried booting from CD, but this didn't work for me - it sounds like it's loading, but eventually just deposits me at the flashing usplash login screen again.

---

### Post by rainjam on 2009-12-09
OK - so I tried the "repair" option and downloaded an update (2.6.31-16-generic now, rather than -14). Problem seems to be that nvidia drivers weren't installed, but at least this time it realised that was what was wrong. A bit of googling and I've worked out how to add the right drivers. So it seems all is ok in the land of ubuntu...

(Apologies if me replying to myself has wasted anybody's time, but a couple of hours ago this didn't seem so obvious...)

---

