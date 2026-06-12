---
title: "Audio drivers for Intel 82801"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by reedte24 on 2009-01-15
Hello everyone! 

I am VERY new to Ubuntu. (Within the last 5 days).... However I have many years of technical background... so I should be able to understand most responses.

I'm using Ubuntu 8.10. The install went perfect except for my sound card. The bongo drum sound for Ubuntu plays when Ubuntu first starts up.... but it just loops forever and no sound will work from that point on.

I have an Intel IDT High Definition Audio 82801 card. The only ALSA driver that exists is the 92XXX (which Ubuntu reverted to) but it obviously isn't correct.

I ran "lspci -v" and this is what it says for the sound card:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f7
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at df300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

If you need to know anything else about my system please let me know. Can anyone help? Does anyone know of a driver for this card?

Thanks in advance!

---

### Post by 2hot6ft2 on 2009-01-15
I think you found the bug in PulseAudio setting the sound to 0 in Intrepid there's a fix in this thread.
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by reedte24 on 2009-01-16
Thanks for the suggestion 2hot, but it didn't do a thing. I went through the tutorial and pasted all of the commands into the terminal. I idnd't get any bad errors, but it still didn't help.

Like I said my card is the 82XXX version and it registers as the HDA Intel STAC 92XX card. I feel like this is the primary problem? But I could be wrong.

Also, when I go to System->Preferences->Sound and click on the test button I get the following error:

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused"

At least this is the error I get when it is set on "Autodetect"

When it is set on ALSA I get this:
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback."

I've attached a screen shot of my alsamixer so everyone can see what I'm looking at (and make sure it's set up correctly).

Any other ideas?

---

### Post by reedte24 on 2009-01-26
Hello everyone! I fixed the problem myself after some extensive research. I fixed it by adding the "irqpoll" boot option to the boot menu. After doing this my sound worked fine.

I found a tutorial on how to do it here:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

However, after doing this my computer seems to be rather unstable? It seems to freeze up rather consistently when I am doing anything more than chatting on Pidgin.

Anyone heard of this before? Thanks, and I hope this helps!

---

