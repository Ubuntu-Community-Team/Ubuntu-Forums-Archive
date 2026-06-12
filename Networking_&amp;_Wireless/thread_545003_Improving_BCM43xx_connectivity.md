---
title: "Improving BCM43xx connectivity"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by Page on 2007-09-07
I have one of those wretched Broadcom 43xx wireless chips in my Ubuntu laptop, and I eventually managed to get it working by using the bcm43xx-fwcutter package to extract the firmware binary blob from the bcmwl5.sys windows driver. 
 
 Because of this, my wifi works on Linux (kind of) but my connection success varies greatly. I can reliably connect to  my own home wireless router anywhere in its range without problems, but at my university, I literally have to be right on top of a hot spot to get a good connection (or even connect at all). However, I can snag distant networks with WinXP.
 
 I was wondering if there was a way I could make my wireless more sensitive to the network when I'm further away from a hot spot or if there is anything at all I could do to solve my problem.

---

### Post by Page on 2007-09-07
anyone?

---

### Post by Breathe on 2007-09-07
Well, yes, i think there is a way...

I would suggest you to uninstall your firmware and try with this other one... I've been working  with it for the last few months and i am really happy with its stability.

Hope that i can help you :D

[http://mural.uv.es/alacer/wl_apsta.o]("http://mural.uv.es/alacer/wl_apsta.o")

You install it the same way (If you saved the file to  ~)

> $ sudo apt-get install bcm43xx-fwcutter (You've already done this)
$ sudo bcm43xx-fwcutter -w /lib/firmware/'uname -r'  ~/wl_apsta.o

---

