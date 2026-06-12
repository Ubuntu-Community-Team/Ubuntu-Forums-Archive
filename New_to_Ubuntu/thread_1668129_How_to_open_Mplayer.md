---
title: "How to open Mplayer?"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by Jetro on 2011-01-15
This has got to be the weirdest thing ever.

I installed Mplayer via Terminal (sudo apt-get install Mplayer), and I can't find the programme anywhere. It's not in Applications. When I type Mplayer in Terminal, I get a ridiculous long line of text.

```
oyv@oyv-laptop:~$ mplayer
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv>        select video output driver ('-vo help' for a list)
 -ao <drv>        select audio output driver ('-ao help' for a list)
 vcd://<trackno>  play (S)VCD (Super Video CD) track (raw device, no mount)
 dvd://<titleno>  play DVD title from device instead of plain file
 -alang/-slang    select DVD audio/subtitle language (by 2-char country code)
 -ss <position>   seek to given (seconds or hh:mm:ss) position
 -nosound         do not play sound
 -fs              fullscreen playback (or -vm, -zoom, details in the man page)
 -x <x> -y <y>    set display resolution (for use with -vm or -zoom)
 -sub <file>      specify subtitle file to use (also see -subfps, -subdelay)
 -playlist <file> specify playlist file
 -vid x -aid y    select video (x) and audio (y) stream to play
 -fps x -srate y  change video (x fps) and audio (y Hz) rate
 -pp <quality>    enable postprocessing filter (details in the man page)
 -framedrop       enable frame dropping (for slow machines)

Basic keys: (complete list in the man page, also check input.conf)
 <-  or  ->       seek backward/forward 10 seconds
 down or up       seek backward/forward  1 minute
 pgdown or pgup   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 x or z           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand

 * * * SEE THE MAN PAGE FOR DETAILS, FURTHER (ADVANCED) OPTIONS AND KEYS * * *
```
I thought there was supposed to be a GUI here?

---

### Post by garvinrick4 on 2011-01-15
#open a terminal:
```
nautilus /usr/share/applications
```Is it there:

#Or below:
```
sudo apt-get install aptitude
``````
aptitude show mplayer
```Will tell you version if installed and much more:

## Or you can try mplayer not Mplayer:

---

### Post by stmiller on 2011-01-15
Nope, no gui. :) mplayer is all from the command line. Basically issue **mplayer *file* or *stream*.**

Ex:

```
mplayer -aspect 16:9 http://bglive-a.bitgravity.com/twit/live/high
```


You might want to check out gmplayer which is a gui:

```
sudo apt-get install gmplayer
```

---

### Post by Smart Viking on 2011-01-15
mplayer is a terminal program.
Try launching "mplayer -gui" <- will probably don't work.
To play play video with mplayer:
```
mplayer /path/to/video.ogv
```

Read the man page for mplayer
```
man mplayer
```

Maybe you where looking for totem?

---

### Post by Jetro on 2011-01-15
Ah, thank you people. :) I actually managed to open the desired file in Mplayer by using Smart Viking's command.

No, I were not looking for Totem, that is after all the standard player...

I wanted to use Mplayer because it seemed to solve problems many people had with wmv &#8211; windows media audio 9 decoder. Unfortunately, I didn't get any sound in Mplayer either.

Is Gmplayer the same as Mplayer, just with a GUI?

**Edit:** *sudo apt-get install gmplayer* did not work.
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gmplayer

```

---

### Post by Smart Viking on 2011-01-15
> **stmiller said:**
> 

You might want to check out gmplayer which is a gui:

```
sudo apt-get install gmplayer
```

Does not exist in the Ubuntu repos.

There are two front ends to mplayer in the repos, they are "smplayer" and "gnome-mplayer".
To install smplayer
```
sudo apt-get install smplayer
```
to install gnome-mplayer
```
sudo apt-get install gnome-mplayer
```

You can also install themes to smplayer if you want it to look pwned/1337
```
sudo apt-get install smplayer-themes
```

:-\"

---

### Post by akand074 on 2011-01-15
SMPlayer is the best I hear, I still use VLC but I have SMPlayer as my backup with a source built mplayer with all the libraries so it can run virtually anything now. Check out [this]("http://ubuntuforums.org/showthread.php?t=1542240") tutorial if you are interested.

---

### Post by Jetro on 2011-01-15
Once again, thanks. :)

I installed something called mplayer-gui and it was something like that I was looking for. It couldn't play the file at all.
I will check out that tutorial later. :) It looked complicated like hell, though. :S

---

### Post by andrew.46 on 2011-01-15
Hi Jetro,

> **Jetro said:**
> I will check out that tutorial later. :) It looked complicated like hell, though. :S

Well I have have actually simplified it enormously just recently so now it consists of a series of code blocks that can be copied and pasted directly into a terminal. I simplified it so that people who do not routinely compile software would perhaps be gently eased into the process :).

Andrew

---

### Post by NightwishFan on 2011-01-15
Edit, nvm, packages changed in new releases.

---

