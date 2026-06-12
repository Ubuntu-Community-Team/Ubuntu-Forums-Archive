---
title: "bad window redraw rates with default/propriety drivers"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by yandos on 2009-03-31
Hi All

I'm using 8.10 with a Nvidia 128MB card, haven't tweaked with the standard build apart from installing the propriety Nvidia drivers - runnign from a 1920x1200 res monitor.

I'm not sure if theres something else I have to tweak, but the redraw rate when alt tabbing, moving windows, even scrolling a page is god-awful.

I've tried with nvidia 177 drivers, then reset the xorg.conf to use the default drivers but still no dice. To give you an example of the lag i'm getting the firefox 'do you want to remember this password' that appears at the top of browser windows after submitting a form takes 2-3 seconds to appear :(

Any help or point in the right direction appreciated!

---

### Post by LowSky on 2009-03-31
if your using 8.10 go to synaptic and search for *nvidia 180* its the newest driver. I think you need backports turned in in your Sources to use the 180 driver

---

### Post by RetchingRabbit on 2009-03-31
Seems like it might just be relevant to mention the exact card you have, since nvidia has several different drivers, and the newest one is not always the answer...

If you don't know this already, ```
lspci | grep -i vga
``` should tell us what you need us to know.

---

