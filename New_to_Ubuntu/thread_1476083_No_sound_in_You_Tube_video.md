---
title: "No sound in You Tube video"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by Charlie Chick on 2010-05-07
Hello Everybody,

Just installed 10.04 on my Acer Travelmate 2410 laptop and have a curious problem: audio works fine for everything (including the mic which didn't work in 9.10) except sound embedded in videos. When I play them in any web browser the video works fine but there is no sound. I presume that this is a codec problem? 

I have ubuntu restricted extras installed as well as VLC.

Thanks.

---

### Post by stoogiebuncho on 2010-05-07
No offense, but it's always best to start with the stupid questions:

1) Is the volume on the youtube player (or other flash player) muted?

2) If you click on the volume icon on your panel and select "Sound Options", there's a tab for programs, check there to make sure the sound for your browser is not muted.

3) In past versions of Ubuntu I've sometimes noticed sound conflicts that cause a program to be muted.  Have you tried restarting, and then going to youtube before opening any other program to see if it works then?

Assuming that's all taken care of, are you running 64-bit or 32-bit?

---

### Post by Charlie Chick on 2010-05-07
> **stoogiebuncho said:**
> No offense, but it's always best to start with the stupid questions:

1) Is the volume on the youtube player (or other flash player) muted?

2) If you click on the volume icon on your panel and select "Sound Options", there's a tab for programs, check there to make sure the sound for your browser is not muted.

3) In past versions of Ubuntu I've sometimes noticed sound conflicts that cause a program to be muted.  Have you tried restarting, and then going to youtube before opening any other program to see if it works then?

Assuming that's all taken care of, are you running 64-bit or 32-bit?

Thanks for responding, I checked the volume on the You Tube window - that's at maximum, when running the video the sound option tab says that no program is running audio and I've tried re-starting, but all to no avail. I'm running 32 bit.

---

### Post by dracayr on 2010-05-07
is this only for flash vids or are normal videos muted too? what about System sounds, music files etc.
if everything is muted, first of all check if you can fix it by installing gnome-alsamixer and checking if an audio channel is muted.

---

### Post by Charlie Chick on 2010-05-07
It only applies to videos inside an browser, any browser. All other sound works OK.

---

### Post by sandyd on 2010-05-07
32/64bit?

---

### Post by dracayr on 2010-05-07
Do you have multiple soundcards? Flash 10 works only with the default ALSA sound card.

EDIT: for the pcm slider that chaosgrimm mentions in the post after this one, you'll have to install gnome-alsamixer

dracayr

---

### Post by chaosgrimm on 2010-05-07
One thing you may want to check is the mixer for your sound card. Not sure were it would be on Ubuntu though (Kubuntu you can access by clicking on the speaker in the notification area). Anyway, most have a PCM slider that is turned down all the way by default. If you find this you'll wanna turn it up.

---

### Post by biscombe on 2010-05-08
I too was having the same problem with YouTube (and presumably other Flash videos as well). Here's what I did to fix it:

1. Make sure you have the flashplugin-installer package installed.
2. In a terminal, do:
```
mkdir ~/.mozilla/plugins
ln -s -f /usr/lib/flashplugin-installer/libflashplayer.so ~/.mozilla/plugins/libflashplayer.so
```Hope that helps.

---

### Post by Charlie Chick on 2010-05-08
> **biscombe said:**
> I too was having the same problem with YouTube (and presumably other Flash videos as well). Here's what I did to fix it:

1. Make sure you have the flashplugin-installer package installed.
2. In a terminal, do:
```
mkdir ~/.mozilla/plugins
ln -s -f /usr/lib/flashplugin-installer/libflashplayer.so ~/.mozilla/plugins/libflashplayer.so
```Hope that helps.

Unfortunately, it didn't work for me. As I had everything important backed up I just re-installed 10.04 and now everything works!

Thanks to everyone who responded.

---

### Post by Jesua on 2010-05-25
I solved this issue reinstalling:

flashplugin-nonfree
flashplugin-installer

From Synaptic, the restart Firefox and the sound on YouTube is back...

---

### Post by craig.brisbane on 2010-07-31
ON FURTHER TESTING THIS DOES NOT APPEAR TO WORK FOR ME

I agree with Jesua, reinstalling ::

flashplugin-nonfree
flashplugin-installer

appears to work. I installed unbunt 10.04 and linux mint 9 several times as I could not figure out the issue as to why flash video in firefox would not work. 

It appears that if I use skype and then attempt to play a flash video it will not work, if I then reinstall lashplugin-nonfree  and flashplugin-installer I can again play flash video.

---

