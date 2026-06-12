---
title: "need help with configuring sound properly"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by KarenAK on 2009-05-21
first off: sound works, more or less, somehow. But.

I read a lot in this forum and followed all the recommendations until suddenly it worked. Mostly worked. But I really don't understand why and which combination of packages and settings I actually need to get sound.

I use logitech USB speakers and they work fine with firefox. However, whenever I switch to a music or video player, I have to move the stream back to the USB speakers.

And I cannot change the volume on my laptop volume control, I have to use the current application's volume control or the one in the systray.

Here's a screenshot of the sound preferences. All the test signals work except sound capture. 

And I really don't know what I should select as Default Mixer Tracks.

[IMG]http://i107.photobucket.com/albums/m312/KarenAK/Temp/Screenshot-SoundPreferences.png[/IMG]



Default Soundcard is set to Pulse Audio.

In Multimedia System Selector Audio the Default Output is set to PulseAudio Sound Server and ALSA PCM on front:1 (USB Audio) via DMA
I do get the test signal there.

Any other information I ought to supply ?


So, please, can anyone tell me how to get the laptop volume control working ?

Thanks in advance for any help with this.

---

### Post by 101011010010 on 2009-05-21
*I'm using Logitech Z10's in Jaunty. I have that option set to Logitech usb speaker (Alsa mixer).Also set volume control (click on speaker icon,click on volume control, set to Logitech usb speaker (alsa mixer)) & finally set Volume control preferences (menu on sound icon,click on preferences, set to the same as others,i.e.Logitech usb speakers (alsa mixer)).I hope this helps.*

---

### Post by KarenAK on 2009-05-21
THANK YOU !!

I have to admit that it never occurred to me to right-click the volume control...... :-)) 

Works ok now *happy dance

---

