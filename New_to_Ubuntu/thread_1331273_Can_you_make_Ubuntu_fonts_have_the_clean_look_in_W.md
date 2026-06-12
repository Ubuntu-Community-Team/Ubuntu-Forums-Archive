---
title: "Can you make Ubuntu fonts have the clean look in Windows of Mac OS X?"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by ovimunt on 2009-11-19
Hi,

I've asked this question in the past and I've tried a few different methods but never managed to get Ubuntu fonts to look nice and clean like they do in Windows or even Mac OS X for that matter.

The one thing I particularly don't like the look of, is Firefox. For some reason, in Firefox the fonts look even worse then they do overall in Ubuntu. 

I know a while back there was a way to get the foonts look similar to Windows but it seems that in Ubuntu 9.10 what this does is only to set the MS fonts as defaults and change the fonts display to monochrome, which is obviously not quite like Windows. 

If anyone out there has got a solution for this, please let me know. In any case, I would still really appreciate it if someone could at least tell me how to get Firefox to look better...

Thanks

---

### Post by ukripper on 2009-11-19
Install ms fonts by running this command:
```
**sudo apt-get install msttcorefonts**
```

More fonts: try this website [http://embraceubuntu.com/2007/05/21/300-easily-installed-free-fonts-for-ubuntu/](http://embraceubuntu.com/2007/05/21/300-easily-installed-free-fonts-for-ubuntu/)


.

---

### Post by ovimunt on 2009-11-19
I have installed all Microsoft fonts by importing them directly from my Windows installation on another partition. But this is not it, even if I change the defaults to the Microsoft fonts they will simply not look like they do in Windows.

I'll try to attach a screen shot to show what I mean.

---

### Post by ukripper on 2009-11-19
> **ovimunt said:**
> I have installed all Microsoft fonts by importing them directly from my Windows installation on another partition. But this is not it, even if I change the defaults to the Microsoft fonts they will simply not look like they do in Windows.

I'll try to attach a screen shot to show what I mean.

Can you get rid of those fonts and try msttcorefonts from ubuntu repos?

---

### Post by ovimunt on 2009-11-19
I actually did try that first but I didn't get the results I expected so that's why I decided to import them from Windows...

---

### Post by ukripper on 2009-11-19
have you tried setting rendering within fonts tab to "subpixel smoothing"?

---

### Post by 3rdalbum on 2009-11-19
It's not actually "clear" fonts, it's fuzzy fonts. By default, in Ubuntu 9.10 this is already set up for you. It's the "subpixel smoothing" option in the Appearance program.

If you have imported your /home from an older version of Ubuntu or have dist-upgraded, then this won't be set unless you set it a while ago.

---

### Post by ovimunt on 2009-11-19
[**This is the old thread**]("http://ubuntuforums.org/showthread.php?t=208396") I was talking about and which gives mixed results...

---

