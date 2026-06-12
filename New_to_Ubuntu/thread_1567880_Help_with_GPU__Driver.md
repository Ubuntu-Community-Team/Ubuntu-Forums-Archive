---
title: "Help with GPU / Driver"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by ubunwhat on 2010-09-04
I felt like this deserved a new thread with a proper title as the issue became apparent in a thread about hard drives.  Anyway, here is my problem.  I have a fresh install on a new HDD that I cannot get to run properly.  I keep getting black screens and reboots and random times.  After much discussion of hard drives, boot cds etc someone suggested it could be my video card.  I am running the Intel GMA 950, and no it is not upgradable on this machine.  After a bit of googling it seems that this chipset in particular causes problems with Ubuntu.   However, most of the posts I found on the issue were several years old.  I guess I am hoping that in the last few years someone has found a fix, or a better driver, or anything at all that might allow me to run Ubuntu on this machine.

---

### Post by sandyd on 2010-09-04
> **ubunwhat said:**
> I felt like this deserved a new thread with a proper title as the issue became apparent in a thread about hard drives.  Anyway, here is my problem.  I have a fresh install on a new HDD that I cannot get to run properly.  I keep getting black screens and reboots and random times.  After much discussion of hard drives, boot cds etc someone suggested it could be my video card.  I am running the Intel GMA 950, and no it is not upgradable on this machine.  After a bit of googling it seems that this chipset in particular causes problems with Ubuntu.   However, most of the posts I found on the issue were several years old.  I guess I am hoping that in the last few years someone has found a fix, or a better driver, or anything at all that might allow me to run Ubuntu on this machine.
press ESC during the computer bootup to display the grub menu.
use up/down arrow keys to select ubuntu (the first one)
press 'e'
at the end of the "kernel" line (not the initrid line), add (with a space in between)
```

nomodeset

```

---

### Post by ubunwhat on 2010-09-04
I know I seem remedial, but can you tell me what this will do?

---

### Post by ubunwhat on 2010-09-04
Ok, don't care what it did.  The bottom line is that it worked.  The real question is this... do I need to do it every time I boot?  Is there a way to make that change permanent?

---

### Post by sandyd on 2010-09-04
> **ubunwhat said:**
> Ok, don't care what it did.  The bottom line is that it worked.  The real question is this... do I need to do it every time I boot?  Is there a way to make that change permanent?
```

sudo nano /etc/default/grub

```add
```

nomodeset
```to the GRUB_CMDLINE_LINUX section (between the quotes, if there is already something there, make sure theirs a space in between)
save and run
```

sudo update-grub
```

---

### Post by ubunwhat on 2010-09-04
Thank you, but I have to point out that I am a total newb.  As in my first exposure to Linux was yesterday.  Would I be typing those things in the terminal once Ubuntu is loaded?  I really am kinda lost.  Also, not sure that it worked.  The nomodeset worked the first time but I shut the machine down and now I am having the same old problem of not being able to boot rather I insert nomodeset or not.  It's a very uncomfortable feeling not knowing whether my laptop is just screwing with me or if I need to be wearing a crash helmet as I walk down the street to avoid injuring myself.  I'm hoping it's the former but right now I'm feeling like it's the latter.

---

### Post by sandyd on 2010-09-04
> **ubunwhat said:**
> Thank you, but I have to point out that I am a total newb.  As in my first exposure to Linux was yesterday.  Would I be typing those things in the terminal once Ubuntu is loaded?  I really am kinda lost.  Also, not sure that it worked.  The nomodeset worked the first time but I shut the machine down and now I am having the same old problem of not being able to boot rather I insert nomodeset or not.  It's a very uncomfortable feeling not knowing whether my laptop is just screwing with me or if I need to be wearing a crash helmet as I walk down the street to avoid injuring myself.  I'm hoping it's the former but right now I'm feeling like it's the latter.
You run the commands after ubuntu starts.

---

