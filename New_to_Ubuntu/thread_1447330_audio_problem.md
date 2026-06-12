---
title: "audio problem"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-04-05
i encountered some audio problem in kubuntu just now! if i play music in amarok i am not able to get the sound when i play youtube videos or if i play any other audio file in other music player !!!

i get this notification


[ATTACH]152395[/ATTACH]

---

### Post by 1991sudarshan on 2010-04-05
pls help me out!!!

---

### Post by stderr on 2010-04-05
I'm unused to Kubuntu, however does it help if you move Pulseaudio to the top of *all* the device preference lists? Pulseaudio is designed to handle and mix multiple audio sources.

edit: Please only create one thread per issue. [This thread]("http://ubuntuforums.org/showthread.php?t=1447334") is a unnecessary duplicate.

---

### Post by 1991sudarshan on 2010-04-05
so which one is the best pulse audio or the HDA intel audio analogue???

---

### Post by stderr on 2010-04-05
HDA intel audio is the device name of your onboard sound card. By the looks of things, it has both analogue and digital outputs, and you are only using the analogue ones. 

Generally speaking, you run everything through Pulseaudio, which mixes and ships the audio off to the correct device. If you choose not to run Pulseaudio (which is quite hard in K/Ubuntu - it's almost always running anyway) then you use a drop-in replacement such as ESD or ALSA. 

You should be running everything through Pulseaudio unless you have a good reason not to.

---

### Post by sandyd on 2010-04-05
you can also use dmix (depreciated) + alsa

---

