---
title: "Skype sound"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by mbzn on 2009-02-24
Hi 
I installed skype, but have problems with the sound, tried all posible options.... I think i should have installed the OSS version. What is the best way to work around this?
I have a intel 82801DB-ICH4 (alsa mixer)
and the SigmaTel STAC9750,51 (OSS Mixer)
(this is what my volume control say)
If you need more info please tell me...

Thanx in advance

---

### Post by arochester on 2009-02-24
The microphone adjustments for Skype are in Skype and not in the computer sound settings.

Open Skype. Click on the S -button (bottom left). Choose Options. Choose Sound devices.

Look at Sound In, Sound Out and Ringing.

Mine didn't work until I changed it to an option with "HW" in it...

---

### Post by mbzn on 2009-02-24
Thanx, but i already tried all of the options in skype. there is either no sound coming out or it says problem with audio output(Something like that in the call screen). It now always say "problem with audio capture" and has no sound on the speakers?

---

### Post by Bölvaður on 2009-02-24
in System &#8594; Preferences &#8594; Sound, change everything to alsa.
in volume control find preferences and add all the options you will think is relevant and make sure input is "mic" and under Recording tab you got your microphone set to capture.... the graphical user interface is different from version to version so I cannot tell you where to click.

and you have Xubuntu and I have only had experience with it in 7.10, but never had problem with sound so I cannot remember how it was.

---

### Post by mbzn on 2009-02-24
hi, running gnome 8.10.
All my thing is on alsa. all my sound is working fine. its only skype that's not working???

any ideas?

---

### Post by mbzn on 2009-02-24
anything?

---

### Post by Bölvaður on 2009-02-25
ok first change your distro to ubuntu 8.10 ;)

Do not use Skype for these tests, use [COLOR="Silver"](Applications &#8594; Sound & Video &#8594; )[/COLOR]Sound Recorder
Then go and make sure your mic is plugged into the correct place (you may want to test all).

Now go back into volume control and under the Recording tab make sure you have the correct input unmuted (you can take all the red boxes with white x on them off to see if one of them might be the correct one). Capture to the max.
There is also supposed to be another source of input under "device". I got "ALSA PCM on front:0 (STAC92xx Analog) via DMA"

You should expect to see a moving pin in sound recorder to indicate the input into the mic, it may be only interference, which means that your audio card is working and you have found the correct settings.
You might be able to create internal interference by playing music while you are doing this, you do not need to listen for anything any way as Sound Recorder gives you visual feedback.

Under the options tab you should put all to mic (you may also want to check line in and see if that will work out better)


if you are using usb headset then there are similar settings for it.


If there comes no sound at all (no moving things to indicate that there is sound input... we dont care about what comes out of your speakers at this point)

If you got sound coming in, but not into skype then there is something wrong with the skype settings and you may want to focus only on skype after you have set the audio settings correctly.

---

