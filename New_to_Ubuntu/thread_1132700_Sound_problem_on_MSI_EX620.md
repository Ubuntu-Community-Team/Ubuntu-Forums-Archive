---
title: "Sound problem on MSI EX620"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by kasperLJ on 2009-04-22
Hi there!
 
I have just installed Ubuntu 8.10 on my MSI EX620 laptop. I am completely new to Linux and ubuntu, and I have the following problem.
 
I can play sound files, but there does not come any sound from the speakers. I've got a double boot, with windows vista on the second partition. When the computer is running in windows there is no problem with sounds. It was bought with vista pre-installed.
 
I think the sound card is ATI HDMI Audio.
 
Maybe someone carefully can give instructions on how to get the sound working when in Ubuntu?

---

### Post by craig_f on 2009-07-03
I know this is old, but I have the same machine except I am running 9.04.  I think the steps may be the same.  The sound was actually working on mine but only out of the jack on the side.  
To fix: 
add "options snd-hda-intel model=6stack-dig probe_mask=1" 
To the end of /etc/modprobe.d/alsa-base.conf
reboot

I actually found this on another forum, but I cant remember where that was now.

---

### Post by tommie74 on 2009-07-14
To fix:
add "options snd-hda-intel model=targa-dig"
To the end of /etc/modprobe.d/alsa-base.conf
reboot

This works better for me because when using the headphone the speakers disable automaticly. It also is advised for msi in /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

---

### Post by Yamikora on 2012-07-22
Hi 
I have the same problem :/
when I trayed to add "options snd-hda-intel model=targa-dig"
To the end of /etc/modprobe.d/alsa-base.conf 
I got a message telling me that it's not possible to save  that file .
can you help me in this :) ?

---

### Post by jmfal on 2012-07-22
Change model= targa-dig

to model=auto

---

### Post by jmfal on 2012-07-22
To edit/save the file run this in terminal
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf   
```

Enter your password
file will open
Scroll to end of file
Add line (try your original option first)
Click save button (in file window)
close/save in etc folder(click etc , click save , close)
Restart pc/laptop for change to take effect
Make sure volumes are not muted
test sound

---

