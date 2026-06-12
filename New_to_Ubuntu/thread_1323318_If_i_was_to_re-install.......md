---
title: "If i was to re-install......"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-11-11
....would i be able to just copy over all my packages that i have installed so that i wouldnt have to download over 20gb of stuff again??

---

### Post by zkriesse on 2009-11-11
Meaning what exactly? Install over previous information? If that is your question then yes.

---

### Post by JamesParnell on 2009-11-11
if i was to make a fresh install of 9.10, because my brightness Fn's dont wanna work -_-.

What would i have to do to make sure i dont loose anything? would installing on another partition be the best way? then just copy and paste it over?

---

### Post by JugglinPhil on 2009-11-11
If you mean installed software then I think no, it'll be lost if you reinstall..

---

### Post by lavinog on 2009-11-11
if your current install is on a single partition, then yes, you should make another partition and install to that.
I don't know how grub will be installed though, and make sure that you keep track of the partitions, because it can be easy to install onto the wrong one and loose everything.

Your best approach would be to backup your home folder to another disk.

If you are concerned about downloading updates, you can copy all the packages from /var/cache/apt from the old install to the same folder on the new install.

---

### Post by durand on 2009-11-11
There is an option on the install cd to not install grub (the bootloader) so that shouldn't be a problem.

---

### Post by lavinog on 2009-11-11
> **durand said:**
> There is an option on the install cd to not install grub (the bootloader) so that shouldn't be a problem.

yes, but if the OP leaves grub installed on the old partition, then later removes the old partition, he will have to reinstall grub.

---

### Post by JamesParnell on 2009-11-11
if only i knew what was causing my brightness keys to stop working, i could sort it -_-. and i wouldnt want to reload 9.10 at all.

---

### Post by JBAlaska on 2009-11-11
I can almost guarantee that re-installing 9.10 will NOT get your Fn keys working. Try posting your system specs here or in the Google window -appended with "Ubuntu 9.10" and try that approach.

---

### Post by durand on 2009-11-11
> **JamesParnell said:**
> if only i knew what was causing my brightness keys to stop working, i could sort it -_-. and i wouldnt want to reload 9.10 at all.

Have you tried configuring your brightness keys in System > Preferences > Keyboard Shortcuts? If I remember correctly, there is an option to do that there.

---

### Post by JamesParnell on 2009-11-11
the thing is they were working earlier on today, i installed a load of new packs, i cant remember which ones, and then my brightness ones failed to respond, all the others work fine.. i hope this can shine some light on the situation, and i dunno how to hide it or upload it, as its saved as a html doc..

---

### Post by durand on 2009-11-11
If you're desperate, you could temporarily use the brightness applet on your panel. Right click on your panel, Add to panel, search for brightness.

---

### Post by JamesParnell on 2009-11-11
> **durand said:**
> Have you tried configuring your brightness keys in System > Preferences > Keyboard Shortcuts? If I remember correctly, there is an option to do that there.
Yeah ive checked there, all i see is volume up/down, i swear brightness used tobe there also, but im not quite sure

---

### Post by JamesParnell on 2009-11-11
> **durand said:**
> If you're desperate, you could temporarily use the brightness applet on your panel. Right click on your panel, Add to panel, search for brightness.
LOL, ive tried that also, i get "cannot get laptop panel brightness"

---

### Post by durand on 2009-11-11
Hmm, that looks like a driver problem, possibly with your graphics driver but I'm out of depth in this area.

---

### Post by lavinog on 2009-11-11
Is it not under power management?

---

### Post by JamesParnell on 2009-11-11
nope, i cant think what i would have done, but i nkow that it wasnt in power management either

---

### Post by raysfan81 on 2009-11-11
You would need to reinstall all programs after reinstalling Ubuntu.  Brightness settings should be under power management if i remember correctly.... Though i only have one laptop running Ubuntu.

---

### Post by JugglinPhil on 2009-11-12
> **JamesParnell said:**
> if only i knew what was causing my brightness keys to stop working, i could sort it -_-. and i wouldnt want to reload 9.10 at all.
Now that you come to mention it, mine ain't working either.. Haven't realized earlier because I rarely use them, so is this a 9.10 bug?

---

### Post by JamesParnell on 2009-11-12
just to let you guys know, after much confusion, it was my kernel (Ubuntu, Linux 2.6.31-15-generic) that was causing the bug. i tried my ...31-14 kernel and it was fine. just delete the above kernel and it should be fine

---

