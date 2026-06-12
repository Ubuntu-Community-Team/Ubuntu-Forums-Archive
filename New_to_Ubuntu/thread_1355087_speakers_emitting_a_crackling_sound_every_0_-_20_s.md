---
title: "speakers emitting a crackling sound every 0 - 20 seconds"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by kapi on 2009-12-14
9.is brilliant, I even got my mic to work which didn't in 9.04.

but the speakers on my laptop keep emitting a crackle every 10 or so seconds while the laptop is running. However when I play sound the noise stops and doesn't return. Any ideas. I guess I can live with it, but am curious as to its source.

---

### Post by bacardiandwatermelon on 2009-12-14
I'm so sure this topic has come up before :-)

---

### Post by ajgreeny on 2009-12-14
I imagine you have an HDA sound card.  Search for "HDA crackling" and you will find the answer, I think.

No 1 in google:
**Procedure to follow** Open terminal and enter the following comamnd
 [INDENT]gksudo gedit /etc/modprobe.d/alsa-base.conf
[/INDENT] This will prompt for password
 Now you have to delete last two lines where you see power-save option
 Save and exit the file.
 If you want you can take backup of the above file before doing any changes
 Credit goes [here ]("http://ubuntuforums.org/showthread.php?t=1335045")

---

### Post by kapi on 2009-12-14
Thanks very much will try, just got skype working so hope it doesn't mess with the settings.

---

### Post by kapi on 2009-12-14
Brilliant

thank you so much- it seems to have worked

listen . . . . . . no crackle, just peace

---

