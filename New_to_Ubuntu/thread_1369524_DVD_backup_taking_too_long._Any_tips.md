---
title: "DVD backup taking too long. Any tips?"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by r3bol on 2010-01-01
I'm looking for some advice on how to backup my kids DVDs in a reasonable amount of ripping time. 
I am using handbrake (a great program) at the moment, but it's taking too long, (like 7.5 hours for a one pass rip). My machine has [_reasonable specs_]("http://h18000.www1.hp.com/products/quickspecs/11602_na/11602_na.HTML") so I was wondering if you guys have any experience ripping and whether you could offer me some advice to get a standard quality rip at around 2 hours (or something near)? (PS. I copy the VIDEO_TS folder to the hard drive first).

Maybe the program used for ripping is important or maybe it's the type of codec matters? Like does Xvid generally take longer or shorter than h264?

Any advice appreciated.

Thanks.

---

### Post by moody_mark on 2010-01-01
Hi, Theres an app called DeVeDe which creates DVDs but im not sure if it will do what you want?

---

### Post by resander on 2010-01-01
I had a similar problem about a year ago

[http://ubuntuforums.org/showthread.php?t=1010107](http://ubuntuforums.org/showthread.php?t=1010107)

and I found that k9copy produced a backup dvd in about 15 minutes.
I had to install libdvdcss2 first via synaptic.

---

### Post by MrWES on 2010-01-01
> **r3bol said:**
> I'm looking for some advice on how to backup my kids DVDs in a reasonable amount of ripping time. 
I am using handbrake (a great program) at the moment, but it's taking too long, (like 7.5 hours for a one pass rip). My machine has [_reasonable specs_]("http://h18000.www1.hp.com/products/quickspecs/11602_na/11602_na.HTML") so I was wondering if you guys have any experience ripping and whether you could offer me some advice to get a standard quality rip at around 2 hours (or something near)? (PS. I copy the VIDEO_TS folder to the hard drive first).

Maybe the program used for ripping is important or maybe it's the type of codec matters? Like does Xvid generally take longer or shorter than h264?

Any advice appreciated.

Thanks.

Do you want an original backup, no matter the size? Or do you want to back them up so they fit on a DVD5 (4400mb)? If you want a full backup, the entire DVD, I would suggest using vobcopy; from the terminal window:
```
sudo apt-get install vobcopy
``` then
```
vobcopy -m
```this will copy the entire disk including menus to your hard drive. You can then use Kb3 to burn to a DL disk. If you want to copy the DVD so it fits on a standard SL DVD, I would suggest using K9Copy to rip it to an iso file and then use K3B to burn the iso. K9copy and K3b are KDE Desktop applications, but they run very well under the GNOME Desktop and IMHO worth the extra installation files to have them.

[http://www.toastboy.com/main/unixlinux/using-vobcopy-and-mkisofs-to-backup-dvds-to-harddrive/]("http://www.toastboy.com/main/unixlinux/using-vobcopy-and-mkisofs-to-backup-dvds-to-harddrive/")


Bill

P.S. Sounds like you are transcoding the DVD with Handbrake into a compressed format like avi, etc. That is why it takes so long.

---

### Post by Paqman on 2010-01-01
What kind of quality are you ripping the DVDs at? Using Handbrake I generally encode to H.264 Matroska videos at about RF:12 and they look really good. Seems to take about 90mins or so, but i've got 2 cores at 3GHz, and you've got what, 1 core at 1.8GHz? For DVDs that aren't particularly good quality to start with I drop the quality setting down to about 16.

If it's taking 7 hours I suspect you're ripping at excessively high quality settings. You can preview the actual quality of the output file before commiting to the full encode. Click "Picture Settings" and make sure "show preview" is checked, and pick somewhere in the middle of the file. It'll encode 5 seconds of the file for you to check the output quality.

---

### Post by r3bol on 2010-01-01
I just need to back up to hard drive. AVI, MKV, MP4 whichever. About 700MB - 1GB for something movie length. 
The 7 h.5 hour thing was h264, 1000kbps, mp3 audio@160kbps, just one pass, frame rate - same as original.

---

### Post by Paqman on 2010-01-01
> **r3bol said:**
> I just need to back up to hard drive. AVI, MKV, MP4 whichever.

You could just rip images of the disks using Brasero then. No need to re-encode at all. Should takes minutes instead of hours.

---

### Post by r3bol on 2010-01-01
> **Paqman said:**
> You could just rip images of the disks using Brasero then. No need to re-encode at all. Should takes minutes instead of hours.It that like ISOs? Could VLC media player play them?

---

### Post by Paqman on 2010-01-01
> **r3bol said:**
> It that like ISOs? Could VLC media player play them?

Ah ok, if you still want to play them, rather than have them as backups then that's a different story. Having said that, the [VLC site]("http://www.videolan.org/vlc/features.html#input_notes") doesn't show .iso as a good media format, but the [wikipedia page]("http://en.wikipedia.org/wiki/VLC_media_player") does.

One way to find out I guess?

EDIT: Just tried it, and yes VLC will play a DVD .iso, as does XBMC.

---

### Post by MrWES on 2010-01-01
> **r3bol said:**
> I just need to back up to hard drive. AVI, MKV, MP4 whichever. About 700MB - 1GB for something movie length. 
The 7 h.5 hour thing was h264, 1000kbps, mp3 audio@160kbps, just one pass, frame rate - same as original.

vobcopy is the cleanest way, and one of the quickest too. Any transcoding you do will take up to several hours depending on the capablities of your machine. If you want the main title in one vob file, use vobcopy -l (lower case L).

Bill

---

### Post by 3rdalbum on 2010-01-01
H.264 is a very intensive compressor. 7.5 hours sounds about right for an older computer such as yours.

I don't use Handbrake, but if it offers Xvid or MPEG-4 you'll want to use those. The quality/bitrate ratio isn't quite as good, but they compress faster.

---

### Post by Bartender on 2010-01-01
I agree with above posts - depending on which features you're asking for, your rip times sound about right.

I always use the "High Profile" settings in Handbrake.  On our Core2Duo (1.5 GHz) laptop a rip takes 5 to 6 hours.  Have noticed one thing that might make a difference for you.  If audio is set to 5.1 "pass through" that adds about 2 hours to the rip compared to setting it as Dolby Pro-Logic II or whatever lower quality settings you're offered.  If you know the rips will only be played on a laptop or desktop then you could choose the lower audio settings.  I figured "in for a penny, in for a pound" and leave it at the highest settings.

I tried ripping on our single-core Pentium 4 (3 GHz) and it took _longer_ than the laptop!  But that was in Windows, using DVD43 in concert with Handbrake, so maybe that's not really a fair comparison.

---

### Post by r3bol on 2010-01-01
Thanks guys, so it seems it's down to xvid vs h264 etc... 
I just installed dvd:rip and it tried it out on a 57 minute video with target size of 700MB, mp3 audio, one pass... and it's estimated to take 1h34m :popcorn: Quality wise, as long as it's watchable, it's good for the kids. 

It looks like the latest version of handbrake doesn't support xvid anymore, so I'll stick with either the old version or keep using dvd::rip. 

As for testing iso with Brasero, it didn't really happen. The graphics dropped out of the window and it seemed to be doing something, but after an hour I quit.

---

### Post by MrWES on 2010-01-01
> **r3bol said:**
> Thanks guys, so it seems it's down to xvid vs h264 etc... 
I just installed dvd:rip and it tried it out on a 57 minute video with target size of 700MB, mp3 audio, one pass... and it's estimated to take 1h34m :popcorn: Quality wise, as long as it's watchable, it's good for the kids. 

It looks like the latest version of handbrake doesn't support xvid anymore, so I'll stick with either the old version or keep using dvd::rip. 

As for testing iso with Brasero, it didn't really happen. The graphics dropped out of the window and it seemed to be doing something, but after an hour I quit.

Try Avidemux

Bill

---

