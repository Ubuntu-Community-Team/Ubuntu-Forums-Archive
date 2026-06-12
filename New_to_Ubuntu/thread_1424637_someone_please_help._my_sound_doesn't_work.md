---
title: "someone please help. my sound doesn't work?"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by narutarded on 2010-03-08
[FONT=Microsoft Sans Serif][SIZE=2]i have ubuntu 8.10 on a dell laptop and intel for sound. my sound has not worked before. i found this site and it helped me the last times my sound wouldn't work. here's the link- 
[http://forums.lenovo.com/t5/Lenovo-3000-and-Value-line/Linux-Ubuntu-Sound-Problems-Semi-Resolved-for-Lenovo-3000-Y410/m-p/62121](http://forums.lenovo.com/t5/Lenovo-3000-and-Value-line/Linux-Ubuntu-Sound-Problems-Semi-Resolved-for-Lenovo-3000-Y410/m-p/62121)

but now when ever i try to type in: 
[/SIZE][/FONT][FONT=Microsoft Sans Serif][SIZE=2]sudo nano /etc/modprobe.d/alsa-base

the termenal says this:

GNU  nano  2.0.7        File:   [/SIZE][/FONT][FONT=Microsoft Sans Serif][SIZE=2]/etc/modprobe.d/alsa-base

it doesn't work anymore. how can i fix/make my sound work again?


[/SIZE][/FONT][FONT=Microsoft Sans Serif][SIZE=2] [/SIZE][/FONT]

---

### Post by Elfy on 2010-03-08
It's waiting for you to finish editing the file

---

### Post by narutarded on 2010-03-10
what do you mean finish editing? i'm not sure what to do...

---

### Post by Soulcage on 2010-03-10
Try sudo gedit /etc/modprobe.d/alsa-base instead

---

### Post by narutarded on 2010-03-11
[SIZE=2]ok so i upgraded my computer with the update manager for ubuntu 9.04 packages thinking that it might be able to fix my sound last night, but no. the sound icon on my toolbar does not work. when i click it, it says: "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured. You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."where can i install the right GStreamer plugins so my sound works??? plus firefox has been freezing up on me for the past half hour, do you know how to fix this???[/SIZE]

---

### Post by bumanie on 2010-03-11
In 9.04, gstreamer should be in restricted extras - [go here]("https://help.ubuntu.com/community/RestrictedFormats") - I think it includes gstreamer stuff.

---

### Post by narutarded on 2010-03-11
i installed all the restricted stuff but it still doesn't work and says the same thing still.

---

### Post by narutarded on 2010-03-14
ok people i think i just found the problem...to my problem. when i went on sound to toggle with some stuff i notice that under defualt track mixer there isn;t any devices to select. first, why aren't there any device selections? where did they go? second, where can i down load a device for ALSA, OSS, or for PulseAudio? thnx! :)

---

