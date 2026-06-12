---
title: "i cant watching videos and listen music at the same time"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by kiraku on 2009-12-21
hi:

after update to 9.10. i cant listen music (with amarok or any reproducer) and watch videos at the same time (mplayer, vlc, etc)...

if im listenig music, when i launch a video, this stay freezed at the beginning, and when i close amarok (not any other way) it start playing, this with mplayer... with vlc, i can watch the video but with no sound...

so, any ideas of what could it be????

---

### Post by LuisGMarine on 2009-12-21
There seems to be a problem with your sound mixing.  In other words more than one application having access to your sound card.  The best recommendation that I can think of is navigate to where ever you get to pick you sound driver and change it to ALSA since I know ALSA supports sound mixing.

For Example:

If you open up VLC. Click on Tools > Preferences.  Then if you click on the Audio icon and change the  "Output" to ALSA audio output, it would take care of 1/2 of the problem.  Now you just need to figure out how to do the same thing in Amarok.  I run ubuntu, so I do not have Amarok installed to guide you through it.  

Try it and see if that might work.

---

### Post by kiraku on 2009-12-21
hi...

i have done both: alsa in vlc and amarok... and the problem persist...

---

### Post by LuisGMarine on 2009-12-21
What is the output when you run this command?
```

sudo lshw -C multimedia
```

---

### Post by kiraku on 2009-12-21
it give me this:

```
*-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:52400000-52403fff
```

---

### Post by LuisGMarine on 2009-12-21
what is the make and model of your computer?

---

### Post by kiraku on 2009-12-21
i have a compaq presario c700, 1Gb ram, intel pentium dual core processor of 1.46 Ghz each and 120 Gb HD...

---

### Post by kiraku on 2009-12-22
> **LuisGMarine said:**
> What is the output when you run this command?
```

sudo lshw -C multimedia
```

why do you want to know this??

---

### Post by lotharmat on 2009-12-22
> **kiraku said:**
> why do you want to know this??

To see what multimedia your PC employs!

---

### Post by Captain_tux on 2009-12-22
> **kiraku said:**
> why do you want to know this??

To see if Ubuntu recognizes your hardware... you don't have to let us know, but then we'd won't be able to help.

---

### Post by LuisGMarine on 2009-12-22
Best bet is to research your sound card with "audio mixing" or "software mixing" and see what comes up on google.  I'm currently home for the holidays so I don't have my Ubuntu computer to mess around with.

---

### Post by kiraku on 2009-12-23
> **Captain_tux said:**
> To see if Ubuntu recognizes your hardware... you don't have to let us know, but then we'd won't be able to help.

i guess that what i want to ask was what does that command do...

---

