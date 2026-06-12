---
title: "No sound from movies"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by Mariane on 2011-02-20
Fresh install of Kubuntu 10.04

At first the sound did not function. In my "System settings/Multimedia" 3 options are displayed:

1) HDA Intel (ALC883 Analog)
2) Jack Audio Connection Kit
3) Playback/recording through the PulseAudio sound server

1 was the default. It did not work. I switched to 2 and there was sound. Amarok played fine. Then I added some packages to watch a video with vlc. vlc shows the pictures but plays no sound. 

Now when I go to "System settings/Multimedia" it tells me 1 functions (I can hear it when I click on "test" but 2 does not function. But whichever I choose there is still no sound from vlc (nor from the other movie players). 

As I tuned Amarok equaliser and saved the settings, could it have grabbed the sound device somehow? Because when I open the movie file with Amarok I can hear the sound of it. 

Mariane

---

### Post by Hedgehog1 on 2011-02-20
> **Mariane said:**
>  Then I added some packages to watch a video with vlc. vlc shows the pictures but plays no sound. 
Mariane

Mariane,

VLC can support more styles of audio - I have found some videos (particularly those with AC3 audio) need to be stepped down for some audio cards.

To test this wild theory, play a move that is not giving sound in VLC using VLC, then from the audio menu in VLC try selecting another audio track.

This is my best guess (for now) based on what you described.

:KS

---

### Post by Mariane on 2011-02-22
Thank you Hedgehog1, but it didn't work. 

I ripped the dvd, because this sometimes makes unplayable DVD playable, to no avail. Now there's only the choice of a single audio channel and when I do "Audio - visualise" the sound is displayed. So vlc can read the sound but cannot send it to the laptop speakers. 

Mariane

---

### Post by mastablasta on 2011-02-22
10.04, HDA Intel....all this points to
 
...try upgrading ALSA by following this guide: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
 
There is a buig with these realtek/intel hda chips. at least now it's priority is medium, though i wish it was very extremely super high must be solved by tomorrow 12:00 :-D
 
Alsa 1.0.23 you are upgrading to is probably preety stable as Debian uses it in its latest Stable version.

---

### Post by Mariane on 2011-02-23
Everything compiled fine but I still have no sound from vlc. 

Mariane

---

### Post by Perfect Storm on 2011-02-23
Have you tried change the audio settings in VLC? It could be that VLC is pointing to a wrong audio server/engine.

---

### Post by Mariane on 2011-02-23
In my home/user directory I had a directory named .pulse. As I know pulse-audio causes nothing but problems on this machine I renamed it to save.pulse.

Now the sound is fine.

Next time I have sound problems I'll look for anything even remotely related to *** pulse-audio and delete them straight away  :mrgreen:

Mariane

---

### Post by mastablasta on 2011-02-24
you could have just told VLC to use ALSA  i believe.

---

### Post by Mariane on 2011-06-04
Then I might have had problems with other programs, or it might have reinstalled itself next time I rebooted... Better be safe ;) 

Mariane

---

