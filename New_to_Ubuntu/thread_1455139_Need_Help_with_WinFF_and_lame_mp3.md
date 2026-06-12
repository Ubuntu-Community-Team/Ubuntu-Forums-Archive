---
title: "Need Help with WinFF and lame mp3"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by BeatnikBandit on 2010-04-15
Ok my problem is whenever i try to use WinFF to convert files for my rockbox mp3/video player i keep getting the same error ```
Unknown encoder 'libmp3lame'
``` although i have ffmpeg and lame installed so why wont winff understand it? I only use it to convert Xvid .avi Files to .mpeg files that are supported by rockbox which is installed on my mp3 Player. I need this as it is the only program i know of that will convert files to a Rockbox capable Mpeg, Rockbox is made using a *nix capable code so I dot understand why its not working maybe there is another dependency i might need? 

Anyone who uses rockbox would probably know or anyone who uses WinFF for anything else frequently I find it to be a nice fast conversion program too, so hopefully someone out their knows what i need. I thank you.

also anyone who has a rockbox compatable Mp3 player i think its a great firmware and for most players it installs it as a dual boot and it makes my mp3 player do twice as much as it used too and it over clocks it slightly to make it run nice. it comes with video player music player text viewer picture viewer and many other apps from games to other useful things. [www.rockbox.org](www.rockbox.org)

---

### Post by Didius Falco on 2010-04-15
Have a look at this thread - it should solve it for you.

Regards,

Didius

---

### Post by e4uforums on 2010-04-15
I'm pretty new to Linux, so take this as it is...

I find whenever terminal complains about a dependency or complains about something that it can't find or doesn't understand, I often find that I can fix it by entering:

```
sudo apt-get install <that thing it's complaining about>
```

In your case:

```
sudo apt-get install libmp3lame
```

In this case where it's a codec, I believe you'll need the Universe repositories enabled.  This may not be sound advise, but it seems to fix me up more often than not.

Best of luck.

---

### Post by BeatnikBandit on 2010-04-15
Didius Falco -  thank you but I dont know what you tried to link to but its ok, I appreciate the help no mattter what!!

e4uforums - Thank you also as i normally try the same thing sometimes it works sometimes it doesntsometimes i am turned around and install packages i didnt need HEHE LOL but i end up figuring it out in the end.

Well In this case i found out the issue on my own First i want to thank you guys for wanting to help me that is what makes the Ubuntu idea work people care about each other.

Now for thoes who wish to use WinFF to convert video files Easily and quickly here is an issue you need to take care of.

You need first ffmpeg any version of this is fine, i know of cource you need ffmpeg to use a front end for it although you cannot use the ubuntu branded version of libavcodec you should use the unstripped version I know this version works the regular version IDK but the ubuntu version DOES NOT WORK. So basically all I did to fix this was change which version libavcodec i had installed. 

Problem solved!:)

---

### Post by e4uforums on 2010-04-15
Glad it's working.  Thanks for coming back to share the solution.

---

### Post by Didius Falco on 2010-04-15
Oops...:redface:

uhhh...here is that link I *_meant_* to put in that message, just in case anyone else needs it down the road.

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by WinterRain on 2010-04-15
> **BeatnikBandit said:**
> 

You need first ffmpeg any version of this is fine

Installing Winff should automatically download ffmpeg. It has for me, anyway.

---

### Post by 3rdalbum on 2010-04-15
> **WinterRain said:**
> Installing Winff should automatically download ffmpeg. It has for me, anyway.

Yes, but it's not enough to have FFMPEG - you need the packages starting with the word "libav" and ending in "extra" (or, if using Ubuntus 9.04 and earlier, ending in "unstripped"), otherwise you can't encode restricted formats.

---

### Post by BeatnikBandit on 2010-04-16
I installed ffmpeg first so i didn't know what it installs with it. although logically, i should have thought that being a ffmpeg front end application ffmpeg would be a dependency so i am sure it would install ffmpeg on its own as i don't think it would not run at all without it. 
Although the one thing that is important that it does not automatically do is install the Un-stripped version of libavcodec which is needed as for some reason the ubuntu package of this codec does not work, I believe it is as the un-stripped version has more codec's that are not free since anything ubuntu branded MUST be GNU free or else that cant brand it. 
There are several versions of libavcodec but I only know the Ubuntu Branded Version wont work with WinFF but the unstripped Ver Does work I don't know about the other one (thier may even be one more but i am not sure) I dont think Lame mp3 encoder is GNU FREE it may be freeware but but GNU, IDK. 

Let you tell me about my stupidity and how i learned what version of libavcodec i needed: I read the program description in synaptic. (OMG I READ DIRECTIONS AND IT HELPED ME, "One small step for males. One giant, leap for male-kind ") So I'm not gunna lie that's how i found it. 

Wait what did i just say, never mind that i found out because i am such an astonishingly smart male i had an epiphany and BAM everything works. This is how i fix everything its like when i touch something its like a mental connection i just KNOW! ::Cough bull$#!t Cough::

ANYWAY i hope this information helps other Males like me who don't read the directions. 


Also kinda off subject but the reason i use this app 90% of the time is for my RockBoxed MP3 player. I purchased a Sansa E260 specifically because it was the cheapest and best for the price that supported rockbox. anyone who owns an MP3 player should check it out (it supports most Ipods, it does not support any touch version as it is very different and for the shuffle as it has no GUI.) It dual boots ALL the time you will not Brick your player and its work the try you might really like it. It is IMO 100% better than the Original firmware, it supports themes so i can pick the look, it gave me great Video Playback, it gave me apps and games, it runs faster than the OF, Seriously i cant tell you you have to check it out, I am not sure but i think they have a emulator that you can download and check out first before you even install it, it even has an installer. go here to look at it if this has caught your attention. [www.rockbox.org]("http://www.rockbox.org") just look personally I don't care if you use it i just want to share it as its Great IMO and i think if you can use it it will make your experience much better. My sansa cost me $30 (from WOOT) and has more options than Ipod version

---

