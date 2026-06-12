---
title: "Headphone Issues"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by neely.nelson on 2009-08-26
I have been looking for a recent post concerning headphone issues, but haven't been able to find anything that is particular to my computer.  I am a newbie, so any help is appreciated.  Here is my dilemma:

I am running alsamixer 1.0.18.  My sound works fine without the headphones, but when the headphones are plugged in, I get no sound at all.  I checked alsamixer, and there is no slider for headphones.  I have tried to upgrade to 1.0.19 and 1.0.20, but when I check to see if the upgrades took, I am still at 1.0.18.

-I am running an Everex Stepnote VA4101M.  
-cat /proc/asound/card0/codec#* | grep Codec produces the following in regards to a soundcard:

Codec: VIA VT1708
Codec: Conexant ID 2bfa

-I went to [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845), but could not find anything that would help me out.

I want to be able to use my headphones.  Any help is greatly appreciated!!!

---

### Post by candtalan on 2009-08-27
might help, not sure:

right click the loudspeaker icon at the top right of the screen. I can see open volume control and also preferences.

When I open the volume control and then look at *its* preferences I see a lot of options, which can be checked ticked.

Do you see a headphone option here?

---

### Post by neely.nelson on 2009-08-27
There is no volume control whatsoever.

---

### Post by neely.nelson on 2009-08-27
UPDATE:

I figured out how to properly install the latest alsamixer.  However, there is still no headphone slider. I have submitted the screenshot of what the alsamixer looks like on my laptop.[FONT=monospace][/FONT]

---

### Post by candtalan on 2009-08-27
> **neely.nelson said:**
> UPDATE:

I figured out how to properly install the latest alsamixer.  However, there is still no headphone slider. I have submitted the screenshot of what the alsamixer looks like on my laptop.[FONT=monospace][/FONT]

The speaker icon I draw your attention to is the icon next to the WiFi signal icon. Right click on the speaker icon and the context menu should include a Volume Control or Open Volume conttrol or similar. Yes?

---

### Post by candtalan on 2009-08-27
The thumbnail picture of your alsamixer windows shows an alsmixer menu bar. Does the Edit menu offer any preferences to be chosen (such as headphones)?

BTW which Ubuntu version are you using?

---

### Post by neely.nelson on 2009-08-27
This is actually the Pulse Audio volume control.  In another thread, it was suggested to change the alsamixer volume control to the Pulse Audio control.  I can't figure out how to get the alsamixer control back.  I have been going to system->preferences->sound and adjusting from there.

I am currently using Jaunty Jackalope 9.04

I am enclosing the screenshot of what is in sound preferences.

---

### Post by candtalan on 2009-08-27
> I can't figure out how to get the alsamixer control back

try system>administration>synaptic package manager 
and install (alsa mixer)

You might have to manage which mixer is default but I played with several mixers and they did not conflict (that I was aware of)

pay special attention to the drop down menu options, and the edit>preferences in the several menus.
hth

---

### Post by neely.nelson on 2009-08-27
I have updated the alsamixer volume control (though I can't get rid of the other volume control). I am including a screenshot of what I see from alsamixer.  As you can see, there is no headphone slider.

---

### Post by SunnyRabbiera on 2009-08-27
Is this a frontal headphone jack?
Laptop or desktop?

---

### Post by neely.nelson on 2009-08-27
The Everex Stepnote va4101m is a laptop, with the headphone jack on the side of the laptop next to the microphone jack.  I have one internal speaker, which works.  I have no sound when I plug in the headphones.

---

### Post by SunnyRabbiera on 2009-08-27
> **neely.nelson said:**
> The Everex Stepnote va4101m is a laptop, with the headphone jack on the side of the laptop next to the microphone jack.  I have one internal speaker, which works.  I have no sound when I plug in the headphones.

did you try the volume button on the front then?
If it has one that is, sometimes real simple crap like that can mess up your day.

---

### Post by neely.nelson on 2009-08-27
There is no volume button.  However, there is a function button on the keyboard to turn up the volume.  I guess that is what $500 at Wal Mart gets you:).  I have tried adjusting the volume from the keyboard, to no avail.  Whenever I adjust the volume, I will take the headphones out to ensure that the volume is still working before I plug the headphones in.  If I can just figure out why I don't have the headphone slider, and figure out how to fix it, all will be fine.

---

### Post by Suranjit on 2009-08-28
Thank you 'candtalan'. It really helped me. Thanks.

---

### Post by neely.nelson on 2009-09-04
I have tried the volume buttons on the laptop, and still I have no sound out of the headphones.  I just can't seem to think of anything else to try.

---

