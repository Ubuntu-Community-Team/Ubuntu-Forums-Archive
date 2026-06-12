---
title: "Toshiba L655 Headphone problem 10.10"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by Vi3tHoneyX on 2011-06-16
Hi. I just installed 10.10 on my friend's Toshiba L655 and it seems as if headphones aren't recognized when plugged in. The speaker continues to play the sound and you can't hear anything in the headphones. 

I tried to do what the first post of this thread said

[http://ubuntuforums.org/showthread.php?t=1641931&highlight=l655+audio](http://ubuntuforums.org/showthread.php?t=1641931&highlight=l655+audio)

but I don't understand how to. How do I edit and add the code?

I also followed the directions for this using the command line

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

but that didn't work either. I'm not sure what to do now. Any and all help would be appreciated. Thank you ahead of time!!!

---

### Post by mister_playboy on 2011-06-16
> **Vi3tHoneyX said:**
> I tried to do what the first post of this thread said

[http://ubuntuforums.org/showthread.php?t=1641931&highlight=l655+audio](http://ubuntuforums.org/showthread.php?t=1641931&highlight=l655+audio)

but I don't understand how to. How do I edit and add the code?

From the terminal, run:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

in the gedit window that opens, paste the line

```
options snd-hda-intel model=thinkpad
```

See if that does anything for the problem.

---

### Post by Vi3tHoneyX on 2011-06-17
Absolute perfection!!!!! Thank you very, very much. :D

<3<3<3<3<3<3<3<3<3<3<3<3<3<3<3<3<3

---

### Post by Vi3tHoneyX on 2011-06-17
Now how do I marked this thread as solved?...

---

### Post by Perfect Storm on 2011-06-17
Thread tools. Just above your first post in this thread.

---

