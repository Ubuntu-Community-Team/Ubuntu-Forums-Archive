---
title: "can't watch movies with Mplayer etc."
date: 2010-08-23
forum: New to Ubuntu
---

### Post by agramahisi on 2010-08-23
Hi!

I can't watch video files of my computer. The problem is double: with VLC I can open them, but my VLC shows green and red stripes throughout the whole movie, so that's not really nice. (I already uninstalled and reinstalled VLC, but it's still the same)
With other programs, like Mplayer, Movie Player, Xine, etc. the program just doesn't open the file. 

Now I really don't understand anything (yet) of computers, but I already checked for help on this forum and elsewhere on the internet and didn't find a solution. The most repeated advice I found was installing these things:                                   

libdvdread4 libdvdcss2 w32codecs                                   ubuntu-restricted-extras


But it's still not working... can anyone help me?


Thanks!

---

### Post by LowSky on 2010-08-23
Hi Welcome to the forums!

Sorry your having issues. Can you please give us more information about your hardware, for example do you have a video card and do you know what model, and what type of media your trying to play is it a DVD or some kind of Mpeg?

thank you

---

### Post by agramahisi on 2010-08-23
hm

well, I guess I have a video card, because with my VLC I can see videos (they are just full of coloured stripes, so maybe the card is broken?). If you tell me how I can know what video card I have, I can look it up maybe? 
I'm not talking about dvd's, I guess it are Mpeg files. (It are movies that somebody has put on my computer from his external hard disk, their filenames mostly end on .avi)

I hope this already says a bit more?

---

### Post by realzippy on 2010-08-23
Click on Applications -> Accessories -> Terminal.
type:

```
lspci | grep VGA
```

and post output please.

---

### Post by agramahisi on 2010-08-23
this is the output:

madelief@madelief-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)
madelief@madelief-desktop:~$

---

### Post by realzippy on 2010-08-23
```
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)
```

..that means you have a *VIA S3 UniChrome Pro* graphicscard.Cannot help you,never configurated a VIA device...
Think you should have a look at the "[openchrome]("http://www.openchrome.org/")" project,or start some google search:

S3 UniChrome Pro ubuntu lucid

Anybody experienced in VIA VGA?

---

### Post by gandaran on 2010-08-23
> **agramahisi said:**
> hm

well, I guess I have a video card, because with my VLC I can see videos (they are just full of coloured stripes, so maybe the card is broken?). If you tell me how I can know what video card I have, I can look it up maybe? 
I'm not talking about dvd's, I guess it are Mpeg files. (It are movies that somebody has put on my computer from his external hard disk, their filenames mostly end on .avi)

I hope this already says a bit more?
hi
in the VLC preferences video settings change the video output driver to X11 if it is set to Xv or vice versa, one of them will fix the issue.
and you can do the same on every other player like mplayer, go to preferences video output and change the driver.

---

### Post by agramahisi on 2010-08-24
waaw, thanks a lot! With VLC it's working now, no stripes at all anymore!
With the other programs I'm unable to change the output (they just don't give me that option), but at least I have one program with which I can watch movies now. I will just use Mplayer for music then, and VLC for movies.

thanks a lot!

---

### Post by gandaran on 2010-08-24
> **agramahisi said:**
> waaw, thanks a lot! With VLC it's working now, no stripes at all anymore!
With the other programs I'm unable to change the output (they just don't give me that option), but at least I have one program with which I can watch movies now. I will just use Mplayer for music then, and VLC for movies.

thanks a lot!
look again in mplayer preferences, it has that option to change the output driver or it used to have, I haven't used mplayer for o long time now so I cant be sure.
for the other player's like totem open the terminal and type **gstreamer-properties** then change the output driver.

---

### Post by andrew.46 on 2010-08-24
Hi agramahisi,

Pick up a copy of SMPlayer (a quality frontend for MPlayer):

```
sudo apt-get install smplayer
```

and you will find it quite easy to change video output in the preferences section...

Andrew

---

### Post by agramahisi on 2010-08-25
Yep, I've been able to change that now, so now I can watch the movie, but some of them don't have audio now. So I went to "audio" and changed the "track" from track 0 to track 2 (there's no track 1 in that movie) but there's still no audio. Shut I also change the audio output now, and if yes, to what?

---

### Post by andrew.46 on 2010-08-25
Hi agramahisi,

If the sound only fails on *some* of the files you may be missing the relevant codec. If the sound fails on *all* files, and you have system sound, you could try changing the audio out to pulse, alsa or oss.

All the best,

Andrew

---

### Post by agramahisi on 2010-08-27
hi!

yes, it appears to be the codec that is missing then. but it doesn't matter, I will just keep two programs, one for music and one for movies (VLC does read the audio of those movies).

Thanks a lot!

---

### Post by andrew.46 on 2010-08-27
Hi  agramahisi,

> **agramahisi said:**
> yes, it appears to be the codec that is missing then. but it doesn't matter, I will just keep two programs, one for music and one for movies (VLC does read the audio of those movies).

Mind you if vlc can play the audio that MPlayer fails on you can identify the audio stream from:

Tools --> Codec Information

and then fit out MPlayer to play the audio :).

Andrew

---

### Post by no2498 on 2010-08-27
this should help with totem and smplayer




5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    



btw this comes from the cheese help faq's

---

### Post by agramahisi on 2010-08-28
yes, I'm back.. 

I'm sorry but I really don't understand anything of all this stuff... so I checked in VLC like you said, and it says this:

stream 0: 
type: audio
codec: mpga

stream 1:
type: audio
codec: mpga
channels: dual-mono
sample-rate: 48000Hz
bit-rate: 128Kb/s

So, I suppose I have to find that mpga codec for Mplayer, but how do I find it? My search on the internet has been quite unfruitful so far. (Or at least that's what I think) The things that I find, like e.g. Xvid Media Codec, say that they are for windows or mac, or can I also use it with ubuntu? 

I'm sorry for my ignorance, but I'm learning!

---

### Post by andrew.46 on 2010-08-28
Hi agramhisi,

> **agramahisi said:**
> 

```
stream 1:
type: audio
codec: mpga
channels: dual-mono
sample-rate: 48000Hz
bit-rate: 128Kb/s
```


Seems odd that vlc plays this but not MPlayer, does MPlayer play mp3s for you? Here is a test file, it is about 8 megs and a nice tune as well :). Just paste this command into a Terminal and the file should land on your Desktop:

```

cd $HOME/Desktop && wget http://www.andrews-corner.org/samples/Revelation_21.mp3

```

I would be interested to hear if SMPlayer can play this file...

Andrew

---

### Post by agramahisi on 2010-08-28
hi andrew!

this is the answer of the terminal:

madelief@madelief-desktop:~$ cd $HOME/Desktop && wget [http://www.andrews-corner.org/samples/Revelation_21.mp3](http://www.andrews-corner.org/samples/Revelation_21.mp3)
--2010-08-28 18:49:31--  [http://www.andrews-corner.org/samples/Revelation_21.mp3](http://www.andrews-corner.org/samples/Revelation_21.mp3)
Resolving [www.andrews-corner.org](www.andrews-corner.org)... 69.163.193.141
Connecting to [www.andrews-corner.org|69.163.193.141|:80](www.andrews-corner.org|69.163.193.141|:80)... connected.
HTTP request sent, awaiting response... 403 Forbidden
2010-08-28 18:49:33 ERROR 403: Forbidden.

So as you see it didn't install it, and I can't go to it manually neither. But Mplayer does play mp3's, although there's an error message that says: ADecoder preinit failed. But it does play the files, and smplayer too!

---

### Post by agramahisi on 2010-08-28
this is the message that Mplayer gives for the movies he doesn't play the sound of: 
cannot find codec for audio format 0x50

---

### Post by andrew.46 on 2010-08-28
Hi agramahisi,

Oops, I neglected to fix the permissions on the mp3 on my site :(. All fixed now:

```

cd $HOME/Desktop && wget http://www.andrews-corner.org/samples/Revelation_21.mp3

```

Although by the sounds of it you should have no trouble playing this. As or the troublesome file could you test again from the commandline this time explicitly specifying the audio streams:

```
mplayer -aid 0 my_file
mplayer -aid 1 my_file
```

In each of these examples you will need to change 'my_file' to the actual name of your troublesome file. If you are not used to the commandline you can select the streams from 'Audio --> Track' in SMPlayer.

Andrew

---

### Post by agramahisi on 2010-08-30
ah, nice! Mplayer plays the sound of your file, although it also gives the error message 'ADecoder preinit failed.' 

for the rest, I don't know what happened: I typed what you said in the  terminal, and at first it didn't work (not changing the audio track  manually in SMplayer neither), and suddenly I open that movie again with  SMplayer and it reads it? and the only answer the terminal gave to me  was this:


madelief@madelief-desktop:~$ mplayer -aid 0 /home/madelief/Desktop/paris je t'aime.avi
> 


">" Has that little answer done the thing?? It really seems impossible to me! Isn't mplayer just playing with me? 

Now I closed smplayer again and tried to open the file, and it did play  the sound, until I manually changed the audio track again, and now I  cannot get it to work anymore..
Now I again put that message in the terminal and it works again! So,  does that mean that everytime I have an audio problem with movies I can  do it like that, no?

waaw, andrew! thanks a lot! you opened a new world for me! :)

---

### Post by andrew.46 on 2010-08-30
Hi agramahisi,

There is an old problem with MPlayer where it has some trouble dealing with oddly labelled audio tracks, and yours seemed to have 2 audio tracks but I suspect only one of these is real. This can be overcome by selecting the tracks manually with -aid (audio id). I am not completely sure if this flaw in MPlayer is fixed in more recent versions, I run the svn MPlayer but I have never actually come across a media files with audio streams like this.

BTW you will need to escape the filename, which has spaces in it in the following manner:

```
mplayer -aid 0 [COLOR="Red"]**'**[/COLOR]/home/madelief/Desktop/paris je t'aime.avi**[COLOR="Red"]'[/COLOR]**
```

and then it should play with either -aid 0 or -aid 1 from the terminal. Your copy of MPlayer I presume came from the Lucid Ubuntu repository?

Andrew

---

### Post by agramahisi on 2010-08-30
hi!

I suppose that indeed only the 0 is the real one, the second one doesn't give any result. I installed Mplayer a few weeks ago but I really don't remember if I downloaded it from the internet, or if it was in my Ubuntu Software Center on the computer... if been looking in so many places for so many things the last week that my memory is a bit mixed up now.

Seen the fact that SMplayer is reading it well, and Mplayer itself not, does that mean that I can erase Mplayer? or will SMplayer not work anymore then?

*judith

---

### Post by mc4man on 2010-08-30
> does that mean that I can erase Mplayer? or will SMplayer not work anymore then?
smplayer is a 'frontend to mplayer'. in other words it uses your installed mplayer.
Remove mplayer and you'll lose smplayer

> seems odd that vlc plays this but not MPlayer

While I've never had the occasion to see locally have noticed something with online streams that contain multiple audio and or video streams.

vlc will default to the highest quality stream where mplayer will always use the first stream (aid 0 or first listed vid 

There was a thread/posts some time ago that demonstrated this pretty clearly..

---

### Post by agramahisi on 2010-08-31
Hi!

well, then I will let them both live. Thank you all for helping me, I've learnt how to know which video card I have, how to make the video quality better and how to play sound in the video when the program doesn't want it.. I'm satisfied! :)

Judith

---

