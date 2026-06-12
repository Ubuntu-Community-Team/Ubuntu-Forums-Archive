---
title: "How on Earth do you play a cd?!"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Jerfo on 2009-09-09
Ok I know, this must sound like the dumbest question ever but I just can't find a damn way to do it! I've been using Ubuntu for nearly a year now but since I never listen to cds at home I had never needed to try up until now and alas! I find out I just can't do it!

The thing is this, when I insert any audio cd nothing happens (and I specify audio cd because I've had no problem with DVDs), when I try to play it using Amarok it crashes, when I go to the media folder both cdrom0 and 1 are empty, nothing happens.

So, is there some sort of fancy little program one has to get for doing such a mundane task? :confused:

---

### Post by earthpigg on 2009-09-09
think back a year, if you can.

did you install **ubuntu-restricted-extras**, or did you use some other method?

open add/remove programs, and see if that package is installed. if it isn't, install it.

---

### Post by lindsay7 on 2009-09-09
Try starting the computer with the cd in the drive. That may work for you.

---

### Post by Windows Nerd on 2009-09-09
Check if it is mounted. It may not be for some reason, though Ubuntu should automount them. 

To mount it:
```
mnt /dev/cdrom
```

I believe this is right, though I may be mistaken. If I am, someone correct me. I forget these things even though I just read them the other day...

Scott

---

### Post by mc4man on 2009-09-09
Technically you need nothing additional at all installed to play an audio cd.
As soon as the Os is installed playback should be possible, if you had 2 drives you can even play them off of a live cd.

To see if the files are available, after cd is inserted look in home folder -> .gvfs - there should be a folder named "cdda mount on scd0" or scd1

Note that .gvfs is a hidden folder

( this location is for gnome, kde is different

---

### Post by FreewheelinFrank on 2009-09-10
Go to Places> Home Folder> Edit> Preferences and click on the Media tab.

For CD Audio, select 'Ask what to do'.

If you then don't see a pop-up screen offering various options when inserting a CD, there's a problem with Ubuntu seeing the disc.

---

### Post by andrew.46 on 2009-09-10
Hi Jerfo,

> **Jerfo said:**
> So, is there some sort of fancy little program one has to get for doing such a mundane task? :confused:

Hopefully the other posters have steered you towards getting your cds recognised under Ubuntu :-). But if you want to win some geek points try playing your cd from the commandline:

```
mplayer -cache 2048 -cache-min 80 cdda://
```

and for even more geek points you can run a cddb query the same way:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -quiet -cache 2048 -cache-min 80 cddb://[/COLOR]**
MPlayer SVN-r29664-4.3.3 (C) 2000-2009 MPlayer Team

Playing cddb://.
Found audio CD with 10 tracks.
================ CD INFO === start =========
 artist=[Schoenberg]
 album=[Verklärte Nacht, Op. 4 - Trio, Op. 45]
 genre=[Unknown]
 nb_tracks=10
 length= 48:12.50
  # 1  6:13.71 @     150	[Verklärte Nacht: Sehr langsam (Bar/Takt/Mesure/Battu 1)] 
  # 2  5:36.46 @   28195	[Veklärte Nacht: Breiter (Bar 100)] 
  # 3  2:13.71 @   53440	[Verklärte Nacht: Schwer betont (Bar 201)] 
  # 4 10:07.68 @   63485	[Verklärte Nacht: Sehr breit und langsam (Bar 229)] 
  # 5  4:38.56 @  109077	[Verklärte Nacht: Sehr ruhig (Bar 370)] 
  # 6  1:50.31 @  129982	[String Trio: Part 1 (Bar 1)] 
  # 7  6:08.74 @  138262	[String Trio: 1st Episode (Bar 52)] 
  # 8  3:00.01 @  165935	[String Trio: Part 2 (Bar 133)] 
  # 9  2:44.08 @  179435	[String Trio: 2nd Episode (Bar 180)] 
  #10  5:38.09 @  191742	[String Trio: Part 3 (Bar 208)] 
================ CD INFO ===  end  =========
Cache fill:  0.00% (0 bytes)   
Verklärte Nacht: Sehr langsam (Bar/Takt/Mesure/Battu 1)

rawaudio file format detected.
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...


```

But I digress more than a little from the original question.....

Andrew

---

### Post by Jerfo on 2009-09-12
Well, none worked, basically it seems that the cds are not being recognized at all, there's nothing on .gvfs, I didn't have those extras installed, only the modules, still no difference and I tried to mount from command line but I guess the command is wrong?

---

### Post by NoaHall on 2009-09-12
It would be ```
mount /dev/scd0 /media/cdrom0 
```

---

### Post by cariboo on 2009-09-12
Audio CD's aren't mounted the same way as data CDs are mounted. What is the output of:

```
dmesg | tail -n20
```

When you insert an audio CD.

---

### Post by Jerfo on 2009-09-14
Here's what comes out, I hope it makes some sense to you because it tells me nothing...

```
[ 6741.804144] ata4.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 6741.804146]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 6741.804148]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 6741.804154] ata4.01: status: { DRDY ERR }
[ 6741.804185] ata4: soft resetting link
[ 6741.985339] ata4.01: configured for PIO3
[ 6746.984185] ata4.01: qc timeout (cmd 0xa0)
[ 6746.984202] ata4.01: TEST_UNIT_READY failed (err_mask=0x5)
[ 6746.984244] ata4: soft resetting link
[ 6747.165391] ata4.01: configured for PIO3
[ 6752.164125] ata4.01: qc timeout (cmd 0xa0)
[ 6752.164139] ata4.01: TEST_UNIT_READY failed (err_mask=0x5)
[ 6752.164147] ata4.01: limiting speed to PIO2
[ 6752.164187] ata4: soft resetting link
[ 6752.345433] ata4.01: configured for PIO2
[ 6757.345075] ata4.01: qc timeout (cmd 0xa0)
[ 6757.345088] ata4.01: TEST_UNIT_READY failed (err_mask=0x5)
[ 6757.345093] ata4.01: disabled
[ 6757.345148] ata4: soft resetting link
[ 6757.500240] ata4: EH complete

```

---

