---
title: "Toshiba laptop microphone not working"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-11-06
I am helping an old friend take his very first steps in computing. 

We went and bought a Toshiba Satellite L350-23J and I do admit it's kind of snazzy in it's grey pinstripe suit. 

Installation of 9.10 went incredibly well, everything works perfectly so far, even the webcam, with one little exception being the built-in microphone. 

The whole town has told my friend he's crazy for letting me talk him into using Ubuntu because it's so complicated and never works. 

Can someone help me with this mike problem?

Thanks a million you guys.

---

### Post by jbrown96 on 2009-11-06
*************
Edit: Try what Jr. Muffin said before you switch to alsa.
*************


Try switching to alsa. System-->Preferences-->Sound and switch all the options to alsa. Reboot. In a terminal (apps-->accessories-->terminal) ```
alsamixer
``` adjust the volume of the microphone channel. You probably shouldn't need to mess with mic boost because it can cause buzzing on the speakers. Esc to exit.

---

### Post by Jr.Muffin on 2009-11-06
Did you check out the settings on the 'Sound Preferences"? Right click on the little audio icon on the top right, click on "Sound Preferences" on the drop down list, and go to the "Input" tab. Play around with the Input volume, change the Connector and choose the right device. Let me know if playing around with the settings worked for you.

P.S: Make sure the "Input Volume" is not in mute.

---

### Post by tahitiwibble on 2009-11-06
I did everything suggested on this post [http://ubuntuforums.org/showpost.php?p=7688035&postcount=9](http://ubuntuforums.org/showpost.php?p=7688035&postcount=9)

The result is that the mike seems to work but sounds like pouring rain on a tin roof when doing a Skype test call.

---

### Post by jbrown96 on 2009-11-06
It looks like you are using alsa. open alsamixer and start using your microphone. Try adjusting/muting channels. 

Channels in Alsa can feedback into one another. You need to get rid (mute) of all channels that are not necessary. That should fix the problem.

---

### Post by tahitiwibble on 2009-11-06
> **jbrown96 said:**
> It looks like you are using alsa. open alsamixer and start using your microphone. Try adjusting/muting channels. 

Channels in Alsa can feedback into one another. You need to get rid (mute) of all channels that are not necessary. That should fix the problem.

Can't seem to get it. I got to a point where I can just hear myself behind a lot of hissing when recording/playing back a sound.

My usb headset works ok.

---

### Post by Arla on 2009-11-06
Might be worth trying installing
linux-backports-modules-alsa-2.6.31-14-generic 

My mic (totally different laptop) utterly failed to work until I installed this backport, at which point everything nicely came to life and worked perfectly.

---

### Post by tahitiwibble on 2009-11-06
> **Arla said:**
> Might be worth trying installing
linux-backports-modules-alsa-2.6.31-14-generic 

My mic (totally different laptop) utterly failed to work until I installed this backport, at which point everything nicely came to life and worked perfectly.

Thanks for chipping in. So would that be? ;

```
sudo apt-get install linux-backports-modules-alsa-2.6.31-14-generic
```

---

### Post by Arla on 2009-11-06
> **tahitiwibble said:**
> Thanks for chipping in. So would that be? ;

```
sudo apt-get install linux-backports-modules-alsa-2.6.31-14-generic
```

I believe so, although I just search for it in Synaptic vs doing command line.

---

### Post by tahitiwibble on 2009-11-06
> **Arla said:**
> Might be worth trying installing
linux-backports-modules-alsa-2.6.31-14-generic 

My mic (totally different laptop) utterly failed to work until I installed this backport, at which point everything nicely came to life and worked perfectly.

Bingo! Thanks Arla :D

---

