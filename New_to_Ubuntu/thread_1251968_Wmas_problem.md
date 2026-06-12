---
title: "Wmas problem"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by mbaybarsk on 2009-08-28
I get an error like this when i try to play a video with VLC player. There is video but no sound...

"  p, li { white-space: pre-wrap; }[COLOR=#ff0000]No suitable decoder module:[/COLOR] [COLOR=#000000]VLC does not support the audio or video format "wmas". Unfortunately there is no way for you to fix this."[/COLOR]


[COLOR=#000000]Is there really no way to fix this? 
[/COLOR]

---

### Post by sydbat on 2009-08-28
> **mbaybarsk said:**
> I get an error like this when i try to play a video with VLC player. There is video but no sound...

"  p, li { white-space: pre-wrap; }[COLOR=#ff0000]No suitable decoder module:[/COLOR] [COLOR=#000000]VLC does not support the audio or video format "wmas". Unfortunately there is no way for you to fix this."[/COLOR]


[COLOR=#000000]Is there really no way to fix this? 
[/COLOR]Not sure what "wmas" is. 

A quick look shows a radio station in Springfield Mass with those call letters, but no mention of a computer/playback media format...unless it means Windows Media Audio, then you just install the restricted codecs from 'Universe' (I believe).

What is it you are trying to play exactly? If it is something you downloaded from a "suspect" source, it might be one of those Windows specific chunks of malware that want you to "Install the correct codecs" or whatever and then infect your Windows machine.

---

### Post by mbaybarsk on 2009-08-28
I just had a .wmv file, a CBT video, there was no sound, so i opened "audio>track1" and tried to enable the sound. i got that error. 

After a few searches, i found that mplayer and some additional stuff fixed this. So i tried and it worked.

---

### Post by mapes12 on 2009-08-28
Go into Synaptic and install ubuntu-restricted-extras  

Then install the Medibuntu packages from here: [http://www.medibuntu.org/](http://www.medibuntu.org/)

If you're having problems after that then please post back.

---

### Post by abbaseo on 2010-02-05
> **mbaybarsk said:**
> I just had a .wmv file, a CBT video, there was no sound, so i opened "audio>track1" and tried to enable the sound. i got that error. 

After a few searches, i found that mplayer and some additional stuff fixed this. So i tried and it worked.

Hi please can you tell me what those additional stuff was. I am on ubuntu karmic and have installed mplayer and all the restricted packages still i only get the video with no sound on vlc and only sound with no video on mplayer.
thanks

---

### Post by Robster2 on 2010-02-05
Applications>Accessories>Terminal

Code: 

sudo apt-get install ubuntu-restricted-extras


Installs the video codecs restricted extras.

---

