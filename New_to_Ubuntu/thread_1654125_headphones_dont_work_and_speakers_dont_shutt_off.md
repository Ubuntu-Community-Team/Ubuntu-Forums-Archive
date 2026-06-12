---
title: "headphones dont work and speakers dont shutt off"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by philipballew on 2010-12-27
my laptop with a hda intell sound set up will not work with the headphones when their plugged in. basically they dont make sound and the speakers keep making noise. im running ubuntu 10.10.

---

### Post by Bucky Ball on 2010-12-27
USB headphones or regular mini-jack?

You should have like a plug and cable icon in top toolbar for pulse audio. Plug in headphones and click that icon. Open 'Volume Manager'.

Get an audio stream going (play some music). That should appear in the 'Playback' window of the Volume Manager. 

Now, right click on that stream and see where it is heading. I'd say it is heading for the speakers. Change it to the other option there, which is no doubt the headphones.

Good luck.

---

### Post by philipballew on 2010-12-28
i believe its running alsa

---

### Post by Bucky Ball on 2010-12-28
Unless you've uninstalled pulse, not the case, although you may have the gnome-alsamixer icon in the toolbar. Make sure nothing's muted in there if so and play with the levels, but guess you already have.

---

### Post by philipballew on 2010-12-28
wheres volume manager?

---

### Post by philipballew on 2010-12-29
anyone? its running alsa and i need to get this working?

---

### Post by philipballew on 2011-01-02
anyone?

---

### Post by philipballew on 2011-01-03
anyone?

---

### Post by Bucky Ball on 2011-01-03
Have you got gnome-alsamixer installed? If not install it. Available in Synaptics.

Check in there if anything is muted or volume down.

Could you run this in a terminal and post the results:

```
cat /proc/asound/version
```

To answer the other question:

Applications->Sound and Video->Pulseaudio Volume Control.

An icon will appear in your top taskbar. Click it and choose Volume Control. 

Get an audio stream going (play some music) and it will appear in the 'Playback Streams' window. Right click on it and you should be able to send it to whatever device you like. If your setup is different check 'Output' and see if you can tweak a fix there.

---

### Post by vivek.pandey on 2011-01-03
> **philipballew said:**
> my laptop with a hda intell sound set up will not work with the headphones when their plugged in. basically they dont make sound and the speakers keep making noise. im running ubuntu 10.10.

try this.. go to sound prefernces->output->connector and change it to analog headphones.. see if the prob is know solved

---

### Post by philipballew on 2011-01-03
the command shows this: Advanced Linux Sound Architecture Driver Version 1.0.23.
i believe im running alsa and not pulse so volume manager is not installed

here is a screenshot showing alsa mixer and how i dont even see an option for headphones. and here is the sound preferences output tab with no real way to change it to headphone

---

### Post by philipballew on 2011-01-04
anyone?

---

### Post by Bucky Ball on 2011-01-04
This is odd. Pulse audio is the default in Maverick. alsa is loaded too and they work together. Try this. Open Synaptics, search for:

pulseaudio

What you got? Is a package by that exact name installed?

Also, search for:

gnome-alsamixer

Is that installed?

Seems that 10.10 works fine on some machines, on others it's buggy. I am only using it because very new machine and only kernel this machine will run on. I would otherwise recommend the LTS release, 10.04

---

### Post by philipballew on 2011-01-04
i just did, there both installed. i dicieded to upgrade the drivers and its fixed!

---

### Post by Bucky Ball on 2011-01-04
Way to go! Great news. That's the learning curve for you.

You should have 'Pulse Audio Manager' or something like that under Applications->Sound and Video (sorry, in Xfce at the moment which is slightly different). If you click that, you will get an icon that looks like a mic and cable in the top taskbar. That is what I've been banging on about.

You have a few options from there. :)

There is also a more human gui for alsamixer also. I will report back when on my desktop.

Enjoy! Please mark thread as 'Solved' using 'Thread Tools'.

---

### Post by bloodychaos on 2011-02-07
My search brought me here, and well, I'm having similar problem with my desktop and rather not make new thread.

In my case, whenever I plug in my headphones, the system will just mute itself. I have to then unmute it. Once I unmute, the speakers and headphones will both play sound (or music if I'm playing any) and I have to manually set output as 'Analog Headphones' so that it'll play through the headphones only.

Currently using a 64bit of 10.10 and 'cat /proc/asound/version' gave me the following. In case it's needed, it's a VIA soundcard
```
Advanced Linux Sound Architecture Driver Version 1.0.23.

```

At the software center I searched for 'pulseaudio' and 'gnome-alsamixer', seems like neither of the softwares are installed. Tried installing both softwares but no go.

I used 9.10 before, but I didn't have problem with the audio jacks. I kinda formatted the previous installation and did a fresh install for 10.10. Anyways, any chance for me to fix this?

---

### Post by philipballew on 2011-02-07
if you type alsamixer in the terminal is the headphone jack muted? or not even there? if your confused about that show a screenshot with the app in the terminal running.

---

### Post by Bucky Ball on 2011-02-07
> **bloodychaos said:**
> My search brought me here, and well, I'm having similar problem with my desktop and rather not make new thread.

In my case, whenever I plug in my headphones, the system will just mute itself. I have to then unmute it. Once I unmute, the speakers and headphones will both play sound (or music if I'm playing any) and I have to manually set output as 'Analog Headphones' so that it'll play through the headphones only.

Currently using a 64bit of 10.10 and 'cat /proc/asound/version' gave me the following. In case it's needed, it's a VIA soundcard
```
Advanced Linux Sound Architecture Driver Version 1.0.23.

```At the software center I searched for 'pulseaudio' and 'gnome-alsamixer', seems like neither of the softwares are installed. Tried installing both softwares but no go.

I used 9.10 before, but I didn't have problem with the audio jacks. I kinda formatted the previous installation and did a fresh install for 10.10. Anyways, any chance for me to fix this?

You will get more attention and specific help if you post a new thread with a title describing your exact problem. You are buried in a solved thread here and your chances of being noticed and consequently helped are slim. ;)

---

### Post by philipballew on 2011-02-07
this is true. only me and Bucky Ball are probably subscribing.if its even a little bit of a different problem, theres room for a new thread.

---

### Post by bloodychaos on 2011-02-08
@Bucky Ball & philipballew

Thanks for the reply. 'alsamixer' gave the following (attached image)

Also, I've opened up a [new thread]("http://ubuntuforums.org/showthread.php?p=10439034") as recommended. Kinda copied pasted everything from the previous post:popcorn:

---

