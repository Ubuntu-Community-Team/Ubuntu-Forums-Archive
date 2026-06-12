---
title: "Docky gone"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by ersatzorama on 2009-05-24
After my upgrade to Jaunty Jackalope (which went fine by the way) I have a strange problem with Gnome-Do's Docky. 

On startup the first search screen appears (and can be used) but after that the real dock does not appear. Through Alt+F2 I can start Gnome-Do again, which will give me the first search screen, but again, it won't turn to the real dock. It doesn't show up in running processes in the System Monitor either. 

I've tried rebooting and reinstalling Gnome-Do, but none helps. Any ideas? I miss my dock! 

Thanks in advance!

---

### Post by Spiritous on 2009-05-24
Try in a terminal:

```
sudo gnome-do &
```

If that doesn't work try downgrading to a stable version):P

---

### Post by kiridude on 2009-05-24
I use another dock, and had a similar experience after upgrading to 9.04. I rectified it by not selecting openGL at startup. As my machine is a couple of years older, my graphics card could not cope.

---

### Post by ersatzorama on 2009-05-24
Thanks! The "sudo gnome-do &" works.. I'm busy with too much stuff to see what it does when I reboot, I'll check that later.. 

I'll also google with the & function actually does. :) May come in handy later!

---

