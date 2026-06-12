---
title: "Sound still plays out of speakers when headphones plugged in?"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by sb5551 on 2010-06-02
Hi everybody

  I just noticed or was actually just told by the person sitting next to me that my speakers still play sound on my laptop even though my headphones are plugged in. The headphones work also. Am I supposed to manually turn this off? When I hit the mute button, the sound goes off on the headphones and the speakers.

My laptop is an HP Touchsmart Tx2. I have no idea what type of sound card or anything like that.

---

### Post by Uzi304 on 2010-06-02
I dunno the permanent fix but if you go into ```
gnome-volume-control
``` and you mute the section that says "Front" it should only play through the headphones. Remember that you have to click mute and not move the sliders all the way down.

---

### Post by ShadowMage on 2010-06-02
Hey there,

What version of Ubuntu are you using? I had this problem in Karmic, but I think it was actually a linux kernel bug. In Lucid I don't have this problem anymore, presumably because the bug is fixed in the newer kernel.

I'm using an HP Pavilion DV6 so it may or may not be exactly the same bug... if you're experiencing this issue in Lucid then hopefully someone else can help you, I don't know much more than what I've already said.

Good luck!

---

### Post by Cathhsmom on 2010-06-02
I am willing to bet that this is fixed by going to system, preferences, Sound.  Then under sound, select the hardware tab and select your headphones.  Then under the output tab, select your headphones. See if this fixes your problem.

---

### Post by sb5551 on 2010-06-02
Yea, I guess that would help I am using Lucid and just noticed the problem. 

I saw where I can change the hardware from speakers to headphones. That does work. Thank you. That does seem kind of annoying that you have to change it everytime you plug and unplug your headphones.

---

### Post by flyver on 2010-06-02
Same for my MSI Wind U120, it had this issue with 9.10 but not anymore with 10.04.

---

### Post by lidex on 2010-06-02
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel index=0 model=toshiba position_fix=1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by sb5551 on 2010-06-02
Thanks lidex.  I am not sure what I just did though when I followed your instructions. 

When I go to System>Preferences>Sound it doesn't give me a sound card, it just says internal audio.

---

### Post by lidex on 2010-06-02
> **sb5551 said:**
> Thanks lidex.  I am not sure what I just did though when I followed your instructions. 

When I go to System>Preferences>Sound it doesn't give me a sound card, it just says internal audio.

Not a problem then, that's the right one, as it's the only one.

---

