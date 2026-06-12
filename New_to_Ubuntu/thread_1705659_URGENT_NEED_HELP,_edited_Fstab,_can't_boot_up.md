---
title: "URGENT NEED HELP, edited Fstab, can't boot up"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by Justacop on 2011-03-12
I edited fstab trying to mount a cd, I really didnt have a clue what I was doing, and only afterwards realised I didnt have to, I made a backup called fstab_original, but in recovery mode I have no idea how to replace the broken fstab with the original. If anybody could please explain to me exactly what to type I would be very greatful.
Also I have already tried editing the fstab file but I am told that it is read only so I am really stuck and need a fix quickly...

---

### Post by andrewthomas on 2011-03-12
Where is the backup?

```
sudo mv /path/to/backup/filename /etc/fstab
```

---

### Post by Hippytaff on 2011-03-12
I have no ides, but since it's urgent [this]("http://ubuntuforums.org/showthread.php?t=283131") might be worth a read

@andrew thomas - long time no see...cheers for helping me out ages ago when I buggered up my gnome-desktop install

---

### Post by Justacop on 2011-03-12
thanks for the fast replies, the backup file is called fstab_original and is located in /etc right next to the broken fstab

---

### Post by Justacop on 2011-03-12
I guess that the code must go something like this then,
sudo mv /etc/backup/filename etc/fstab
ts my bet shot for now i guess but i dont want to mess things up any more XD

---

### Post by Hippytaff on 2011-03-12
That should do it

---

### Post by Justacop on 2011-03-12
=/ thanks for the help but I have tried "sudo mv backup/fstab etc/fstab_original" and some others. Still no luck, if anybody could show me exactly what to type then i would be a very greatful newbie.

---

### Post by Justacop on 2011-03-12
Okay i got this far. "sudo mv /etc/fstab_original /etc/fstab" this tells me that I cant backup because it is a read only file system =\ can anybody tell me how to do this? I am already root =S

---

### Post by Hippytaff on 2011-03-12
try doing sudo before the mv command...failing that you should be able to change the permissions of the fstab file as root...but I have no experience of this.

---

### Post by Justacop on 2011-03-12
Thanks for the help guys :D I figured it out,
to make backup i had to remount / i think XD, like this anyway
"mount -n -o remount /"
"sudo mv /etc/fstab_original /etc/fstab"
Then I just pressed Ctrl+D and it booted up like a charm, which makes the thread solved :D, so again thanks! I couldn't have done it without yahs :D.

---

### Post by Hippytaff on 2011-03-12
Your very welcome, but it looks as though you worked it out for yourself :-)

---

