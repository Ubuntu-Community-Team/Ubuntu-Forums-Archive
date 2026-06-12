---
title: "Missing items from desktop"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by Roger49 on 2011-09-03
Evening all,
Everything was going so well with my 10.10 installation, then I had problems with a couple of Gnome applets, which I chose to delete - bad move!
Now my Mobile Broadband has vanished (posting this from Windows) and I only have the date displaying in the top right of my screen.
Any suggestions?
I have a feeling I may have to back up all my data to removable media and reinstall - may as well go for 11.04, although I may be a bit undergunned on a P4 with half a gig of memory!
Looking forward to any constructive comments.
TTFN
Roger49

---

### Post by Leshrac on 2011-09-03
If I understand you well, what happens is that you have deleted your applets from the bar and don't know how to add them back.

The easiest way to restore your bars to the default configuration would be writing something like this into a terminal:

gconftool-2 --recursive-unset /apps/panel

And then:

pkill gnome-panel

This should reset your configuration and bring back everything to the default configuration.

---

### Post by Frogs Hair on 2011-09-03
Here is a variation of the above command if it that doesn't work for some reason .```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

---

### Post by Roger49 on 2011-09-04
Thanks Gents,
I'll just kill off this live cd session and give it a go!
Regards,
Roger49

---

### Post by Roger49 on 2011-09-04
Thanks Gents,
The single line command from Frogs Hair did the job.
The missing symbols reappeared as if by magic!
Thanks again,
Best Regards,
Roger49:P

---

### Post by zanaz on 2011-09-08
How do you fix the same problem in a Natty installation? That command does not work for me. I get the output: gnome-panel: no process found.

---

### Post by Roger49 on 2011-09-19
Hi,
I think I've found the reason for my problems with the gnome applets (which has been ongoing).
I'm running 10.10 from a usb hard disk. As I understand it, the rate of data transfer is too low, and the applets are timing out. I plan to reinstall on an internal SATA drive and will update in due course.
rgds
Roger49

---

