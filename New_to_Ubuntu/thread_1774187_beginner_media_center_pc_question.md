---
title: "beginner media center pc question"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by wep940 on 2011-06-03
I'm just a beginner with the idea of a media center pc.  I would like to know the answers to the following, if possible, so I can help my sister's son in law:
 
- if a video card has hdmi output, does that mean I can directly connect to my hdtv and get the high resolution of the TV, or only something like 600x400?
 
- does HDMI output include audio?  If not, how do I get the audio from the PC to the HDTV?  The HDTV already has the speakers, etc., they want to use, so how do I get the sound from the PC to the HDTV?
 
- are there any inexpensive video cards, either PCI or AGP4x, that support HDMI output and would work in this situation?
 
 
Thanks in advance for your time!

---

### Post by Hedgehog1 on 2011-06-03
I use HDMI between my computer and my LCD TV for both sound an picture.

HDMI will carry most any resolution, and certainly as high as your TV can go (1920x1080).  You will need to determine the real resolution of the TV (some are less than the 1920x1080; these are still fine for movies).

If you select a basic NVidia card with HDMI and are running Natty, you can get sound working using this method: [**_Natty How To: Audio over HDMI for NVidia_**]("http://ubuntuforums.org/showthread.php?t=1741294").  Getting sound over HDMI in 10.10 is more complicated.

If you select a basic ATI card with HDMI, I believe the sound over HDMI setup is simple even in 10.10.  I use all NVidia here at home, but ATI at work (with no HDMI on those systems).

If you have not acquired the PC yet, any motherboard with on-board video and HDMI out is capable of outputting HDTV and sound over HDMI, and no seperate video card is required.

I use HMDI and amy very happy with it.  I did order a handful of the 'Amazon basics HDMI' cables because they work great (even support 3D) and are priced reasonably.

HDTV video out is not a big load on a PC (unlike video games), so PC and video requirements are met by most current low end PCs.

***The Hedge***

:KS

---

### Post by mastablasta on 2011-06-03
yeah cheapest HDMi card with HDMI output would do. ATI does the sound over the card. not sure how it's with nvidia.
also this list might help:
[http://www.ubuntu.com/certification/catalog](http://www.ubuntu.com/certification/catalog)

---

### Post by papibe on 2011-06-03
> **wep940 said:**
> if a video card has hdmi output, does that mean I can directly connect to my hdtv and get the high resolution of the TV, or only something like 600x400?
In most cases: Yes, because almost any modern card can handle at least minimum HD (1280x720, 1366x768, or similar).

> **wep940 said:**
> does HDMI output include audio?  If not, how do I get the audio from the PC to the HDTV?  The HDTV already has the speakers, etc., they want to use, so how do I get the sound from the PC to the HDTV?
Not really, some relatively recent cards (couple of years old) don't pass the audio through HDMI. You have to check the card's specs.

In the case it doesn't, the only 'practical' solution would be if your TV has a PC input. That is, that has separate audio and video inputs. That's the way I have connected my HTPC to my Sony Bravia: Nvidia 9500 GT -> DVI output -> DVI-HDMI cable -> HDMI PC input. The sounds is going from the PC's line output to the TV's stereo RCA inputs. 

> **wep940 said:**
> are there any inexpensive video cards, either PCI or AGP4x, that support HDMI output and would work in this situation?

What you really want in a HTPC is video hardware acceleration. The Nvidia 8400 GS would work, but it has limited [acceleration]("http://www.mythtv.org/wiki/VDPAU"). If your PC supports PCIe, there are plenty of options. For example the Nvidia 210 (around US$40).

If you have a little more budget, there are little hptc wonders. I helped my brother to configure a [Zotac Mag]("http://www.microcenter.com/single_product_results.phtml?product_id=0332179"). Everything worked perfectly:
[LIST]
[*]Full Ubuntu 10.4 install, so it's not only for movies (you can use Firefox to browse the internet, etc).
[*]It has an NVIDIA ION incorporated in the motherboard so it supports hardware acceleration.
[*]It supports audio over HDMI, and is very easy to config using the graphical interface.
[*]XBMC runs perfectly (free HTPC software).
[/LIST]
The only thing that's not is optimal is that the wireless card is not the best (actually pretty bad). If you use it with an ethernet cable... no problem.

Hope it helps.

---

### Post by wep940 on 2011-06-03
Thanks all for the input!  It is very helpful to me.  The PC in question is a hodge-podge.  It started life as an old Compaq Presario 5360.  The only thing besides the case that is original now is the floppy drive.  I replaced the power supply, the motherboard with an used eMachines 2.3 or 2.4 ghz Celeron, 512mb memory, an 80 gig ATA100 drive, and a DVD-ROM/CD-RW drive.  The current video is Intel 845 I think (I'd have to check again) with only VGA output.  I know their TV has a VGA input, but I know the video wouldn't be HD, and I'm not sure it could get the resolution.

---

