---
title: "Loud, annoying, scary sound at reboot"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by sleepee on 2010-02-11
First of all, my apologies if this is repeated.  i know this is somewhat of a common problem.
But i've got this problem where i hear this loud, popping sound from the speakers when i reboot my comp....and it's scary sometimes, because i don't expect it  lol!
but the thing is, it doesn't always happen.  it seems like my comp just does it when it feels like scaring me.

but other than when i reboot, it also happens when i log in through the console.  anytime i log in like that, that loud speaker noise happens when i hit the tab button for the auto-completion feature, or when i press backspace with no characters in the line, and of course, after i enter "sudo reboot"

now, i've checked the forums for some answers and one of the suggestions was to comment out this option in alsa-base.conf

```
# Power down HDA controllers after 10 idle seconds
# options snd-hda-intel power_save=10 power_save_controller=N
```

well, i tried that, but it didn't work.

another suggestion was to enter this line in the /etc/modprobe.d/blacklist.conf file

```
blacklist pcspkr
```

so i checked the blacklist file, and that line was already there..

so now i really don't know what else to try..
and this is kind of an embarrassing problem, especially when i take my laptop to school...
any help will be greatly appreciated.  thanks in advance

---

### Post by Kareeser on 2010-02-19
It sounds like your "alert sound" is corrupted... take a look at "Sound" in "Preferences". Can you mute the Alert volume, and when done, is the sound still there?

---

### Post by sleepee on 2010-02-25
hmmmm... i hadn't thought of that.  you might be on to something...
anyway, i'll try that out, but it might be a while before i get back to you because i have to test it out a few times since it seems to happen sporadically.

btw, i had recently taken out pulse audio and left alsa to try and fix another problem, but i put pulse audio back again...  just in case that might be relevant..

---

### Post by Lucid-Nvidia-&gt;rrrrrr on 2010-06-19
> **sleepee said:**
> hmmmm... i hadn't thought of that.  you might be on to something...
anyway, i'll try that out, but it might be a while before i get back to you because i have to test it out a few times since it seems to happen sporadically.

btw, i had recently taken out pulse audio and left alsa to try and fix another problem, but i put pulse audio back again...  just in case that might be relevant..

hey
any updates?were you able to fix it?

---

