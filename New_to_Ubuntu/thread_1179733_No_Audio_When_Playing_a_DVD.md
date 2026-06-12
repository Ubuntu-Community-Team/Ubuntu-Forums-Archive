---
title: "No Audio When Playing a DVD"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by MoonWolf85 on 2009-06-06
So I just downloaded all the Medubuntu repos and then got libdvdcss2 and all the gstreamer stuff... And I finally can play a dvd on my laptop... However there is no sound. But when I play my pandora radio station, I have sound. And the VLC Media player that I'm using isn't on mute or anything that I can tell. 

Help?

---

### Post by uberlube on 2009-06-06
launch VLC from the terminal and inspect the readout. It should give u an idea as to where o start looking. Im assuming though that its prolly a missing codec that hasnt been installed yet.

---

### Post by MoonWolf85 on 2009-06-06
I'm going to sound like an idiot, I know it... 

How do you do any of what you just said?

---

### Post by uberlube on 2009-06-06
The terminal is found under Applications/Accessories in your menu. It gives you the power to operate your OS through the command line. This program will be your friend through your whole Linux experience so it is best to get to know it as much as possible. Here is a good knowledge base:
[http://www.linuxcommand.org/index.php]("http://www.linuxcommand.org/index.php")

Once you have it open type in vlc and press enter. It will open the application and will give you a readout of how it was launched. Copy and paste that readout in your next post.

---

### Post by MoonWolf85 on 2009-06-06
jen@robbie-laptop:~$ vlc
VLC media player 0.8.6e Janus


That's all it said.

---

### Post by MoonWolf85 on 2009-06-06
When I opened the DVD in VLC, all this appeared in the terminal... 

VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: TAKEN
libdvdnav: DVD Serial Number: 3A747E97
libdvdnav: DVD Title (Alternative): TAKEN
libdvdnav: Unable to find map file '/home/jen/.dvdnav/TAKEN.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000004a7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004ac
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00000568
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0000118c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00002914
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00007417
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002b610c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002e31ef
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
[00000343] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000

---

### Post by uberlube on 2009-06-06
Ya that would be the DRM at work. Are you sure that u have libdvdcss installed? Also u should run threw [this]("http://www.psychocats.net/ubuntu/nonfree") if u havent already.

---

### Post by MoonWolf85 on 2009-06-06
I did this from the Medibuntu site. 

**With the entire Medibuntu repository**

 If you have added the entire Medibuntu repository, you just need to install the package using APT: 
sudo apt-get install libdvdcss2  
[B]
[/B]

---

### Post by uberlube on 2009-06-06
yerp

---

### Post by MoonWolf85 on 2009-06-06
I went through and did all the things I was told to do here. [http://ubuntuforums.org/showthread.php?t=1163173](http://ubuntuforums.org/showthread.php?t=1163173)

Namely, this stuff... 

If you couldn't find libdvdcss2, then it's likely that you don't have the extra repository set-up properly (per Nightwishe's note). Kindly read that link again, about how to add 3rd party repositories like Medibuntu, and after adding that, you have to refresh the synaptic db. If I recall right, the 3 basic packages I've always installed to get full DVD playability are:
- w32codecs (or sometimes called win32codecs or win32all),
- libdvdread3
- libdvdcss2

I'm just not sure what I need to type in terminal to try uninstalling VLC and then reinstall it in the new environment.

---

### Post by MoonWolf85 on 2009-06-06
Well I figured out how to unstall and then reinstalled VLC and still no audio. What codec could I be missing? I have w32Codecs, libdvdread3, libdvdcss2. Those are all the things I was told to get.

---

### Post by uberlube on 2009-06-06
Ok so im assuming that libdvdcss is installed and u can see the video playing in VLC, just no sound right. U shouldnt have to uninstall vlc to get it to work properly. Im still thinking that u need to install the ubuntu-restricted-extras which houses all of the audio codecs that u need to get your sound working (Wether it be listening to audio on a dvd or listening to an mp3). There are a million threads in this forum to get these codecs installed so i believe that this is where u should head from here. Unless im wrong about your situation.

---

### Post by uberlube on 2009-06-06
Sorry i posted the wrong link earlier try [this]("http://www.psychocats.net/ubuntu/mp3") out instead.

---

### Post by MoonWolf85 on 2009-06-06
Yes, video, just no sound. 

I do have Ubuntu-restricted-extras installed. And since I installed it I've been having problems listening to mp3's that I've downloaded using frostwire, but that is rather besides the point.

---

### Post by uberlube on 2009-06-06
Thats definitely your problem then if u are having issues even listening to mp3's. The codecs for them are one and the same as the ones for watching dvd's. Give me a few and ill get back to u with some more info on installing these. I havent had to in a very long time.

---

### Post by MoonWolf85 on 2009-06-06
Thank you

---

### Post by uberlube on 2009-06-06
[https://help.ubuntu.com/community/RestrictedFormats/#Audio](https://help.ubuntu.com/community/RestrictedFormats/#Audio)

go threw that and see if there is anything in there that u havent done yet

---

### Post by MoonWolf85 on 2009-06-06
This might sound dumb, but I was reading the stuff in the link you just gave me and recalled this from a different problem I was having. 

Have you installed all of the extras needed for playing DVD's? Start by adding (via the package manager) ubuntu-restricted-extras, and the gstreamer good/bad/ugly sets.

This might sound really dumb, but I couldn't find any gstreamer good/bad/ugly sets. I don't even know what that person was talking about. Could that be the problem?

---

### Post by mc4man on 2009-06-06
It's been quite awhile since i used vlc 0.8.6 but 90% of the time having no audio in vlc can be solved by opening vlc -> settings -> preferences -> click on advanced options -> audio -> highlight output modules and in drop down on the right side change from default to alsa ....

make sure you click on save before exiting the settings menu

if you have any navigation issues on the dvd

Right click on Applications -> edit menus. In the pop up highlight Sound & Video, on the right side screen right click on vlc -> properties. If the command is vlc %U change it to this 

```
vlc %f
```

---

### Post by MoonWolf85 on 2009-06-06
> **mc4man said:**
> It's been quite awhile since i used vlc 0.8.6 but 90% of the time having no audio in vlc can be solved by opening vlc -> settings -> preferences -> click on advanced options -> audio -> highlight output modules and in drop down on the right side change from default to alsa ....

make sure you click on save before exiting the settings menu


Um... wow... That worked. So simple. 

Thank you both very much for all the help! Extra thanks to Uberlube for being very patient with me and trying so hard. Thank you.

---

### Post by uberlube on 2009-06-06
np. i knew it had to be something real simple.

---

