---
title: "What program captures a video from a small tape?"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by Mariane on 2011-05-16
Hi, 

I rented a camera and now I had to give it back. I am left with small video tapes and I rented a video player to play them. This was cheaper than keeping the camera for another day. 

The video player connects to my computer via the firewire port. The output of:

```

dmesg

```

after connecting it is: 

```

[35766.161130] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[35766.161145] ieee1394: Node paused: ID:BUS[0-00:1023]  GUID[0800460103fb1b2d]
[35769.220045] ieee1394: Node removed: ID:BUS[0-00:1023]  GUID[0800460103fb1b2d]
[35772.620372] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0800460103fb1b2d]
[35772.620476] ieee1394: Node changed: 0-00:1023 -> 0-01:1023

```

Kino does not work for capture and dvgrab tells me "camera does not exist" - which is true, it is not a camera but a video player. 

I also checked some video editing programs in the hope that they would have a capture function included: KDENlive, openmovieeditor, cinelerra and openshot. But either they don't have this feature or I couldn't find it on their interface. 

Cinelerra doesn't install from the usual depositories. To get it you have to do: 
```

sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra

```

So please tell me what program I should use to capture the videos I have recorded on these small tapes and save them on my computer. 

Results of some commands I found online:

```

lspci

```

```

05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```

```

grep 1394 /var/log/kern.log

```

Endless scrolling of thousands of line saying:
```

ohci1394: fw-host0: IR DMA error - packet too long for buffer

```

```

gksudo modprobe raw1394
gksudo modprobe dv1394

```

Did nothing apparent. Who knows?

I keep editing this post. At last something looks promising: 
```

sudo dvgrab -f hdv tryvideo

```

It started the videoplayer and it says "Capture started". I'll post later, it seems like it is going to play the whole tape at watching speed. 

Final edit: this works!!! The image has a few jumping lines (horizontal lines which briefly don't fit with the rest of the picture) but on the whole it is OK. dvgrab creates several files called tryvideo001.m2t, tryvideo002.m2t, etc. They can be played back with vlc. 


Mariane

---

### Post by mikewhatever on 2011-05-17
I am wondering if you couldn't just capture the video with VLC. I don't know if the firewire input would be available as a device to capture from, it may reqire some searching.

---

### Post by Allavona on 2011-05-17
Have you tried pitivi video editor?

---

### Post by wep940 on 2011-05-17
Or.....perhaps use mencoder from the command line.  Someone helped me out with that with a USB video/audio capture device (has RCA jacks - can hook-up VCR, etc.).  It worked great for me.

---

### Post by jmore9 on 2011-05-17
If that thing will connect to a tv , then you could connect it to a tv tuner card and just record it like a tv program

---

### Post by Mariane on 2011-05-18
Thank you all for your suggestions. I gave back the rented video player. I tried vlc on it but I couldn't find the tape. I mean, these things don't show up as files in a directory. I wish they did, but they don't. I tried mounting and it tells you the tape is not a valid file system. 

> **Allavona said:**
> 
Have you tried pitivi video editor?


No. Is it good? 

Mariane

---

