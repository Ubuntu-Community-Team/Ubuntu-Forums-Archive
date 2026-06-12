---
title: "gtk-recordmydesktop video playback is too fast"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by CJay554 on 2010-05-01
Hey everyone i wasn't quite sure where to post this under, im not completely sure if its a hardware issue or a program issue. But when i record a video with anything over 7 frames per second in gtk-recordmydesktop the video playback after the recording move 2x or more the speed it should be. While the voice itself plays in a good pace. 


Also, I use the "Encode on the Fly" option, without this option my video is horribly choppy but it works at regular pace. In this sense it may seem like a Video Driver fault, or even maybe my processor can't keep up?
heres my video lshw entry: 

```
-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:30 memory:fc100000-fc1fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
```

Also my audio:

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
             resources: irq:22 memory:fc300000-fc303fff
```

If anyone has any idea what could be the problem please please please help! I'm trying to make high quality videos for my Ubuntu Lost Videos youtube channel but its kind of a bummer when the system your working on gives you these problems...

---

### Post by sylanor on 2010-05-09
Hi !! 

I have exactly the same problem... On my laptop with my geforce 103m and on my desktop-pc with his Ati 4870x2. I think the problem is not from the gpu. But i've no idea from where... 

If someone has a solution , thanks for helping us !

Thanks ! :)

---

### Post by CJay554 on 2010-05-10
bump

---

### Post by sylanor on 2010-05-11
BUMP too ^^ !

---

### Post by elliotn on 2010-05-11
i have neva manage to record my vids with sound

bump

---

### Post by sylanor on 2010-05-11
What's the complete program's name ? "Neva manage" ? I can't find it on the repository and on the internet... thanks for helping.

---

### Post by Neovos on 2010-05-16
> **sylanor said:**
> What's the complete program's name ? "Neva manage" ? I can't find it on the repository and on the internet... thanks for helping.

I think he was saying that he "never managed" to get it working with video and sound altogether :lol:

---

### Post by Tinooz on 2010-08-30
The video is too slow because, during the recording, your computer is too slow to record and compress the requested number of frames per second. When the computer can only manage, say, 5 frames per second but you requested 20, the video will run 4 times too fast. 

The solution is to reduce the requested number of frames per second, (in the advanced section of the options), or use 'no compression'.

---

### Post by Pampanga on 2010-09-26
> **Tinooz said:**
> The video is too slow because, during the recording, your computer is too slow to record and compress the requested number of frames per second. When the computer can only manage, say, 5 frames per second but you requested 20, the video will run 4 times too fast. 

The solution is to reduce the requested number of frames per second, (in the advanced section of the options), or use 'no compression'.

Works like a charm!:P I had it as "Encode On The Fly" but changed it to 'Zero Compression'. Although it takes a while to encode after recording, at least now it work as it suppose to be.

Thank you very much...:guitar:

---

### Post by julio prada on 2011-01-21
I lowered the frame per second to 6, unchecked  Zero compression, checked quick subsampling and finally the video is in normal speed and in perfect sync with audio.
Looks like my Intel P6100 is not able to encode my 1366*768 screen on time and was loosing lots of frames.
I did not notice any change to the video quality for what I am doing.
Thanks Tinooz and all...

---

### Post by Pithikos on 2011-10-04
Any idea on how to fix the video to match the sound. I recorded 10 mins of tutoring and would prefer to fix the video as it already took me 2 hours to get the video perfect(though then I noticed that the video was fastforwarding).

---

### Post by mehdieft on 2012-02-21
> **Pithikos said:**
> Any idea on how to fix the video to match the sound. I recorded 10 mins of tutoring and would prefer to fix the video as it already took me 2 hours to get the video perfect(though then I noticed that the video was fastforwarding).
Hi
on the Advanced Menu change the following Setting
Performance\Frame per Second = 10
enable the following option:
1-encode on fly
2-zero compression
3-quick subsampling
4- full shot at every frame

---

### Post by dvdkon on 2013-04-12
I think that lowering the video quality will reduce the CPU usage by the compression, so it will not skip frames
(I know this is an old post, I wrote this for possible future visitors)

---

### Post by wildmanne39 on 2013-04-12
Thread closed. Please do not post in old threads.

---

