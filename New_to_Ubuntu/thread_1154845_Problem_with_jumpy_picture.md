---
title: "Problem with jumpy picture"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by tmos22 on 2009-05-10
I installed Ubuntu 9.04 last week. When i try to watch high quality videos online or if i play a game , the picture is always jumpy, the sound plays fine. Could this be my graphics card? If so , how do i update it?

---

### Post by 3rdalbum on 2009-05-10
What card do you have?

If it's AMD or Intel, you will be much happier with an Nvidia graphics card. If this is a desktop computer and it has a PCI-E slot, you can buy a graphics card and just slot it in. Even something fairly basic, like an Nvidia 9500 (or GT120) would be great.

There is a known problem with AMD's drivers, that means you can't run Compiz and watch video at the same time. This may be the problem you are describing? You can turn off desktop effects temporarily while watching video. Or, upgrade to an Nvidia card; they don't have that problem.

---

### Post by Bölvaður on 2009-05-10
Open the terminal (Applications &#8594; Accessories &#8594; Terminal)

Post the output of these commands (paste in the terminal is ctrl+shift+v)
```
lspci | grep VGA
```

```
glxinfo | grep vendor

```

---

### Post by tmos22 on 2009-05-10
I have an nvidia card, everything was fine until a few weeks ago when i was on vista, i did a system update on vista and nothing is running smoothly since

02:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M G (rev a1)

glxinfo | grep vendor
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

---

### Post by tmos22 on 2009-05-10
Bump

---

### Post by Bölvaður on 2009-05-10
This looks ok for me.

You might want to try out other drivers (System &#8594; Administration &#8594; Hardware Drivers)

and check the difference for each driver by opening the terminal and type

```
glxgears
```

and you'll see something like mine
```
$ glxgears
63951 frames in 5.0 seconds = 12790.149 FPS
66721 frames in 5.0 seconds = 13344.195 FPS

```

if it is much lower than what I have then you have problems... as I have similar card as you

---

### Post by tmos22 on 2009-05-11
****

11257 frames in 5.0 seconds = 2251.323 FPS
11219 frames in 5.0 seconds = 2243.670 FPS
12887 frames in 5.0 seconds = 2577.343 FPS
21216 frames in 5.0 seconds = 4243.173 FPS
26961 frames in 5.0 seconds = 5392.124 FPS
29257 frames in 5.0 seconds = 5851.378 FPS
25670 frames in 5.0 seconds = 5133.832 FPS
27410 frames in 5.0 seconds = 5478.222 FPS
29091 frames in 5.0 seconds = 5818.170 FPS
29028 frames in 5.0 seconds = 5805.426 FPS
18070 frames in 5.0 seconds = 3613.920 FPS
29171 frames in 5.0 seconds = 5834.061 FPS
26797 frames in 5.0 seconds = 5359.235 FPS
11848 frames in 5.0 seconds = 2369.423 FPS

Any way of making it better???

---

### Post by tmos22 on 2009-05-11
Anyone?

---

### Post by durand on 2009-05-11
Run ***glxinfo  | grep "direct rendering"*** and tell us if it shows a Yes or No. If it's a no, you may need to reinstall the nvidia drivers.

EDIT: oops, misread...

---

### Post by tmos22 on 2009-05-11
I got a yes..... :(

---

### Post by durand on 2009-05-11
Hmm, strange. Does that video problem happen with other video players as well? Like mplayer or vlc?
```
sudo aptitude install mplayer vlc
```

---

### Post by PlaceboMessiah on 2009-05-11
this is happening to me as well

however, on certain 'high bandwidth' scenes of a bluray rip, the sound will get strangled as well

---

### Post by PlaceboMessiah on 2009-05-11
here's my info:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project

glxgears

808 frames in 5.0 seconds = 161.553 FPS
778 frames in 5.0 seconds = 155.424 FPS
834 frames in 5.0 seconds = 166.762 FPS
806 frames in 5.1 seconds = 159.455 FPS
716 frames in 5.0 seconds = 143.159 FPS
817 frames in 5.0 seconds = 163.304 FPS
806 frames in 5.0 seconds = 161.096 FPS
812 frames in 5.0 seconds = 162.227 FPS
798 frames in 5.0 seconds = 159.561 FPS

seems kinda slow

I'm on a Toshiba Satellite running in high performance mode
model: A200-FE0 1.66ghz, 1.5gig ram

glxinfo | grep "direct rendering"
Yes

---

### Post by tmos22 on 2009-05-11
> **durand said:**
> Hmm, strange. Does that video problem happen with other video players as well? Like mplayer or vlc?
```
sudo aptitude install mplayer vlc
```


It dosnt happen on any videos i have on VLC or any downloaded videos. It is mostly streaming. It even happens with simple flash games online. They are so laggy!

---

### Post by PlaceboMessiah on 2009-05-11
conversely this only has been happening in vlc and mplayer for me as i do not do any streaming or flash games with this machine

---

### Post by durand on 2009-05-12
@PlaceboMessiah: Does your problem still happen after you buffer the videos for a while? It sounds a lot like not having enough bandwidth to cope with streaming. Do you have direct rendering enabled?

@tmos22: My flash is also really slow, maybe you could try upgrading to flash 10, though it didn't really help me..

---

### Post by PlaceboMessiah on 2009-05-12
> **durand said:**
> @PlaceboMessiah: Does your problem still happen after you buffer the videos for a while? It sounds a lot like not having enough bandwidth to cope with streaming. Do you have direct rendering enabled?



direct rendering is enabled

how would i set up a big buffer?  My issue is not from internet streamed videos, but from HD files on my hard drive.

---

### Post by durand on 2009-05-12
Hmm, I guess it could be that your processor is too slow or that you don't have enough ram? Sorry, I'm out of ideas :(

---

### Post by coasat on 2009-05-12
I think your problem is similar to mine. When the picture was in full screen the image was choppy and did not run smoothly. 

Here is the thread I posted: [http://ubuntuforums.org/showthread.php?t=1147149](http://ubuntuforums.org/showthread.php?t=1147149)

Here is the link I was directed to (which solved the problem) :

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Hope this helps,

coasat

---

