---
title: "How can I disable pulse audio?"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by Mariane on 2010-01-24
I have alsa functioning, but I'm afraid pulse audio is still lurking in my laptop. 

When I type : 
say hi
I hear "hi hi"

longer sentences are always followed by an echo or garbled at the end. 

Mariane

---

### Post by llawwehttam on 2010-01-24
Pulseaudio is very intertwined with the gnome-desktop.

As I have posted before:

```
llawwehttam@Deadlock:~$ apt remove pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be **REMOVED**
  libcanberra-pulse pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev
  pulseaudio-module-x11 **ubuntu-desktop**
0 upgraded, 0 newly installed, 8 to remove and 4 not upgraded.
After this operation, 5,325kB disk space will be freed.
Do you want to continue [Y/n]? 


```and yes I have an alias:

```
alias apt='sudo apt-get'
```However I don't know how much it is with the KDE desktop. Have you tried:
```
 sudo apt-get purge pulseaudio*
```

EDIT: If you try the above then carefully read all packages it wants to remove before proceeding.

---

### Post by Mariane on 2010-01-24
Thank you. 

It says: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdns35
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  pulseaudio*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1106kB disk space will be freed.

So it looks OK.

Mariane

---

### Post by marshmallow1304 on 2010-01-24
AFAIK, pulseaudio is not installed by default on Kubuntu.

---

### Post by Mariane on 2010-01-24
It was installed on my laptop and I don't remember ever apt-getting it. But I'm not certain, I fiddled with sound so much... 

Anyway, now it's gone but the problem remains. The "say hi" is just a symptom of it, my main problem is that whenever I plug a headphone (and I have tried 3 different headphones) the sound keeps coming out of the laptop speaker. 

aplay -l says I have 2 sound devices:
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Is that normal? 

Mariane

---

