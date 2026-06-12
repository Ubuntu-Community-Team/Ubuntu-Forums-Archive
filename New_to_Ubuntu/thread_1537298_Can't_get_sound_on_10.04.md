---
title: "Can't get sound on 10.04"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by beltea on 2010-07-23
Hey guys

I recently upgraded to 10.04 Lucid from Karmic. I have a Toshiba Satellite L300. When i try to play music, or get some sound for that matter, no sound is heard. I need help, i've searched the net for answers but can't seem to find anything for me. I have an ICH8 Intel sound card and I can't find it here: 

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

In the previous version of Ubuntu (Karmic) my sound worked perfectly, why doesn't it now?

Anyone got some ideas?

---

### Post by dca on 2010-07-23
This isn't going to help much but I never do OS upgrades on any platform (Windows, etc) because of these possibilities.  Could be changes in sound systems between versions and now sound config is messed up...  I have same HD controller in my laptop and sound works fine but that was from a clean install.


...try this, find Ubuntu 10.04LTS 32bit Desktop Live CD and boot it up and see if there's sound...

---

### Post by beltea on 2010-07-23
I tried one of the guides that was posted here but it didn't work. I now get the message 

"no sound card found"

when typing  aplay-l. What can i do from here?

---

### Post by Eisenwinter on 2010-07-23
What is the brand name of your sound card?

---

### Post by Chad Olson on 2010-07-23
I had the same problem make shure you have all your software sorces up to date and run and update.

---

### Post by lidex on 2010-07-24
Purge your old pulseaudio config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Now re-install alsa. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

---

