---
title: "Sound problem-weird noises on 10.04"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by U-Ren on 2010-09-27
Hello, I'm a very recent user of Ubuntu and I'm having this weird problem with my sound that I can't fix. I tried all the sound troubleshooting threads, including the new Alsa package. So:

-I have a Asus motherboard with a Realtek HD sound card-it has a front panel and back one. The card is recognized from linux and it works well, I can hear sound (*good* sound) from both the speakers and the headphones on the front panel.

-The problem is that besides that, I can hear a weird clacking/crack sound from both my speakers and my headphones all the time, from the moment Ubuntu starts loading. More weird sounds happen when the hard drive is working heavily, or the cd-room is reading a cd (it seems like all the sounds from the pc are being 'played' in the speakers). I heard it even during the Ubuntu installation and I can hear it even in another linux I tried (mandriva linux). 
It never happens in Windows, nor in bios/before the load of Ubuntu. In windows and bios I can only hear the light sounds of the fans.

Btw. Right now, I have a fresh installed Ubuntu with no alterations (I can't even play mp3 in this one as I didn't install codecs or anything). The one I messed with was on another drive that I use for testing.

Uh-any idea?  Thank you.

---

### Post by jtarin on 2010-09-27
Disabling Compiz seems to help some with these same symptoms.

---

### Post by U-Ren on 2010-09-27
> **jtarin said:**
> Disabling Compiz seems to help some with these same symptoms.

What should I do? Remove the compiz package? Or something else? I'm very, very new at this and I'm scared to alter stuff on my own.

---

### Post by jtarin on 2010-09-27
Go to System > Preferences > Appearance..and select None on the Visual Effects tab.

---

### Post by U-Ren on 2010-09-27
> **jtarin said:**
> Go to System > Preferences > Appearance..and select None on the Visual Effects tab.

I already have it disabled then. I had it like that since I installed it. It doesn't seem to fix it. :(

---

### Post by U-Ren on 2010-09-27
I think I ...fixed it? 

I installed the Alsa mixer and muted the cd. The noise disappeared. 

I don't know if I can call this a fixed problem but at least it's not bothering me anymore, so I'm considering it as solved.

Thanks~

---

### Post by lordmonkeyu on 2011-10-09
I have the same problem on Acer TravelMate 574G and the AlsaMixer "trick" does not help. Anyone has some ideas ?

---

### Post by U-Ren on 2011-10-12
> **lordmonkeyu said:**
> I have the same problem on Acer TravelMate 574G and the AlsaMixer "trick" does not help. Anyone has some ideas ?

Did you try to alter the settings in the mixer? I had another weird problem in Natty and changing one of the sliders (can't remember which) muted the clicking.

---

