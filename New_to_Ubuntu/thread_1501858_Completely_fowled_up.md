---
title: "Completely fowled up"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by jetgraphics on 2010-06-04
Greetings. I am a recent transplant from Mandriva (KDE) to Ubuntu (Gnome) and am somewhat bemused, befuddled, and occasionally lost.

**Audio:**
When running Win XP, I use the computer to drive 5.1 speaker system, from 3 other sources (KVM switched). In other words, depending on the KVM switch, the KVM **audio out** goes into the LINE IN, and then feeds out to the speakers.
[UBUNTU] I verified that the input was not mic but line in. But no sound comes out. Is there something or application that needs to be initialized so that the LINE IN is sent to the 5.1 speaker system?

**Video:**
I have two LCD monitors fed by HD-2600XT graphics card.
After the initial load and boot, Ubuntu allowed me to adjust the monitors from mirror to separate displays. However, once it finished upgrading, and rebooting, the twin monitor settings were gone.

---

### Post by Mariane on 2010-06-04
If you are using alsa, try typing alsamixer or alsamixergui in a terminal to adjust the volume of all possible sound outputs independently. 

As for the dual monitor settings you have to log into Gnome if you are using kde and then look for: 
system > administration > "your hardware"

For example I have nVidia graphic card so I configure the 2 monitors in:
system > administration > nVidia

Or maybe it is
administration > system > nVidia? Anyway, you'll find it. 

With Ubuntu some settings seem to be only tuned under Gnome, but you can still use kde if you like. You type:
sudo apt-get install kdebase

Then nex time you log in you will be given the choice on the login screen between kde and Gnome (The default is whichever you used last).


Mariane

---

### Post by jwbrase on 2010-06-04
> **jetgraphics said:**
> **Audio:**
When running Win XP, I use the computer to drive 5.1 speaker system, from 3 other sources (KVM switched). In other words, depending on the KVM switch, the KVM **audio out** goes into the LINE IN, and then feeds out to the speakers.
[UBUNTU] I verified that the input was not mic but line in. But no sound comes out. Is there something or application that needs to be initialized so that the LINE IN is sent to the 5.1 speaker system?

One of the more irritating things with a new Ubuntu install. There's a setting somewhere that ends up defaulting to things being muted (at least on Intrepid and Jaunty, which are the two versions I've used), but it's really well hidden, and since a reinstall isn't an everyday occurence, I always have to hunt for it again each time I do a new install...

---

### Post by jetgraphics on 2010-06-07
So far, I have not found the solution.
Audio applications play audio files.
And the mixer app shows the proper input is selected (Line in, not Mic), and not muted.
But the Line in signal is not being sent out to the speakers.

Video problem is intermittent.
When I boot Linux, sometimes it comes up with only one monitor active (in the hardware section), with mirrored display.
I reboot, and then the two monitors are active, without the mirrored display.
I dunno.

---

### Post by 4Orbs on 2010-06-07
On the alsa mixer, you might try the Aux In rather than Line In. If you don't see an Aux In slider, there is a button on the mixer where you can add a number of different control sliders that normally don't show up by default.

EDIT: The Alsa Mixer gui is not the same mixer that opens when you just click the mixer link on the System Menu.

---

