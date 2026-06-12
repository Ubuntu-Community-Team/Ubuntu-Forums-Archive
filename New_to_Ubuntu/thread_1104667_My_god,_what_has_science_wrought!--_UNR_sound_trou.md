---
title: "My god, what has science wrought?!-- UNR sound trouble on an HP Mini 1030NR"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Norph on 2009-03-23
So I just got a little netbook.  An HP Mini 1030NR, as the thread title indicates.  I love the dang thing already.  To pieces.  To bits.  But I decided I didn't quite want to use Windows XP again.  I'd never used Ubuntu (or indeed anything but windows/macos) before, so I was leery of taking the full plunge and removing windows from a system with no optical drive.  I installed Ubuntu Netbook Remix (Jaunty) instead on a 4 gig microSD card I had lying around.  It's working surprisingly well, aside from sound.

There is no sound.  Whatsoever.  It neither records anything nor plays back anything.  Woe is me.  Woe, woe, woe.  I don't give up, though.  I find [this here thread](http://ubuntuforums.org/archive/index.php/t-997590.html) in which the last post advises > 
1) Edit /etc/modprobe.d/alsa-base and add the following line:
options snd-hda-intel model=ref

2) Right click the Volume Control on the panel and click preferences. Click on PCM to highlight it.

3) Double click on the Volume Control on the panel, click Edit, and then click preferences. Check off "Digital Input Source", and both "Input Source" check boxes.

4) Click on the options tab, and set "Digital Input Source" to "Analog Inputs", the first "Input Source" to "Line", and the second "Input Source" to "Mic". Everything should now be working.

I did not need to change anything for the hot keys to work.
I've got as far as editing the file that guy suggested, but I can't save it.  The text editor comes up with "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."  I'm hoping that following that advice will allow me to get sound and thereby ditch windows entirely.  But if I can't save then it's nearly moot.  How do I give myself permission to edit the file?

---

### Post by fooman on 2009-03-23
in order to edit the file in step one of the thread you quoted,  you need root permissions.  you get them by entering a "sudo" or "gksudo" in front of the command.  you will then be prompted to enter your password,  which will be invisible as it is typed...so make sure to type it correctly!

to edit the file, type or copy/paste the following into a terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

then add the suggested line, save and close the file.

hope that helps.

---

### Post by Norph on 2009-03-23
That's helping, yes, but I need a little more info.  How do I get to commandline?  Do I have to reboot and go into debug mode?

---

### Post by fooman on 2009-03-23
> **Norph said:**
> That's helping, yes, but I need a little more info.  How do I get to commandline?

you mean a terminal?  ...i am not sure how your distro is set up with menus,  but in ubuntu... you just go to applications > accessories > terminal

---

### Post by Norph on 2009-03-23
Your instructions were right, but somehow the whole damn thing went haywire after I did what those instructions said and rebooted.  Looking for suggestions about sound.

---

