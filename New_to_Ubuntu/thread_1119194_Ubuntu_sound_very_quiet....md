---
title: "Ubuntu sound very quiet..."
date: 2009-04-07
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-07
the sound is very quite on my Ubuntu install if I turn everything up full volume including my speakers I get just enough sound to be able to hear what people are saying on a video....

I've checked that everything is turned up and I have also tried 'alsamixer' and that appears to be fine;)

thanks in advance!

PS: I'm using the built in sound on my motherboard (see sig...)

---

### Post by fooman on 2009-04-07
is the PCM slider turned up in alsamixer?

---

### Post by skymera on 2009-04-07
Type alsamixer into the terminal.

Nudge the sliders higher, i have mine maxed :)

---

### Post by kamitsukai on 2009-04-07
Sorry should of mentioned before but I'm using 8.10 so there's only one slider on alsamixer which is on full... :(

---

### Post by albinootje on 2009-04-07
> **kamitsukai said:**
> Sorry should of mentioned before but I'm using 8.10 so there's only one slider on alsamixer which is on full... :(

There's a sound troubleshooting howto on this forum :
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

And please post the output of your :
```

lspci

```

---

### Post by fooman on 2009-04-08
> **kamitsukai said:**
> Sorry should of mentioned before but I'm using 8.10 so there's only one slider on alsamixer which is on full... :(

install the gnome-alsamixer from synaptic (system > administration > synaptic package manager...search for "gnome-alsamixer").

or just open a terminal (applications > accessories > terminal) and type or copy/paste:

```
sudo apt-get install gnome-alsamixer
```

after it installs,  find it in applications > sound & video.

...check all the sliders there are turned up.

---

### Post by PriceChild on 2009-04-08
*edits title*

---

### Post by kamitsukai on 2009-04-08
> **fooman said:**
> install the gnome-alsamixer from synaptic (system > administration > synaptic package manager...search for "gnome-alsamixer").

or just open a terminal (applications > accessories > terminal) and type or copy/paste:

```
sudo apt-get install gnome-alsamixer
```

after it installs,  find it in applications > sound & video.

...check all the sliders there are turned up.

Brilliant! the one labeled master f was all but muted...

> **PriceChild said:**
> *edits title*

Thanks;)

---

### Post by wbee on 2009-04-08
kamitsukai,

Please forgive the intrusion,but I saw your computer description in your original post.

Are you running 32 or 64?

Does your computer recognize all four gigs of your memory?

Does your board "crossfire" and if so,does it do so with Ubuntu?

It probably has nothing to do with your sound,but I'm considering a similar board and I'm curious.

------------

Thank you

---

### Post by kamitsukai on 2009-04-08
> **wbee said:**
> kamitsukai,

Please forgive the intrusion,but I saw your computer description in your original post.

Are you running 32 or 64?

Does your computer recognize all four gigs of your memory?

Does your board "crossfire" and if so,does it do so with Ubuntu?

It probably has nothing to do with your sound,but I'm considering a similar board and I'm curious.

------------

Thank you


I'm running Ubuntu 64 and it recognises all 4 gigs I'm not sure about crossfire but I think it does the Nvidia equivalent (Scalable Link Interface?)

---

