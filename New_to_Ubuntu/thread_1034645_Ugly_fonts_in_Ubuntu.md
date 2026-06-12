---
title: "Ugly fonts in Ubuntu"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by Onoskelis on 2009-01-08
Hello.

Ubuntu is the first Linux distro that I have tried, and I find it to be decent enough for word processing and other casual things.

My main problem is the fonts in Ubuntu. I turned on subpixel rendering, and put it on full hinting, but the fonts still look awful and blurry. 

Is there any way to fix this? Or is this just the way fonts are supposed to look in Ubuntu?

---

### Post by iaculallad on 2009-01-08
Hi and Welcome to Ubuntu.
You could try this guide on [how to smoothen your fonts in Ubuntu]("http://www.goitexpert.com/entry.cfm?entry=Enable-Smooth-Fonts-in-UBUNTU-Linux").
HTH.

---

### Post by Onoskelis on 2009-01-08
> **iaculallad said:**
> Hi and Welcome to Ubuntu.
You could try this guide on [how to smoothen your fonts in Ubuntu]("http://www.goitexpert.com/entry.cfm?entry=Enable-Smooth-Fonts-in-UBUNTU-Linux").
HTH.

Didn't work too well. It seems like it just did the same thing as subpixel font rendering, which still looks bad.

---

### Post by iaculallad on 2009-01-08
> **Onoskelis said:**
> Didn't work too well. It seems like it just did the same thing as subpixel font rendering, which still looks bad.

Try adjusting your screen's refresh rate, that could be another factor.

---

### Post by Onoskelis on 2009-01-08
> **iaculallad said:**
> Try adjusting your screen's refresh rate, that could be another factor.

The refresh rate is fine. My settings currently are 60Hz refresh rate, and a resolution of 1680 x 1050.

---

### Post by syga on 2009-01-09
Check out this website for sharp fonts, like in Windows:

[http://www.sharpfonts.com/](http://www.sharpfonts.com/)

---

### Post by Onoskelis on 2009-01-09
> **syga said:**
> Check out this website for sharp fonts, like in Windows:

[http://www.sharpfonts.com/](http://www.sharpfonts.com/)


Thanks, these fonts look perfect.

Although I'm confused on how to install them. It says I need to compile freetype2 and do some other weird stuff that I don't understand. I'm new to Linux :popcorn:

---

### Post by hivelocitydd on 2009-01-09
I think you can find the answer for this on the following link

[http://ubuntuforums.org/showthread.php?t=151692](http://ubuntuforums.org/showthread.php?t=151692)

---

### Post by albinootje on 2009-01-09
> **Onoskelis said:**
> Thanks, these fonts look perfect.


You can install those Microsoft fonts in Ubuntu like this :
```

sudo apt-get install msttcorefonts

```

(Those fonts have a restricted license but are free to use.
MS stopped putting them online, but Sourceforge has them still.)

Not so long ago RedHat came with the Liberation fonts, which aim to replace these fonts.
```

sudo apt-get install ttf-liberation

```
If you prefer to use Synaptic Package Manager, then use those two package names in Synaptic to install them.

---

### Post by Onoskelis on 2009-01-09
Okay I figured it out. Thanks guys.

---

