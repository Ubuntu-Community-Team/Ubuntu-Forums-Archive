---
title: "HP dv3-2155 sound problems"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by joebix on 2009-11-21
Hi everyone!

I am a beginner in the ubuntu world. I have just installled ubuntu 9.10 on my laptop (HP dv3-2155), but don't have the sound on it.

I have tried many kind of commands, but nothing is working!

When I switch to vista, the sound is perfect though! I would like to stop switching to vista and use only ubuntu.

Please, can somebody help me to solve this issue?Thanks in advance!

JB

---

### Post by amalgamut on 2009-12-18
I have the same problem with my new HP dv3-2250es. I tried ubuntu 8.04 and it is even worse. 

I can hear the sound when the login screen appears and after that, the little intro music. But once the system has started I can't hear music, movies or flash sound like in youtube videos.

I checked the volume with alsamixer and seems to be fine.

I upgraded my alsa driver to the last version.

¿What else can I do?

---

### Post by amalgamut on 2009-12-20
Hello!

I have good news!
I just solved my problems with sound in ubuntu 9.10 in my HP dv3-2250es

Here's what I did:

1. Download and install the last alsa drivers (I am not sure if this step is needed).
2. Add this line to "/etc/modprobe.d/alsa-base.conf":

    options snd_hda_intel model=hp-dv5 

#Notice the model is not dv3 but dv5

3. Restart alsa with command:
    
    > sudo alsa reload

In my sound preferences i set the device to "analog stereo duplex".

---

### Post by teonghan on 2010-04-03
Thank joebix, was helping friend to install Karmic on his DV3, and your tip works like a charm!

---

### Post by pekino on 2010-04-04
This solution works for me on ubuntu 9.10 in my pavilion dv3

---

### Post by harry35 on 2010-04-05
Hi everyone,

I'm having the same sound problem with my HP G71-340US laptop. No sound at all, not even when Ubuntu boots up. I'm dual booting this machine, Win7 and Ubuntu 9.10. Under Win7, the sound works fine, but not with Ubuntu. 

I couldn't understand the above suggestions on how to cure the previous poster's sound problems, or how to translate them to my computer. I was trying to use rythmbox rather than alsa, but I did download alsa and install it, but it doesn't work either.

What does the above advice mean?

Add this line to "/etc/modprobe.d/alsa-base.conf":
options snd_hda_intel model=hp-dv5 

Is this something I should type into the command line in the terminal if I had a hp-dv3 machine? It looks like the first line above is the poster's normal command line and the second line the actual command. And should I have some or all of those directories on my machine?

I probably need some other command for my HP-G71, but how do I figure out what it is? 

Thanks for any help on this. As you can tell, I'm an ultranoob with linux, although I did know how to use the DOS command line some years ago before Windows came along.

One other comment, I was able to load Ubuntu successfully on my Toshiba A105 laptop without any sound problems.

---

### Post by amalgamut on 2010-06-17
> 
What does the above advice mean?

Add this line to "/etc/modprobe.d/alsa-base.conf":
options snd_hda_intel model=hp-dv5 
It means you should have a file called "alsa-base.conf" in the folder "/etc/modprobe.d/".
You have to edit that file with a text editor and add the line "options snd_hda_intel model=hp-dv5" to it (without quotation marks).

Good luck!

By the way, have anyone tried the sound in ubuntu 10.4?

---

