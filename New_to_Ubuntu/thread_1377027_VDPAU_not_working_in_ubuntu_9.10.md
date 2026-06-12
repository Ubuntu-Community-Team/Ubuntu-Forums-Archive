---
title: "VDPAU not working in ubuntu 9.10"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by e_man on 2010-01-09
Hi, I decided to put together a small HTPC ( Zoatc mb with Intel Atom 330 cpu, nvidia 9400M, 4 Gigs RAM) using ubuntu 9.10. I'm very new to linux since this is my first install of ubuntu. After installing ubuntu and the nvidia driver I was expecting a smooth HD video playback but HD videos in XBMC shutter too much and VLC just freezes. I know that this mb is capable of doing more so I'm suspecting that VDPAU is not enabled. How do I enable VDPAU for VLC and other apps?
My cpu usage while watching a MKV file in XBMC is:
CPU 1 - 30%
CPU 2 - 15%
CPU 3 - 11%
CPU 4 - 13%

---

### Post by Greenwidth on 2010-01-09
Should be Ok with that cpu usage, which nvidia driver are you using?

EDIT:
Just tried this test mkv:
[http://www.megaupload.com/?d=1D4BX1U9](http://www.megaupload.com/?d=1D4BX1U9) (Bird_42_MBit_ABR_(+-1.5 MBit).mkv 109.6 MB)

on my netbook - Atom 270 cpu Nvidia 9400M 2Gb RAM
with Nvidia 190.42 driver
15% CPU 1
5% CPU 2

Disabling compositing helped as well:
sudo apt-get install fusion-icon
start in system tools > right click and switch to Metacity (doesn't have compositing in default setup)

Also XBMC is from ppa:
[https://launchpad.net/~team-xbmc/+archive/ppa](https://launchpad.net/~team-xbmc/+archive/ppa)

---

### Post by e_man on 2010-01-09
Thanks for you reply.
I was expecting smoother playback. I'll see what happens if overclocked from 1.6 ghz to 2 ghz. I'm using nvidia driver version 185 and overscan is killing me too...lol. But at least XBMC can take care of that for video playback.

---

### Post by darkshadow on 2010-01-09
Are you sure you are using the right vc and vo since they are not defaulted to. To make sure use mplayer from the command line so you can read the output and make sure.

mplayer -vc ffh264vdpau -vo vdpau video.mkv

---

### Post by e_man on 2010-01-09
> **darkshadow said:**
> Are you sure you are using the right vc and vo since they are not defaulted to. To make sure use mplayer from the command line so you can read the output and make sure.
 
mplayer -vc ffh264vdpau -vo vdpau video.mkv
 
How do i run mplayer from the command line? and what are vc and vo? Sorry very new to this.

---

### Post by Great Blue Heron on 2010-01-09
e_man

Follow this guide to install the [very latest version of Smplayer]("http://ubuntuforums.org/showthread.php?t=1305181"). You need to install the latest official Nvidia driver 190.53 because the latest version of mplayer (VDPAU) doesn't work drivers earlier than 190.32.

---

### Post by darkshadow on 2010-01-09
just run the following command using the replacing video.mkv with your file in a terminal

mplayer -vc ffh264vdpau -vo vdpau video.mkv

-vc is forcing it to use the right (V)ideo (C)odec
-vo is forcing it to use the right (V)ideo (O)utput

---

### Post by e_man on 2010-01-10
> **Great Blue Heron said:**
> e_man
 
Follow this guide to install the [very latest version of Smplayer]("http://ubuntuforums.org/showthread.php?t=1305181"). You need to install the latest official Nvidia driver 190.53 because the latest version of mplayer (VDPAU) doesn't work drivers earlier than 190.32.
 
Ok, Iwas able to install 190.53 driver but couldnt follow through with Smplayer install.
this is the error message after trying to install mplayer-nogui
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
  mplayer-nogui: Depends: libasound2 (> 1.0.22) but 1.0.20-3ubuntu6.1 is to be installed
                 Depends: libesd0 (>= 0.2.35)
                 Depends: libjack0 (>= 0.118+svn3796) but 0.116.1-4ubuntu2 is to be installed
E: Broken packages
 
 
 
> **darkshadow said:**
> just run the following command using the replacing video.mkv with your file in a terminal
 
mplayer -vc ffh264vdpau -vo vdpau video.mkv
 
-vc is forcing it to use the right (V)ideo (C)odec
-vo is forcing it to use the right (V)ideo (O)utput
 
I can't run that command since couldnt install mplayer-nogui

---

### Post by lenkiatleong on 2010-01-10
> **e_man said:**
> Hi, I decided to put together a small HTPC ( Zoatc mb with Intel Atom 330 cpu, nvidia 9400M, 4 Gigs RAM) using ubuntu 9.10. I'm very new to linux since this is my first install of ubuntu. After installing ubuntu and the nvidia driver I was expecting a smooth HD video playback but HD videos in XBMC shutter too much and VLC just freezes. I know that this mb is capable of doing more so I'm suspecting that VDPAU is not enabled. How do I enable VDPAU for VLC and other apps?
My cpu usage while watching a MKV file in XBMC is:
CPU 1 - 30%
CPU 2 - 15%
CPU 3 - 11%
CPU 4 - 13%

Not sure how you watch the MKV file. Is the MKV file in a NAS or another PC or in this HTPC itself?
If its not in HTPC, are you using wireless or wired connection? 

I have a similar HTPC setup like yours and my VLC is playing m2ts file smoothly with Nvidia driver version 185 !! However, my m2ts files are in a NAS wired to router (1Gbps) and my HTPC is also wired to the same router. No problem using Ubuntu 9.10 and VLC.

As m2ts file demands 17Mbps bandwidth, i reckon mkv should not be a problem too.

---

### Post by e_man on 2010-01-10
The files are on an external hard drive. but I might be streaming them from my laptop in the future via wireless. I'll dump one file to my hard drive and see how it plays.

---

### Post by sdowney717 on 2010-01-10
there is a setting on the video output in xbmc you can change.
I cant recall the exact phrase but it has to do with vdpau disabling.

look at render method under video settings -playback.

---

### Post by e_man on 2010-01-10
Setting rendering system to VDPAU I did that already but didnt help.

---

### Post by darkshadow on 2010-01-11
Have you tried getting rid of the smplayer ppa before installing mplayer-nogui

---

### Post by e_man on 2010-01-11
> **darkshadow said:**
> Have you tried getting rid of the smplayer ppa before installing mplayer-nogui
 
I just read about that in another thread. Maybe thats the problem. I'll try when I get back home. How would can I get rid of it?

---

### Post by gradinaruvasile on 2010-01-11
The solution:

Install mplayer (and drivers) from the following PPA:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

And run from tha command line as was suggested before:
Open a terminal. Type in it:

```
mplayer -vo vdpau -vc ffh264vdpau movie.mkv
```

You can open a nautilus (ubuntu's file explorer) window, type that stuff before the movie name, and then simply drag-and-drop the movie from the nautilus window in the terminal window. Press enter. F is fullscreen, page up/down is forward/backward 10 min, up/down forward/back 10sec, space pause.

The trick is to make sure you have only this ppa enabled that has mplayer. Trust me, it works if setup right. 
I have a crappy Athlon 3200+ single core with ASUS M3N78-VM mobo that has integrated nvidia 8200 on it - watching 1080p movies is at ~25% CPU EVEN WITH COMPIZ ON (semi-transparent cube with atlantis plugin , wobbly windows, blurry windows headers, burning windows etc effects activated). It seems VDPAU bypasses somehow Compiz.
I use the latest (now 195.30) Nvidia drivers directly from their site BTW.

---

### Post by e_man on 2010-01-11
> **gradinaruvasile said:**
> The solution:
 
Install mplayer (and drivers) from the following PPA:
 
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)
 
And run from tha command line as was suggested before:
Open a terminal. Type in it:
 
```
mplayer -vo vdpau -vc ffh264vdpau movie.mkv
```
 
You can open a nautilus (ubuntu's file explorer) window, type that stuff before the movie name, and then simply drag-and-drop the movie from the nautilus window in the terminal window. Press enter. F is fullscreen, page up/down is forward/backward 10 min, up/down forward/back 10sec, space pause.
 
The trick is to make sure you have only this ppa enabled that has mplayer. Trust me, it works if setup right. 
I have a crappy Athlon 3200+ single core with ASUS M3N78-VM mobo that has integrated nvidia 8200 on it - watching 1080p movies is at ~25% CPU EVEN WITH COMPIZ ON (semi-transparent cube with atlantis plugin , wobbly windows, blurry windows headers, burning windows etc effects activated). It seems VDPAU bypasses somehow Compiz.
I use the latest (now 195.30) Nvidia drivers directly from their site BTW.
 
Ok I'll give mplayer nogui a try (can't wait to get home lol). Then compiz will be next. Well, I have to resolve overscan issues before I do anyting else....

---

### Post by Man of Wax on 2010-02-05
Hi,
I have the same problem. If i start mplayer from terminal:

```
mplayer -vo vdpau -vc ffh264vdpau movie.mkv
```

vdpau works very well (5-10% cpu utilization) but if I start the mplayer gui vdpau doesn't work. From the gui I've selected as video output "vdpau" but in the codec & demuxer tab there isn't any ffh264vdpau (or any *vdpau codec family).

---

### Post by andrew.46 on 2010-02-05
Hi Man of Wax,

> **Man of Wax said:**
> I have the same problem. If i start mplayer from terminal:

```
mplayer -vo vdpau -vc ffh264vdpau movie.mkv
```

vdpau works very well (5-10% cpu utilization) but if I start the mplayer gui vdpau doesn't work.

Rather than use the default gui of MPlayer which has been effectively abandoned by the MPlayer developers you may find better results using SMPlayer. You have not mentioned which version of Ubuntu you are using but if you are using Karmic the following single command will get the latest SMPlayer:

```

sudo add-apt-repository ppa:rvm/smplayer && \
sudo apt-get update && \
sudo apt-get install smplayer

```

I suspect that it will be a lot easier to get vdpau output with SMPlayer than with the older gui...

All the best,

Andrew

---

### Post by Man of Wax on 2010-02-06
Thank you Andrew, smplayer gui works perfect :D

---

### Post by andrew.46 on 2010-02-06
Hi Man of Wax,

> **Man of Wax said:**
> Thank you Andrew, smplayer gui works perfect :D

Excellent news :). An added bonus is that the developer of SMPlayer is available on these forums if there are any questions concerning this fine application.

Andrew

---

### Post by mutha88 on 2010-02-12
Hi! I have a similar problem with VDPAU, that's why I'm posting in that topic.

Here it is:

I've installed Ubuntu i386. My CPU is Intel Core2Duo e2160 @ 1.8 Ghz and my video card is GeForce 9800GT. I have installed both mplayer and smplayer. Both of them work.

Buuut... When I play 720p mkv file my CPU usage goes insane - 60 - 90% !!! 

I tried enabling vdpau under smplayer gui -> Options -> Preferences -> Video -> Output driver -> vdpau

That's all I've done. And the result is, that I can't use vdpau under Ubuntu, which makes me sad, because I use DXVA under Win7 with no problems at all... :(

By the way, I'm using the newest driver from NVIDIA - 195.30

Can u help me?

---

### Post by AdrianVeidt on 2010-02-22
Since the 190.53 driver, the libvdpau shared library is no longer included in the nvidia driver package. It is a separate package that need sto be installed. Nvidia does include their own libvdpau driver, but it needs the shared lib to work.

The shared lib is included in Lucid but not Karmic. Libvdpau1 is the package name.

---

### Post by Dimitree on 2010-03-17
Dear God thank you guys :) smplayer works just great.
All i did is select video output as vdpau and already had the libvdpau1 package installed in lucid and it works just great :)
I think smplayer should be installed as default in ubuntu, it's so great ^^

---

### Post by Laxman_prodigy on 2010-03-26
> **AdrianVeidt said:**
> Since the 190.53 driver, the libvdpau shared library is no longer included in the nvidia driver package. It is a separate package that need sto be installed. Nvidia does include their own libvdpau driver, but it needs the shared lib to work.

The shared lib is included in Lucid but not Karmic. Libvdpau1 is the package name.


I have now everything. But, it still doesn't work with "VDPAU". I have checked I have nvidia ppa enabled and I have installed 190 version as it is called stable.

What am I missing now?

What should do now? I have 64-bit Ubuntu.

---

### Post by smpn on 2010-04-12
> **darkshadow said:**
> Are you sure you are using the right vc and vo since they are not defaulted to. To make sure use mplayer from the command line so you can read the output and make sure.

mplayer -vc ffh264vdpau -vo vdpau video.mkv

Awesome!!  That got it working for me!

Thanks

---

