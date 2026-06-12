---
title: "Mp3 and WMA convert to AAC"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Ladychanta on 2009-08-06
I have a Nintendo DSi, and to use the music function on it I need to convert my music files to AAC.    I am new to Ubuntu and am still trying to figure this out.  Right now my media players are Banshee and Rhythmbox (which I don't care for), and my OS is 8.1.  What do I need to download to be able to conver MP3 and WMA files to AAC?  Also once done will I be able to keep my MP3 and WMA formatted songs or is it that once they are converted I'm stuck with them as AAC files?

I am a newb when it comes to comand script, and I don't like messing in my terminal unless I have too.  So if you could please give me newb friendly instructions.  Thank you very much.
-LadyChanta

---

### Post by bodyharvester on 2009-08-06
> **Ladychanta said:**
> What do I need to download to be able to conver MP3 and WMA files to AAC?  Also once done will I be able to keep my MP3 and WMA formatted songs or is it that once they are converted I'm stuck with them as AAC files?

hi, :)

try this, [http://www.creationrobot.com/2005/04/convert-mp3-to-aac-easily/](http://www.creationrobot.com/2005/04/convert-mp3-to-aac-easily/)

it uses itunes, i dont trust most converters on the internet, im not saying they are all evil though :p

i dont have a clue how itunes works, though if you have to download it and run an executable (.exe) file open "add/remove applications" and install WINE then the executable will run in WINE

good luck

---

### Post by SaaTeeVaaGreen on 2009-08-06
i used to use a program called dbpoweramp music converter when i was a window$ user and found it very useful. it will do the conversion you require (though you may need to install extra codecs first).

you will need to run it through wine to get it working, but it should work fine. you will also be able to keep the original music files, just need to select the option when you use it.

there is more than likely a linux equivalent available in the repositories, i just dont know what it is!

---

### Post by jacklinux on 2009-08-06
> **SaaTeeVaaGreen said:**
> i used to use a program called dbpoweramp music converter when i was a window$ user and found it very useful. it will do the conversion you require (though you may need to install extra codecs first).

you will need to run it through wine to get it working, but it should work fine. you will also be able to keep the original music files, just need to select the option when you use it.

there is more than likely a linux equivalent available in the repositories, i just dont know what it is!
for windows your right. However on linux it crashes more often than not via WINE.

---

### Post by Ladychanta on 2009-08-06
Ok I have wine.  But I would still like to find a program that will help me convert mp3 to aac.   if any one knows of a program i could use please let me know.

---

### Post by andrew.46 on 2009-08-07
Hi Ladychanta,

> **Ladychanta said:**
> Ok I have wine.  But I would still like to find a program that will help me convert mp3 to aac.   if any one knows of a program i could use please let me know.

If you do not mind working on the commandline the program FFmpeg will do this quite easily. Have a quick look at:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

for a guide to getting the most out of your copy of FFmpeg. A typical conversion from mp3 to aac would be:

```
ffmpeg -i infile.mp3 -acodec libfaac -ab 128k outfile.aac
```

with many other possibilities available with other options.

All the best,

Andrew

---

### Post by mikechant on 2009-08-07
I use the gui application 'soundkonverter' for all my nusic conversion needs. It's in the repositories. Note there is also a different program called 'soundconverter'!

---

### Post by Ladychanta on 2009-08-07
> **mikechant said:**
> I use the gui application 'soundkonverter' for all my nusic conversion needs. It's in the repositories. Note there is also a different program called 'soundconverter'!

I found the soundconverter...and it will do aac to mp3 but not the other way round.  but i'll try the other one thank you.

---

### Post by fennec_fox on 2009-08-07
Try downloading winff . I believe it's in add/remove. It's at least in synaptic. If you do it through synaptic you might have to install ffmpeg separately. 

winff provides a gui for ffmpeg. Then you can just load the file, go the drop down and choose audio. Then choose what format to convert to.

---

### Post by Ladychanta on 2009-08-08
I really apriciate all that you guys have done but me but I've tried everything but the one that has me go in to the terminal.  I don't know my way around the Terminal, and I"m scared I might screw up my computer.

Soundconverter and Soundkkonverter both are nifty but they don't convert TO AAC
 Please if you know for a fact that a program will convert TO AAC then please let me know.

Thanks bunches
-Ladychanta

---

### Post by mc4man on 2009-08-08
Don't really use soundKonverter but...

Sounkonverter will encode to aac (m4a) including from .mp3

It may do some wma's (wma2,  and depending on setup wma3. While it should do wmal thru mplayer it doesn't seem to work, maybe could be 'fixed'

Make sure you have faac installed (soundkonverter uses faac, not libfaac0

To check open soundkonverter -> settings -> configure soundkonverter -> backends, compare to screenshot

SK will not transfer tags, for that there is a nautilus script that is very easy to use - nautilus-script-audio-convert. Is very easy to use though for a batch convert you will need to use the terminal. (just ask, not very hard to do, will not 'mess up' your install

---

### Post by bodyharvester on 2009-08-08
pffft.

trust someone to come up with an easy solution after ive downloaded crappy converters to find one that works    -_-

lol

---

### Post by stinger30au on 2009-08-08
> **bodyharvester said:**
> pffft.

trust someone to come up with an easy solution after ive downloaded crappy converters to find one that works    -_-

lol


if u using 9.04 get winff from repos

it is a giu front end and works well for converting this kind of stuff

---

### Post by fennec_fox on 2009-08-11
I just found this today and I thought of this thread. If you're still reading this thread you might want to try this. 

[http://www.gtk-apps.org/content/show.php/Audio%2BVideo%2BImage%2BText%2BISO+Convert?content=92533](http://www.gtk-apps.org/content/show.php/Audio%2BVideo%2BImage%2BText%2BISO+Convert?content=92533)

---

### Post by timcredible on 2009-09-29
winff works great.  my grandson just got a dsi and i tried soundkonverter first, the dsi didn't like the files.  i tried winff and it works perfect.  why didn't nintendo just use .ogg files?  they're open source and royalty free?

---

### Post by mlitty on 2009-12-20
Winff is great, but there's an easier way.

Check out the post here [http://ubuntuforums.org/showthread.php?t=407184](http://ubuntuforums.org/showthread.php?t=407184)

basically, you install 
```

sudo apt-get install nautilus-script-audio-convert nautilus-script-manager
sudo nautilus-script-manager enable ConvertAudioFile

```

and then restart nautilus.  You should then be able to right click any sound file or group of sound files and choose to convert it to any of several formats.

This is how I convert files for my daughters' DSi's.  The converter converts them to "filename.aac" and I rename them to "filename.m4a".  That's all the tinkering it needed.

---

