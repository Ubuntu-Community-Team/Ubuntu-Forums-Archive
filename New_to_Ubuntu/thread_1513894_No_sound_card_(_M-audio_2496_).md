---
title: "No sound card ( M-audio 2496 )"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by andreiiar on 2010-06-20
[LEFT]Ok. I managed to pul my internet connection ok now I'm dealing with the soundcard for the last 2 hours. It's an audiophile 2496 and lspci lists it with the 'kernel modules: oss_envy24'. I went to m-audio and they redicrected me to oss for a linux driver. I installed the driver and output is ok with 'osstest' command but i still get no sound card on 'aplay -l'. Also I have no modules beggining with snd- as i read for command 'modprobe snd-oss_envy24"eg
[/LEFT]

---

### Post by themusicalduck on 2010-06-20
Just wondering, which version of Ubuntu do you use? The standard Ubuntu version or something like Lubuntu? Do you have pulseaudio or have you removed anything like that?

I ask because I have a sound card very similar to the 2496 (Audiophile 192) and it is dealt with completely by pulseaudio without any problems at all. All I had to do was go to the sound settings from the volume menu and select the right output on the Output tab.

---

### Post by andreiiar on 2010-06-20
> My card is not showing as hardware. When I try to install the driver I get

'WARNING: Error running install command for snd
FATAL: Error inserting snd_ice17xx_ak4xxx (/lib/modules/2.6.32-22-generic/updates/alsa/pci/ice1712/snd-ice17xx-ak4xxx.ko): Unknown symbol in module, or unknown parameter (see dmesg)'

Fixed by reinstalling ubuntu. My fault

---

