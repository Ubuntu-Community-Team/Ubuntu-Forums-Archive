---
title: "Grub menu duplicate when kernal image updated..."
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Letterbomb05 on 2009-11-25
Hey there, I'm having a little trouble with Ubuntu 9.10. I installed a bunch of updates a few days ago and one of the updates was a new kernal image (I think that's the name for it, can't remember now! >_<). Anyway, my grub menu usually looks something along the lines of:

```

Ubuntu Linux Kernal 1.45 etc etc etc.... (or whatever)
"" Safe Mode
"" Mem Test
Windows XP

```

Anyway, when I get the update I have two new options at the top of the list. The list then looks something like:
```

Ubuntu Linux Kernal 1.55 etc etc etc.... (or whatever)
"" Safe Mode
Ubuntu Linux Kernal 1.45 etc etc etc.... (or whatever)
"" Safe Mode
"" Mem Test
Windows XP

```


The lists I've written there are purely to illustrate the problem at hand, the information isn't accurate, I couldn't remember what the list looks like exactly.

Anyway, as you can see this isn't a major problem that affects the system working in any way, it is slightly annoying though! Thanks in advance for any feedback, much appreciated!

- Aaron.

---

### Post by oldfred on 2009-11-25
It is not a duplicate because it gives you the choice of booting either the new or the old kernel. Sometimes a new kernel may not work for your configuration and it makes it easy to boot the old one.

I always kept two kernels shown in the menu of old grub and only occasionally housecleaned out old kernels in synaptic. They do not take up much space. I have not seen a way to limit showing a limited number of kernels, yet, for grub2 other than housecleaning.

---

