---
title: "Sound keeps messing up everything"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by Zopiac on 2010-08-02
Here's my story. Sound used to work perfectly fine, as far as I was able to listen to music, and the controls were OK (but I had not tested gaming or wine yet) but when I installed my new motherboard a month or so back, the control went haywire. The keyboard control still changed the volume by 5% or so on the little popup volume indicator, but in alsamixer I could see that 0% on the volume slider meant 0% in alsamixer (I cannot remember which channel it was, but it was not changing the main volume whatsoever, which remained at 0%) while 5% on the slider was about 40% volume, 10% meant 80%, and 15% maxed it out at 100%, which was blasting loud. I had almost no control over the volume, since the jumps were so great. I was still able to work fine in rhythmbox, though, due to its volume changer that worked MUCH better than the ubuntu controls.

But then I tried to play Spring RTS. Sound didn't work in it at all, nor matter what I did, so I looked online and it said to remove pulseaudio. This is what really screwed me over. No sound worked at all until i worked for a good hour and a half to try to fix it, and even that didn't remedy it fully. Every once and a while when I just log in and start the game does it have sound, but usually not, while the sound throughout the system is damaged, too. The keyboard volume control does not work, alsamixer won't open:
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused
cannot open mixer: Connection refused
And I have no idea what to do.

All I want is to listen to music, run a few Wine games (which don't have working sound, but say they work perfectly on the AppDB, and I'm not sure if the problems I am experiencing are connected with it), run Spring, and be able to control it via keyboard, Correctly!

Please help me, because this is extremely aggravating. I can't do a reinstall of the OS, either, because Brasero seems to have a 100% fail rate recently.

---

### Post by -kg- on 2010-08-02
Well, I have some (possibly) bad news for you.

If you are still running Jaunty (9.04), the support cycle ends at the end of this month.  Unless you want to continue to run an unsupported OS (some do), you will need to upgrade (I suggest re-installation) at least to Karmic 9.10 (its support cycle ends in April 2011) or (suggested) to Lucid 10.04 LTS (its support cycle ends in 2013).

I've not heard of issues with Brasero, but then again, I use k3b for burning.

---

### Post by Zopiac on 2010-08-02
> **-kg- said:**
> Well, I have some (possibly) bad news for you.

If you are still running Jaunty (9.04), the support cycle ends at the end of this month.  Unless you want to continue to run an unsupported OS (some do), you will need to upgrade (I suggest re-installation) at least to Karmic 9.10 (its support cycle ends in April 2011) or (suggested) to Lucid 10.04 LTS (its support cycle ends in 2013).

I've not heard of issues with Brasero, but then again, I use k3b for burning.

No, I am running 10.04

Well I reinstalled pulseaudio, and am back to the fudged up volume control (at least it isn't completely broken now) and theres no sound period in Spring D:

---

### Post by sandyd on 2010-08-02
> **Zopiac said:**
> No, I am running 10.04

Well I reinstalled pulseaudio, and am back to the fudged up volume control (at least it isn't completely broken now) and theres no sound period in Spring D:
have you tried playing with pavucontrol?

---

### Post by simosx on 2010-08-02
When sound stops working or is misbehaving in general, the first thing to do is produce the alsa-info.sh settings file. This is pure Alsa settings, that can indicate if Alsa is to blame (for example, if there is a regression).

To do so, run

> wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh


You will be prompted to send the details to the alsa-project.org website. Select Yes and write down the URL for your data. 
Finally, post that URL here.

Killing pulseaudio, reinstalling pulseaudio or the alsa packages is too much of Windows troubleshooting.

---

### Post by Zopiac on 2010-08-02
> **carlee said:**
> have you tried playing with pavucontrol?

No I have not, I will try doing so now.
EDIT: It shows that there is output whilst running Spring, but I hear nothing.

> **simosx said:**
>  When sound stops working or is misbehaving in general, the first thing to do is produce the alsa-info.sh settings file. This is pure Alsa settings, that can indicate if Alsa is to blame (for example, if there is a regression).

You will be prompted to send the details to the alsa-project.org website. Select Yes and write down the URL for your data. 
Finally, post that URL here. 

[http://www.alsa-project.org/db/?f=800f992432704cff1771be96dbdfe9da95ff4c1f](http://www.alsa-project.org/db/?f=800f992432704cff1771be96dbdfe9da95ff4c1f)

---

### Post by Zopiac on 2010-08-02
Well I installed a PCI Sound Card in hopes of possibly fixing things (was using onboard) but Ubuntu couldn't even detect the card (was not in lspci) and continued to use onboard. Phooey.

---

### Post by Zopiac on 2010-08-02
Well I used a workaround for the volume control problem by disabling those shortcuts and creating ones for aumix -v +5 and aumix -v -5. However, the main problem still persists, and that is that there is no sound in Spring RTS.

---

### Post by Jeepman on 2010-08-02
I had the same issue with a HP laptop, what i did, I went into the synaptic package manager and installed the KDE Desktop environment. (don't load into KDE) After it was installed the sound worked and so did the wifi, Might want to try that out

---

### Post by Zopiac on 2010-08-02
> **Jeepman said:**
> I had the same issue with a HP laptop, what i did, I went into the synaptic package manager and installed the KDE Desktop environment. (don't load into KDE) After it was installed the sound worked and so did the wifi, Might want to try that out

Spring still has no sound...Wine games do at this time (it might be a result of reinstalling pulseaudio, running killall pulseaudio right before opening it, or the KDE trick, idk tho).

So right now the only thing I need to get running is Spring RTS!

---

### Post by simosx on 2010-08-02
> **Zopiac said:**
> 
[http://www.alsa-project.org/db/?f=800f992432704cff1771be96dbdfe9da95ff4c1f](http://www.alsa-project.org/db/?f=800f992432704cff1771be96dbdfe9da95ff4c1f)

The output looks quite complete and the kernel messages at the end do not show any warnings/errors.

With the alsa-info.sh output, we see you have the VIA VT1708S chipset. Using this and searching on Google gets us plenty of results of what to do next.

Your next move is to verify that the most generic audio commands work or not on your computer. See Takashi's (Linux Alsa developer) post on this, replying to your card some time ago,
[http://mailman.alsa-project.org/pipermail/alsa-devel/2009-July/019290.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-July/019290.html)

Next step is to check if there is a BIOS update available for your computer. If there is, it's recommended to update your BIOS. It has happened before that DSDT tables in the BIOS where wrong and the manufacturer silently fixed them (Google for 'DSDT Ubuntu' for background on DSDT issues). Try again the instructions by Takashi.

Next step is to try to update your Alsa to the very latest. You currently have Alsa 1.0.21 (kernel) and the latest is 1.0.23. See [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810) for instructions. You can revert back to your previous version by reinstalling the Alsa packages. Once you perform this, restart. Try the instructions by Takashi.
Produce a new alsa-info.sh and post it here. The alsa-info.sh will be different due to a newer Alsa. Then we can compare the two together to see what changed.

Finally, you can try different 'model' names instead of letting Alsa autodetect your hardware. See [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568) for information on how to try out different model names. If you manage to find a solution, it's important to report it so that Alsa is updated and in the next version your hardware is autoupdated. Some users find the existing model name, but forget to tell anyone and users like you have to do the work again and again.

That's some work to do. Good luck! :popcorn:

---

### Post by Jeepman on 2010-08-02
sorry that the KDE did not work.

---

### Post by Zopiac on 2010-08-02
> **simosx said:**
> The output looks quite complete and the kernel messages at the end do not show any warnings/errors.

With the alsa-info.sh output, we see you have the VIA VT1708S chipset. Using this and searching on Google gets us plenty of results of what to do next.

Your next move is to verify that the most generic audio commands work or not on your computer. See Takashi's (Linux Alsa developer) post on this, replying to your card some time ago,
[http://mailman.alsa-project.org/pipermail/alsa-devel/2009-July/019290.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-July/019290.html)
This has been completed successfully; the two commands work flawlessly.

> **simosx said:**
> Next step is to check if there is a BIOS update available for your computer. If there is, it's recommended to update your BIOS. It has happened before that DSDT tables in the BIOS where wrong and the manufacturer silently fixed them (Google for 'DSDT Ubuntu' for background on DSDT issues). Try again the instructions by Takashi.
I recently updated BIOS when I switched motherboards.

> **simosx said:**
> Next step is to try to update your Alsa to the very latest. You currently have Alsa 1.0.21 (kernel) and the latest is 1.0.23. See [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810) for instructions. You can revert back to your previous version by reinstalling the Alsa packages. Once you perform this, restart. Try the instructions by Takashi.
Produce a new alsa-info.sh and post it here. The alsa-info.sh will be different due to a newer Alsa. Then we can compare the two together to see what changed.
OK, I've upgraded, here is my alsa-info.sh: [http://www.alsa-project.org/db/?f=4a2745be98e76fee468e62ba8f1361736e9b8c2a](http://www.alsa-project.org/db/?f=4a2745be98e76fee468e62ba8f1361736e9b8c2a)

> **simosx said:**
> Finally, you can try different 'model' names instead of letting Alsa autodetect your hardware. See [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568) for information on how to try out different model names. If you manage to find a solution, it's important to report it so that Alsa is updated and in the next version your hardware is autoupdated. Some users find the existing model name, but forget to tell anyone and users like you have to do the work again and again.
I'm not exactly sure what to do for this or what it will do. Elaboration please?

> **simosx said:**
> That's some work to do. Good luck! :popcorn:
:( Not so far... But thanks for trying! Hopefully we can get this sorted out.

---

### Post by simosx on 2010-08-03
First of all, thanks for going through all the steps. Not many people manage to complete them.

> **Zopiac said:**
> This has been completed successfully; the two commands work flawlessly.

Since these work, then you can record and playback audio using Alsa just fine. You may test here if 
1. jack sense is working for the headset and the headset microphone. That is, you perform the same commands but with your headset plugged in. 
This normally requires some minor changes in Alsa to fix, if it does not work.

Since Alsa works for playback and recording, then you step to the next level which is PulseAudio configuration, and looking into the PulseAudio bug reports for issues.

> **Zopiac said:**
> I recently updated BIOS when I switched motherboards.


OK, I've upgraded, here is my alsa-info.sh: [http://www.alsa-project.org/db/?f=4a2745be98e76fee468e62ba8f1361736e9b8c2a](http://www.alsa-project.org/db/?f=4a2745be98e76fee468e62ba8f1361736e9b8c2a)


I'm not exactly sure what to do for this or what it will do. Elaboration please?

If you did not have any playback/recording using the primitive Alsa commands (but it worked in step 1 so no need), you would need to try out different Alsa model names. You add the parameter in /etc/modprobe.d/alsa-base.conf then you reload the Alsa Linux kernel driver and recheck.

> **Zopiac said:**
> :( Not so far... But thanks for trying! Hopefully we can get this sorted out.

Since Alsa works for you as shown in Step 1, then your task is to get PulseAudio configured properly. It is possible that PulseAudio, for some reason, has configured to send audio by default to an unused destination (for example, HDMI?). You would google now for 'PulseAudio configuration'. Try first the GUI tools to select different sources and sinks. There are also command line tools, parec, parecord which can record from different sources. Try them out.

---

