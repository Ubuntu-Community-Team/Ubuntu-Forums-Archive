---
title: "Broken the sound - not sure why"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by zcacogp on 2010-07-05
Chaps, 

Sound on my desktop machine no longer works. Let me explain. 

1. I built it (10.04 lucid) about a month ago, and it worked very well. BUT I lost the library in Amarok everytime I closed it down (as per this thread: 

[http://ubuntuforums.org/showthread.php?t=1518936](http://ubuntuforums.org/showthread.php?t=1518936).) 

2. As suggested in the thread above, I did the following: ```
sudo apt-get install mysql-server-core-5.1
```

It fixed the Amarok problem, but broke the sound output. 

3. I removed the installation I did above (i.e. typed ```
sudo apt-get remove mysql-server-core-5.1
```), but it made no difference. 

4. Following the instructions in the "Comprehensive Sound Problem Solution Guide" (here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)), I still can't make it work. 

```
aplay -l
```
gives this: 
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I have tried the section detailing how to get the ALSA drivers from a fresh kernel, and while all parts complete fine it still won't play any sound. 

I can type ```
alsamixer
``` into the terminal, and find that I seem to have three soudn cards (I'm not sure how I manage this.) They are '- (default)', '0 HDA ATI SB' and '1 HDA ATI HDMI'. I can see the levels in each of these, and none of them are muted. 

A little bit more about the symptoms: there is no volume icon in the top right hand corner of the screen, and if I open something that makes noise (Audacity, for instance), it won't make any noise. However, in Audacity, the position indicator skips along the track about 3 or 4 times quicker than it should, suggesting that there is more of a problem than simply that the sound is muted. (I have the playback speed set to 1.0, so it isn't this.) 

I'd welcome any suggestions as I am not getting anywhere on my own at the moment. 

All help welcomed - thanks. 


Oli. 

P.S. I think the hardware is all OK; if I boot the machine into Windows then sound works fine.

---

### Post by zcacogp on 2010-07-05
OK, some progress. I don't fully understand what I am doing, but I updated ALSA to version 1.0.23, from the instructions here: 

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

I can now get sound out of the machine - it will play system noises (the drum-roll on login, for instance), and it will also play sound fine from Audacity. 

In the process of updating ALSA, I as told that I have three soundcards on the machine, as follows: 

1. hda-intel ATI Technologies Inc SBx00 Azalia (Intel HD9)
2. hda-intel ATI Technologies Inc RS780 Azalia Controller
3. Legacy Probe legacy ISA (non-PnP) Chips

All well and good. **But** ... 

I have uninstalled and re-installed Amarok (I thought it was the cause of the problem) and this now doesn't work. When it starts, it tells me that  KDE thinks that certain devices have been removed, and would I like the system to forget about them? When I click "manage devices" I am shown the same screen as if I click "Configure Phonon", which has a number of devices greyed out, as per this screenshot. 

[IMG]http://i76.photobucket.com/albums/j14/zcacogp/Screenshot-SoundSystem-Amarok.png[/IMG]

Also, when I click "Test" for any one of them, no noise is made. 

I don't understand what I am looking at here, but can anyone help me with why several of these devices are greyed-out (they weren't before the problems started), and what I can do to get them back?

I understand that ALSA is the system that communicates with the soundcards, and that Pulseaudio runs on top of ALSA as a sound server (I understand I am running Pulseaudio as well), but that Phonon also runs on top of ALSA and can't get control of it when Pulseaudio is running, but I don't understand the details of this or how it affects me. I also don't understand how I can have three sound cards, or what the list of things in the screenshot above are. I also don;t understand how OSS comes into the picture, or whether I am running it. (If anyone has any links to some pages which explain this sort of thing then I'd be grateful - thanks. I've tried googling but nowhere seems to explain it in simple terms.) 

All help will be welcomed. As I said, sound has worked fine on this machine before so I know it can be achieved again. Hopefully without having to rebuild Ubuntu from scratch tho'!

Thanks very much, in advance, for any help you can give. 


Oli.

ETA: I'm running 10.04 Lucid, and the only sound cards I am aware of are part of the ATI motherboard - there are no extra sound cards plugged into the machine.

---

### Post by lidex on 2010-07-07
Try this for amarok:
```
sudo apt-get install --reinstall phonon-backend-xine libxine1-ffmpeg
```
I could use some system info. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

Are you able to get sound from gstreamer apps? ie: rhythmbox, exaile, etc

---

### Post by zcacogp on 2010-07-07
Lidex, 

Aaagh! I have just (well, about an hour ago), rebuilt the machine ... I am currently re-installing all the bits that I am used to having! And (thus far), it all looks as if it is working as it should. 

Alas. However, that notwithstanding, many thanks for your help - it is appreciated. And I'm sorry I reached for the rebuild disk sooner rather than later. 

Thanks. 


Oli.

---

