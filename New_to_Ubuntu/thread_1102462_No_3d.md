---
title: "No 3d?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by eilios on 2009-03-21
I tried to run a world of goo demo, but it won't run. Neither will 3d windows and cube gears for compiz fusion. When I check my drivers it says there are none. What do I do? I have an Intel Graphics Media Accelerator 950. BTW: I installed, so it isn't a virtualbox issue like before.

---

### Post by eilios on 2009-03-21
Bump, could anybody help me?

---

### Post by Bölvaður on 2009-03-21
please do not bump your thread within ... well 22 hours.. though normally people say 24.

While you was bumping perhaps other people like me where or are looking for the solution.

A simple google search showed that intel has opensource drivers available for linux, and people are using this card in linux with no problems.
So that is a good news.



Does this help?
[URL="http://ubuntuforums.org/showthread.php?t=228517"]

http://ubuntuforums.org/showthread.php?t=228517[/URL]

---

### Post by eilios on 2009-03-21
> **Bölvaður said:**
> please do not bump your thread within ... well 22 hours.. though normally people say 24.

While you was bumping perhaps other people like me where or are looking for the solution.

A simple google search showed that intel has opensource drivers available for linux, and people are using this card in linux with no problems.
So that is a good news.



Does this help?
[URL="http://ubuntuforums.org/showthread.php?t=228517"]

http://ubuntuforums.org/showthread.php?t=228517[/URL]
I used the terminal command. Going to test it out now.

EDIT: Still crashes. :/

---

### Post by Bölvaður on 2009-03-21
can you copy and paste all what you did with all the errors?

*added*
btw did you do a hard restart?

---

### Post by eilios on 2009-03-21
> **Bölvaður said:**
> can you copy and paste all what you did with all the errors?
No errors, it crashes and goes straight back to login. When I try to add it back it says "xserver-xorg-video-intel is already the newest version."

---

### Post by Bölvaður on 2009-03-21
if you cannot get back into ubuntu you can go into recovery mode. find /etc/X11/xorg.conf
cd /etc/X11

remember to take backup before doing the change.
cp xorg.conf xorg.conf_backup


and change driver to vesa (instead of intel)
I think nano is default text editor so

nano xorg.conf

save and restart x .. well or just do a hard restart


*added*
when you got your x working again we can get back to setting up your driver.
Remove the package you just installed from the link.
Post what you wrote in the terminal (just to have everything in this thread for easier access later)

---

### Post by Art3mis on 2009-03-21
I had a similar problem, which I resolved by disabling compiz

---

### Post by eilios on 2009-03-21
> **Bölvaður said:**
> if you cannot get back into ubuntu you can go into recovery mode. find /etc/X11/xorg.conf
cd /etc/X11

remember to take backup before doing the change.
cp xorg.conf xorg.conf_backup


and change driver to vesa (instead of intel)
I think nano is default text editor so

nano xorg.conf

save and restart x .. well or just do a hard restart


*added*
when you got your x working again we can get back to setting up your driver.
Remove the package you just installed from the link.
Post what you wrote in the terminal (just to have everything in this thread for easier access later)
I don't see intel, I just get this.
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
Oh, and I typed this to get it.
sudo cp xorg.cong xorg.conf_backup

---

### Post by RomeReactor on 2009-03-21
Hi. Try going into grub, select "recovery mode", and then use XFIX.

---

### Post by SunnyRabbiera on 2009-03-21
Some video cards work better then others with compiz, mine has a good interaction despite being a older intel video card.

---

### Post by eilios on 2009-03-22
I used wubi, how should I do this?

---

### Post by eilios on 2009-03-22
Bump. Xfix does nothing.

---

### Post by eilios on 2009-03-22
Bump.

*sigh*

---

