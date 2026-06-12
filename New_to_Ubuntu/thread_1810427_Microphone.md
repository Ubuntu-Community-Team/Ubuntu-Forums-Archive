---
title: "Microphone"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by Savicava on 2011-07-23
External and internal microphones are recording my voice with scratchy sound using in-built sound recorder program or Skype just like in example downloaded from the link below:
[[COLOR=#0033aa]http://www.mediafire.com/?vks4druyv8wa43k[/COLOR]]("http://www.mediafire.com/?vks4druyv8wa43k")
PulseAudio input is used and don't know how to make those two programs use "HDA SIS966: ALC660-VD Analog (hw:0,0)" audio input and output which are working flawlessly when i record my voice in "Audacity" program version 1.3.12-beta with interface host set to ALSA just like in the MP3 sound example downloaded from the link below:
[[COLOR=#0033aa]http://www.mediafire.com/?e1hubfxdusbdq7r[/COLOR]]("http://www.mediafire.com/?e1hubfxdusbdq7r")
When setting "Audacity" playback and recording to default it is still good but not perfect because of little scratching like in the example below:
[[COLOR=#0033aa]http://www.mediafire.com/?dgg3bvislb151a7[/COLOR]]("http://www.mediafire.com/?dgg3bvislb151a7")
Same scratchy problem are encountered in Windows VIsta and Windows 7 both 32 and 64 bit but without the apropriate drivers.
I'm using ASUS X59SR-AP022 Notebook for over two years now and here are Ubuntu 10.04.2 informations from console command "alsamixer" below:
[[COLOR=#0033aa]http://www.mediafire.com/?tcehvjyvnc5v5b9[/COLOR]]("http://www.mediafire.com/?tcehvjyvnc5v5b9")

---

### Post by androssofer on 2011-07-23
if u open sound preferences and select the input tab do u have more than 1 option? 

also if u open terminal and type:

```
alsamixer
```

i think u can select which microphone to use... (i only have 1 mic so cant confirm...)

aside from tht it might b time to play with asound.conf... i'v been tweaking mine recently to get HDMI sound, so i know some stuff, lets hope its usefull..(assuming u dnt already know lots about asound.conf...) haha. gotta rush off to work now :(, but when i get home and will look into tweaking asound.conf for mic's and we can fumble thru it together :). 

assuming no1 comes on the interim who actually knows about asound.conf for mics?... any1?

---

### Post by Savicava on 2011-07-23
> **androssofer said:**
> if u open sound preferences and select the input tab do u have more than 1 option? 

also if u open terminal and type:

```
alsamixer
```

i think u can select which microphone to use... (i only have 1 mic so cant confirm...)

aside from tht it might b time to play with asound.conf... i'v been tweaking mine recently to get HDMI sound, so i know some stuff, lets hope its usefull..(assuming u dnt already know lots about asound.conf...) haha. gotta rush off to work now :(, but when i get home and will look into tweaking asound.conf for mic's and we can fumble thru it together :). 

assuming no1 comes on the interim who actually knows about asound.conf for mics?... any1?
Thanks for your quick reply!
In the input tab of sound preferences there is only "Internal Audio Analog Stereo" to choose.
Here is the picture:"http://www.mediafire.com/i/?65f40bj2bgh2vep".
Can't find a way to choose which microphone to use but that is automatic and working good anyway.

---

### Post by Savicava on 2011-08-08
With the help from the thread on the link below i am now convinced what is the problem:

[http://ubuntuforums.org/showthread.php?t=1317483](http://ubuntuforums.org/showthread.php?t=1317483)

It is needed that the microphone input is set to appropriate input like i did in the Audacity, but i didn't know how to do it in the Skype version 2.2.0.35 for the was only "PulseAudio server (loacal)"  option in the "Sound Devices" settings for microphone, speakers and ringing.

In the Skype version 2.0.0.72 i can set my audio input and output to:
"Default device (default)"
"HDA SIS966 (hw:SIS966,0)"
"HDA SIS966 (plughw:SIS966,0)
"hdmi"
"rawbluetooth"
"pulse"

**Important**: Note that sound in the portable Skype 2.0.0.72  from the link below worked for me only with regular Skype 2.2.0.35 installed.

[http://linux.softpedia.com/get/Communications/Chat/Skype-Portable-49021.shtml](http://linux.softpedia.com/get/Communications/Chat/Skype-Portable-49021.shtml)

Although it is not perfect, i can finally talk with friends and expect a good stable version of Skype in the future of Ubuntu!

---

### Post by Savicava on 2011-08-10
I finally managed to make in-built sound recorder program record my voice perfectly by setting appropriate sound devices in the menu accessed using the command below which opes Multimedia Systems selector:

**gstreamer-properties**

---

### Post by elisiariocouto on 2012-03-19
HOLY JESUS! THANKS, FINALLY!

Uff, I've been searching for this workaround for so many times, thanks mate :D

---

