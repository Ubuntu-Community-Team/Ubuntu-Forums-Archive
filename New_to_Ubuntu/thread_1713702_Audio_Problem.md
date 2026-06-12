---
title: "Audio Problem"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by zhengbin on 2011-03-24
I was trying to record sound on my computer using my speaker phone under Ubuntu, and nothing was recorded; I switched to Windows 7, and it worked fine.I ran the testing program in Ubuntu, and nothing was recorded. Can I safely say that there is some configuration I need to do in order for the speaker phone to work?

---

### Post by stoogiebuncho on 2011-03-25
How does your speaker phone connect to your computer?  Is it through a usb port, or an audio jack?

Try clicking on the volume icon in your taskbar, and going to the Sound Properties.  There should be an "input" tab there.  See if you can find your speaker phone on the list of input options, and then make sure it is enabled, and not muted, and that the volume is turned up.

---

### Post by Arijit_Kundu on 2011-03-25
open a terminal (applications>accessories>terminal) and run:

sudo apt-get install alsamixer

when it'll over, run in the terminal

alsamixer

now volume up all capture/mic options. Press tab to go to next page. When it is done, press escape to finish. Try to record after that.

---

