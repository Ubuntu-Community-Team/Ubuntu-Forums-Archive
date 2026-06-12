---
title: "xubuntu 9.10 slow while watching videos and unable to restart properly"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by John Phang on 2010-09-15
The specs i have is 1066mhz celeron processor, 1gb ram and 20gb hd.
These treads have bother me for a long time, what should i do to fix it? anyone could help me please?

---

### Post by mikewhatever on 2010-09-15
Are you talking about flash videos like on youtube or vimeo, or any kind of videos? What's the output of **lspci | grep -i vga** ?

---

### Post by John Phang on 2010-09-15
I mean any type of videos, it just slow while watching videos.
here is it when i type on the code:

john@john-laptop:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

---

### Post by sikander3786 on 2010-09-15
While playing a video in whatever media player you like, either run System Monitor or the following command and see how much Processor, RAM and Swap are being used. Also see which processes are on top.

```

top

```

---

### Post by yaztromo on 2010-09-15
For some videos your CPU is probably too slow to play without experiencing choppyness. Lower resolution vids should be just fine.

As for your GFX card, it is likely not helping at all. I know someone else with a trident card that struggles also.

You could always try installing mplayer (sudo apt-get install mplayer) and see how that gets on with them.

---

### Post by John Phang on 2010-09-15
here is what get when i play video on totem while typed 'top' in terminal (screenshot). 

currently i'm using gnome mplayer its ok but still a bit lag while playing videos, but the problem is it cant get full screen size like this (screenshot-1). I've tried mplayer before it wont work on  my machine/computer.

---

### Post by sikander3786 on 2010-09-15
The CPU usage is exactly 100 %. Were you ever able to play videos on the same system fluently? Seems like you've also enabled desktop effects (transparency). If so try to stop the extra effects and see if it helps (I've never used Xubuntu so don't know much about that). Also try to switch the media player. VLC for instance...

---

### Post by mikewhatever on 2010-09-15
> **John Phang said:**
> here is what get when i play video on totem while typed 'top' in terminal (screenshot). 

currently i'm using gnome mplayer its ok but still a bit lag while playing videos, but the problem is it cant get full screen size like this (screenshot-1). I've tried mplayer before it wont work on  my machine/computer.

I think it's obvious that you expect too much of that computer.

---

### Post by yaztromo on 2010-09-15
I think the Trident card is definitely a stumbling block. Asking it to do desktop effects will only exacerbate the problem, couple that with a slow CPU and maybe even SDRAM and you will really struggle with decent quality video files.

If I remember it right the minimum I could get away with was a 1.2ghz Athlon XP with DDR memory and an Nvidia Geforce 2 for smooth video playback on Xubuntu.

Time to invest in a new rig.

BTW. You can also try the mplayer-nogui package for fastest possible mplayer, and press D to enable frame dropping and F for fullscreen (although mplayer and your trident card seem to have issues with this)

---

### Post by John Phang on 2010-09-16
ok, i know it now, anyway thanks for the help. :)

---

