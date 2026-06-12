---
title: "Just Installed Ubuntu, no sound?"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by tycho brahe on 2011-02-09
Hi,

Just bit the bullet and installed unbuntu as a dual boot, on top of windows XP. When I boot in xp sound is fine, but when I boot in ubuntu, media plays, but there is no sound... Thought it might be the motherboard drivers, but when I put the disk in and try to install I just get an error cant read message. Any ideas?

Thanks,

Zane

---

### Post by baldy4eva on 2011-02-09
Silly question, I know but, is the volume turned down?

---

### Post by tycho brahe on 2011-02-09
Ha Ha, yeah, I'd never live that down! It says the volume is on full on the media player, and also in the sound menu off the equvalent of the start bar...

---

### Post by tycho brahe on 2011-02-09
Just checked again, all volume controls I can find in sound preferences are 100% and hardware is listing the on board sound... I'm stuck!

---

### Post by tycho brahe on 2011-02-10
okay, pretty sure its a driver issue. Does ubuntu use different drivers to windows? If so wheres the best place to find them?

---

### Post by baldy4eva on 2011-02-10
Not too sure... Ubuntu should install an ALSA driver during install. Have a look here to see if your sound card is supported  [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

---

### Post by Vaphell on 2011-02-10
to narrow problem down open terminal and run
```
lspci
```
it will list devices your system has detected, look for something with audio. The line below will find it automatically
```
lspci | grep -i audio
```
Once the audio chipset model is known, it's easier to find a solution.

---

### Post by mastablasta on 2011-02-10
> **tycho brahe said:**
> okay, pretty sure its a driver issue. Does ubuntu use different drivers to windows? If so wheres the best place to find them?
 
Sure Ubuntu uses ALSA. 
 
What Ubuntu are you using? 10.10?
 
As already mentioned get the model of the card and post it here.
 
you might also want to check volumes in terminal by typing:
 
alsamixer 
 
and then setting the volume to full on all devices.
 
Next try changing the output (in sound preferences) to analog stereo.

---

### Post by tycho brahe on 2011-02-10
yup, its ubuntu 10.10. Just went system:admin:aditional drivers and it says no proprietary drivers in use, but my nividea GTX graphics card is working at least a bit... The sound is onboard on a gigabyte ma74gmt¬s2.
sound device: ATI technologies inc SBx00 Anzalia (intel HDA)

---

### Post by tycho brahe on 2011-02-10
when i type in alsamixer I get an error; cannotload mixer controls: Invalid argument

---

### Post by tycho brahe on 2011-02-10
put in a cheap generic sound card and now the sound is working ... really need to get the onboard sound working though cause i only have the one pci slot and i want to connect to the internet...

---

### Post by tycho brahe on 2011-02-15
Any ideas on solving the conflict?

---

### Post by tycho brahe on 2011-02-15
This worked for me too! Guy over at Tech Support forum had the same problem with the gigabyte_ motherboard_ (MA74GMT-S2), 
K-B suggested solution:

Go to terminal: 
 
Code:
 sudo nano /etc/modprobe.d/alsa-base.conf 

When the file opens, add these 2 lines to the end of it:
  
Code:
 alias snd-card-0 snd-hda-intel 
options snd-hda-intel model=auto

Dont understand what it did, but it worked! Can anyone explain? Thanks!

---

