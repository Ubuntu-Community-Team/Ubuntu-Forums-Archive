---
title: "Speakers and Headphones"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by justin43384 on 2010-08-14
When plugging in headphones and playing a song, the sound comes out of bothe the headphones and speakers.  Is there any way to fix this?

Thanks in advanced.:KS

---

### Post by blazemore on 2010-08-14
> **justin43384 said:**
> When plugging in headphones and playing a song, the sound comes out of bothe the headphones and speakers.  Is there any way to fix this?

Thanks in advanced.:KS

Where are the speakers plugged in? At the back? Are the headphones plugged into a port on the speakers themselves, or on the PC?

---

### Post by DarkAmbient on 2010-08-14
Goto system > settings > sound. (or what it's called i got Swedish Ubuntu so I'm not sure on the english name).

Theres a tab that should be called something like hardware. Either you turn off the unit that you dont want enabled. You do that by highlighting one of the units and then choose "off" in profil beneath.

Or you could click the 4th tab that should be called something like output. 

Then click any of the units available under that tab. One unit should be for the speakers, next one should be for the earphones. The one marked is the one that the sound will go through.

Sounds a bit strange that you get sounds through both speaker and headphones. But you should be able to turn off on and another through soundproperties.

---

### Post by blazemore on 2010-08-14
OK Try these two command in the terminal (best to copy & paste):

```

echo "options snd-hda-intel model=laptop" | sudo tee -a /etc/modprobe.d/alsa-base
sudo /etc/init.d/alsasound restart
```

That's worked on an HP laptop before.

---

### Post by justin43384 on 2010-08-15
I tried your ways but they didn't work.  iS there a command so I can just disable my speakers?

Also, m]y speakers are plugged straight in to my laptop.

---

