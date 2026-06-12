---
title: "Hmm, Oh Dear, Squiggly lines on my video..."
date: 2009-03-04
forum: New to Ubuntu
---

### Post by quietbear on 2009-03-04
Hello, just tried using my new camera to record a short video.  I pre-watched it on the TV with the AV outs, so I know it is not the actual video quality that is the problem.

Here is the problem.  First this is what I did to get the video from the camera to my system: (Panasonic SDR-S10)

Pluged the camera into comp (USB)
It shows up as an external storage device
Opened the folder, dragged and dropped the file clip into my my comp

So now it is on my PC, (well sorta)

The problem is that when I play it now, there are a ton of squiggly lines especially when in motion.  Its sorta like all teh verticle lines in the shot get really squiggly, and especially if the camera moved slightly.

Like I said, IT IS NOT THE CAMERA.

It has to do something with either how I xfered the file to my system, or something that is missing that I need to properly play it.

From the box it says it records in MPEG-2.

Also, it was a 9 minute clip.  It was about 360 MB.  That is alot isnt it?  Is there a way to save it in a different format that will be like 1/3rd of that?

SOrry, I am new to video editing, always did graphics before now, so I thought I would give video a try.

Oh, PS, tonight I downloaded Kdenlive as well.  Thought that maybe there might be a way to get the video using that program instead of actually xfering the file from the camera to the PC like a data file.

Thanks

---

### Post by quietbear on 2009-03-04
To be honest, I am just about ready to switch back to XP.  I dont know why, but whenever I connect the camera to the PC, if I play the file from the camera, or if I transfer it over, it doesnt matter, I get a ton of squiggly lines.

Any vertical line turns really squiggly (like waves in a pool sorta).

It works fine on the TV, so it is most certainly not the camera, but Linux.

Is there something I need to download to help pretty little linux understand the video or something?

---

### Post by dmizer on 2009-03-04
Try disabling advanced desktop effects and see if that makes the video any better.

---

### Post by quietbear on 2009-03-04
Found a another person with a similar problem but on a Mac, maybe it will help you understand what I mean, or maybe to help you with the Linux solution:

[http://discussions.apple.com/thread.jspa?threadID=1795061]("http://discussions.apple.com/thread.jspa?threadID=1795061")

---

### Post by quietbear on 2009-03-04
> **dmizer said:**
> Try disabling advanced desktop effects and see if that makes the video any better.

I dont have any of the effects turned on to increase performance

---

### Post by quietbear on 2009-03-05
After more searching, I believe the problem to be with interlacing.  My question is this I guess.  Is it because of my LCD display, and it will be fine?

Meaning, even though it looks squiggly to me, if I upload it to youtube or whatever, will everyone else see it fine?

---

### Post by dmizer on 2009-03-05
Can you provide a direct link to an unmodified video you are experiencing problems with (not youtube)? Even if we do not have the same problem, we might be able to determine what yours might be by seeing the video.

Also, please open a terminal and post the output of this command:
```
lspci
```

---

### Post by quietbear on 2009-03-05
> 00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)


THere is the output.  I cant give a link to the video because it is 360 MB and far to large for me to load anywhere.

I think I may have found the solution using Kino and some of the settings, exporting a copy now to see if it gets rid of the interlacing and compresses it down enough to put up.

Well, it didnt export anything, I will try again to see if it works after a nice restart.

---

### Post by dmizer on 2009-03-05
You indicated that all video from your webcam appears this way. Can you take a shorter test video and upload it somewhere?

What video players have you tried? Have you tried VLC?

---

### Post by quietbear on 2009-03-05
Got it to work.  The video is interlaced on the system until I export it in other formats and remove the interlacing.

Thanks for the help though.

---

