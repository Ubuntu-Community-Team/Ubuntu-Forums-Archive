---
title: "n00b q's, flash crash and f-stop"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by PalMD on 2010-05-28
Recently installed Ubuntu.

1) flashplayer keeps crashing in chrome, and crashes firefox

2) Imported my photos, but the import folder is different from the one f-stop reads from.  When i tried to move them, it started copying them instead.  Any ideas?

---

### Post by cariboo on 2010-05-28
> **PalMD said:**
> Recently installed Ubuntu.

1) flashplayer keeps crashing in chrome, and crashes firefox

What version are you using, 32-bit or 64-bit? How did you install flash?

> 2) Imported my photos, but the import folder is different from the one f-stop reads from.  When i tried to move them, it started copying them instead.  Any ideas?

F-spot copies all your photos to ~/Photos, I don't use it any more, because I found it to annoying. If you are using Lucid (10.04) I would suggest giving shotwell a try, it is in the repositories.

---

### Post by PalMD on 2010-05-28
64bit, i unfortunately cannot remember how i installed it...followed instructions from somewhere.


any idea how to get f-stop to recognize all photos without copying them and eating up tons of memory?  or should i just try one of these other apps?

---

### Post by lovinglinux on 2010-05-28
> **PalMD said:**
> 64bit, i unfortunately cannot remember how i installed it...followed instructions from somewhere.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you have the package libmoon installed, then remove it. It has been causing Firefox crashes on several users machines.

---

### Post by BandD on 2010-05-29
I'm not exactly sure what you mean when you say "When i tried to move them, it started copying them instead."  

If you want you can set f-spot to use any folder as the default import folder (i.e. where f-spot saves the photos to).  Just open f-spot and go to Edit --> Prefences.  Then when the dialog box pops up, the first option will let you browse to any folder in your filesystem.

Alternatively, if you just want to import photos without f-spot makeing a copy of them to your "Photos" folder (the folder you set it to in the previous paragraph) then when you go to File --> Import and see the dialog box make sure you un-check the option that says "Copy fiels the Photos folder".

I hope that answers your question!

---

