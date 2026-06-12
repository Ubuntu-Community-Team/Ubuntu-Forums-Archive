---
title: "Audio problem"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by deusxechelon on 2009-04-17
Ive googled and googled and googled and cannot come up with a solution. I have no sound, but if i blow into the microphone, I can hear it on the speakers. I attempted to follow the guide here on the forums: [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845) but it appears to not apply to me. Any ideas would be appreciated!

System:
P5Q SE Plus
On board Audio

uname -r
2.6.24-23-generic

aplay -l:(
Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

asoundconf list
Names of available sound cards:
Intel

lspci -v
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: ASUSTeK Computer Inc. Unknown device 82fe
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

### Post by deusxechelon on 2009-04-19
Bump

---

### Post by JoshuaRL on 2009-04-19
> **deusxechelon said:**
> Bump

You might try double-clicking the little volume applet on the panel/taskbar, and making sure all the sliders are up.  I've had that happen to me where one I thought didn't matter was down and my sound didn't work.

---

### Post by Achilles124 on 2009-04-19
There are several audio drivers available for Linux. If I remember correctly: pulseaudio is one of them. Another is alsa. I am not an expert on this but I think you have to test your system on different audiodrivers. 

Note: interesting is that your mic does work. Try to use audacity and see what works with audacity. Then you have your driver you need also.

---

### Post by deusxechelon on 2009-04-19
> **JoshuaRL said:**
> You might try double-clicking the little volume applet on the panel/taskbar, and making sure all the sliders are up.  I've had that happen to me where one I thought didn't matter was down and my sound didn't work.

Ive checked that more times than I care to share, believe me. Though Im not entirely sure which I should have my audio set to on my volume control. In 'Change Device' I have several things listed:

-HDA Intel (ALSA mixer)
-VIA ID 397 (OSS Mixer)
-Playback: Alsa PCM on front:0 (HDA Generic) Via DMA (Pulseaudio mixer)
-Capture: Monitor source of ALSA PCM on front:0 (HDA Generic) Via DMA (Pulseaudio mixer)
-Capture: Alsa PCM on front:0 (HDA Generic) Via DMA (Pulseaudio mixer)

All of which are on max volume and unmuted. Also FYI, I have a headset jacked in the back and speakers jacked into the front panel (I remove the speakers from time to time to move to another pc, makes life easier)

Hope this makes guidance easier

> **Achilles124 said:**
> There are several audio drivers available for Linux. If I remember correctly: pulseaudio is one of them. Another is alsa. I am not an expert on this but I think you have to test your system on different audiodrivers. 

Note: interesting is that your mic does work. Try to use audacity and see what works with audacity. Then you have your driver you need also.

Thanks for your response. I just tried audacity, when I talk into the mic while recording, I can hear myself live but the audio lines indicating that the program is receiving the audio do not move.. nor is there sound when I play it back.

Are there settings I should play with?


Any other ideas?

---

### Post by JoshuaRL on 2009-04-19
> **Achilles124 said:**
> There are several audio drivers available for Linux. If I remember correctly: pulseaudio is one of them. Another is alsa. I am not an expert on this but I think you have to test your system on different audiodrivers.

Technically, PulseAudio an ALSA aren't drivers.  A driver goes in between the OS and the hardware, and makes the harware work.  PulseAudio and ALSA are sound servers.  You'll need to have the right driver for your audio card separate from them.  But if you can hear anything other than a system beep, that part is okay.  From [what I read here,](http://ubuntuforums.org/showthread.php?t=789578) it seems like there is a bug in Intrepid that sometimes sound will get reset to 0.  I think this is the OP's problem.

---

### Post by deusxechelon on 2009-04-19
[QUOTE=Achilles124] From [what I read here,](http://ubuntuforums.org/showthread.php?t=789578) it seems like there is a bug in Intrepid that sometimes sound will get reset to 0.  I think this is the OP's problem.[/QUOTE]

Going to give this a shot, will post back with a yay or nay. Thanks.

---

### Post by deusxechelon on 2009-04-19
Unfortunately still no sound, followed each step exactly however I did come across something unusual not mentioned in that guide

> Appendix A - General Troubleshooting
This section will outline some general troubleshooting steps you can perform to help identify your problem, and the information I need to help with your issues:

   1. Close all applications that may be accessing the sound card.
   2. Open the "PulseAudio Device Chooser" from Applications/Sound & Video. Click on the applet icon, and click "Volume Control...". Click on the "Playback" tab.
   3. Launch the application you wish to test and allow it to play sound.
   4. Check PulseAudio Volume Control's Playback tab and see if the application displays an entry while the application is (or should be) playing audio.


After I followed all the steps and sitll had no sound I went down to the troubleshooting section and where it mentions open Pulseaudio device chooser, when I do that nothing happens, no error, nothing.

---

### Post by gackt on 2009-04-21
hey, at least your system do have sound. I'm sure the solution is around the corner, care to try this stupid method?
open terminal:
1. sudo alsa force-reload
   after that
2. Pulseaudio

Gud luck

---

