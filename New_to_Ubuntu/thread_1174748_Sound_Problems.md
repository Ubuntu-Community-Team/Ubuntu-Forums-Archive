---
title: "Sound Problems"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-05-31
Hello, I am new to Ubuntu and the other day I opened a video but there was some back ground noise and it was annoying especially when the sound is low it happend to all the videos I opened so I tried using another video software and it still occured. I also faced the same problem when using a music player. Considering that the videos all work well on my Windows XP.

---

### Post by MontelEdwards on 2009-05-31
Open the volume control.
Press prefences.
Check PCM
then turn the PCM all the way up.

---

### Post by xoe on 2009-05-31
I don't have sound on my ubuntu 8.04lts. have read and tried just about every hint out there, but still nothing.
pls help!!!! am literally goin nuts as I only have ubuntu installed and need sound asap!
grateful for any/all help.
need newbie guide that doesnt assume I know anything about ubuntu which I dont.
tnx

---

### Post by mosaabJ on 2009-06-05
> **MontelEdwards said:**
> Open the volume control.
Press prefences.
Check PCM
then turn the PCM all the way up.

[SIZE="5"][COLOR="Red"]The PCM is turned all the way up[/COLOR][/SIZE]

---

### Post by eMJayy on 2009-06-05
> **mosaabJ said:**
> [SIZE="5"][COLOR="Red"]The PCM is turned all the way up[/COLOR][/SIZE]

It sounds as if you will need to try the other sound driver options located within *System > Sound*...this will open *Sound Preferences*... just select the drivers from the drop-down list next to the  *Movies and Music* option. click the test button to determine if the selected driver in the list will work. If you hear a tone during the test, that particular driver will work. 

On my PC, I'm using the Alsa drivers for my Soundblaster card, and the mixer I use is the Alsa mixer. I don't know what drivers are listed in your Sound Preferences menu, but there should be more than one option that should work with your PC.  

 Also, I've found that having System sounds turned on can affect the operation of my card at times (particularly when using 5.1 surround sound), so I have system sounds turned off. You can turn off system sounds by going to *System > Sound* and then clicking the Sounds tab...then untick 'play alerts and sounds'. You should probably try this first before testing and trying other drivers as I suggested above.

---

### Post by eMJayy on 2009-06-05
Forgot to add this link - [http://ubuntutip.googlepages.com/](http://ubuntutip.googlepages.com/)

This [website]("http://ubuntutip.googlepages.com/") is very useful for new Ubuntu users. It basically explains everything that you need to know as a newbie and has some useful troubleshooting tips. 

The section that's relevant for this thread is here - [http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)

---

