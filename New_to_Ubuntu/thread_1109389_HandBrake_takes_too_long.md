---
title: "HandBrake takes too long"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by lil_kid1333 on 2009-03-28
I'm currently using HandBrake to rip and convert a movie to mp4 but damn its taking WAY to long its says ETA 9 hrs and god damn its gonna kill my PC T_T

anyone know why it's taking so long or any way of making it go faster? maybe I don't got the right codecs but im sure I installed the Gstreamer codecs...

---

### Post by cwsnyder on 2009-03-28
Converting video is _very memory intensive_ and also demands a very fast mass storage.  Tips for speeding up conversion, besides moving to a faster, multi-core processor?  Stuff in at minimum 3G of RAM in your machine and convert the video to your internal hard drive, not an external hard drive.  You can move it to an external drive later, but you _need_ the extra speed during the conversion process.

The better the resolution of the copy you are trying to make, the longer and longer it is going to take, relative to the length of the movie.

---

### Post by lil_kid1333 on 2009-03-28
> **cwsnyder said:**
> Converting video is _very memory intensive_ and also demands a very fast mass storage.  Tips for speeding up conversion, besides moving to a faster, multi-core processor?  Stuff in at minimum 3G of RAM in your machine and convert the video to your internal hard drive, not an external hard drive.  You can move it to an external drive later, but you _need_ the extra speed during the conversion process.

The better the resolution of the copy you are trying to make, the longer and longer it is going to take, relative to the length of the movie.

oh man I only got 512 RAM...... T_T this is painful I got alot of other stuff to do and now I got to wait :'( alright thanks dude

---

### Post by halitech on 2009-03-28
I don't use Handbrake but I do use Devede alot and on my P4 1.8 with 896meg of ram it takes from 4-6 hours to convert 4 tv shows (~45minutes each) to fit on a single dvd. The more ram you have the better it will go but also, the faster your processor, the faster it will go again

---

### Post by MrWES on 2009-03-28
> **lil_kid1333 said:**
> oh man I only got 512 RAM...... T_T this is painful I got alot of other stuff to do and now I got to wait :'( alright thanks dude


I have 2gm RAM and it still takes several hours. Best to set it and forget -- setup it up and run it overnight.

Bill

---

### Post by lil_kid1333 on 2009-03-28
Yeah but damn it man it heats up my room hella :'(

Nothing will happen to the pc though right?

---

### Post by halitech on 2009-03-28
> **lil_kid1333 said:**
> Yeah but damn it man it heats up my room hella :'(

Nothing will happen to the pc though right?

nothing as long as you have proper cooling in the system

---

### Post by lil_kid1333 on 2009-03-28
Yeah the fans their and working :) Thanks guys

---

### Post by huzzam on 2009-03-28
Which codec you use also makes a big difference. On my system (2gHz core2duo, 4gb ram) encoding to h.264 takes about three times longer than encoding to mpeg4. And I find that if i'm encoding to a high bitrate (I usually use 1500kbps) the results are fine for either codec.

peter

---

### Post by perrti-y02 on 2009-03-28
I am running a 2.66Ghz dual core with 2gb of RAM and a full movie will be done in about an hour for me. I can easily encode 4 at once (takes slightly longer but less time than doing all 4 in sequence) and I can browse the web whilst listening to music.

I am using DVD::rip as opposed to handbrake.

---

### Post by Shampyon on 2009-08-19
Bumping to ask related question --

I've been trying to back up my DVDs to small-size MKVs, but I think the encoding speed is getting a bit slower, probably because I'm using settings like Exhaustive Motion Esitmation with a 64px range (I used to use Uneven Multi-Hexagon) and 9/14 Reference/B-Frames for the anime...

Anyway, what I'd like to know is, would it be a good idea to buy more RAM to speed up encoding?

```
OS: Kubuntu 9.04 Jaunty
CPU: Intel Core Duo E8400
RAM: 2GB
Swap Memory: 4GB
Video Card:GeForce 9800GT PCI-E 512MB
```
SysInfo output is attached of you want more detail.

---

### Post by Shampyon on 2009-08-19
> **Shampyon said:**
> Bumping to ask related question --

I've been trying to back up my DVDs to small-size MKVs, but I think the encoding speed is getting a bit slower, probably because I'm using settings like Exhaustive Motion Esitmation with a 64px range (I used to use Uneven Multi-Hexagon) and 9/14 Reference/B-Frames for the anime...

Anyway, what I'd like to know is, would it be a good idea to buy more RAM to speed up encoding?

```
OS: Kubuntu 9.04 Jaunty
CPU: Intel Core Duo E8400
RAM: 2GB
Swap Memory: 4GB
Video Card:GeForce 9800GT PCI-E 512MB
```
SysInfo output is attached of you want more detail.

Another related question: Will I need to change my swap memory from 4GB to 8GB? If so, is there a way to do resize the partitions without losing data?

***Edit:*** I just noticed [the guide for resizing partitions without losing data on the GParted site]("http://en.kioskea.net/faq/sujet-2036-how-to-resize-a-partition-using-gparted-on-linux").

---

### Post by Shampyon on 2009-08-21
I opened up System Monitor while running Handbrake (not using Exhaustive Motion Estimation any more - I saw no discernible difference between it and the much faster Uneven Multi-Hexagon mode).

It seems Handbrake wasn't using much of my RAM at all - at most, a quarter of the 2GB. It was, however, using up to 70% of my CPU. Given the cost involved in upgrading a CPU I only bought eight months ago, I think this is one issue I can live with, especially since reverting to Uneven Multi-Hexagon has brought encoding time down to three to four hours per movie.

---

