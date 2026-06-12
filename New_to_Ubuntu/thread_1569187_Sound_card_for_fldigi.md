---
title: "Sound card for fldigi"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by bsmith52 on 2010-09-06
I've been trying to learn Ubuntu linux. Been reading thru tutorials. Formatted hard drive. Yesterday, loaded 10.04 with dual boot (Win XP). Installed drivers for printer. Installed software. But unable to configure fldigi for my sound card to work on ubuntu!

It should be simple: my sound card is working. It is the onboard card for the HP DC7100 tower. I'm accustomed to Win, and expect to see the name of my sound card. But I see some /dev/dsp, and some Intel ICH6 MIC devices (microphone?). I'm sure that one of these devices correlate to my sound card. But which one? How?

To get things going, I want to practice digial modes on the website websdr.org.

There must be a simple way to translate these devices into something that I can understand.

Thanx,
Bill KC0TBO

---

### Post by silbak04 on 2010-09-06
Try installing alsamixer.

```

$ sudo apititude install alsamixer

```

---

### Post by bsmith52 on 2010-09-06
Went to the alsa website and downloaded the .tar.bz2 file. Uncompressed with bunzip2. Then did the following:

tar -xvwf alsa-driver-1.0.23.tar

But this resulted in 100's of requests requiring a "y". So need to know how to perform this tar command recursively.

I also checked synaptic package manager. It turns out that there is already installed alsa-utils in 10.04. It includes "amixer". Do I need alsamixer also?

I was previously using 8.10. I did what I thought was a clean install of 10.04 (installed 10.04 from CD). But I had to re-install my Lazerjet 1012 print drivers, even though 10.04 "recognised" my printer. fldigi looks just the same under 10.04 as it did under 8.10. Maybe there is "stuff" left over from 8.10?

Thanks for your help.

---

### Post by silbak04 on 2010-09-06
First of all, no need to go to alsa website...since everything is in repo...just pop up a terminal (Applications->Accessories->Terminal) and type the following code:

```

$ sudo aptitude install alsamixer

```

no need to go to website and get the tar file and all that...

---

### Post by jcoles on 2011-01-23
Was this ever solved?

I have the same issue in Maverick Meerkat.

No selection on the fldigi Configure > Sound Card page will deliver Line In audio to the program. Alsamixer sets the audio levels for the inputs and with it I can hear the Line In, so I know that the sound card works. Also, other programs have no sound problems.

---

