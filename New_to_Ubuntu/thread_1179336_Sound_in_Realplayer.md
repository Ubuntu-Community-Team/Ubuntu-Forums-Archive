---
title: "Sound in Realplayer"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by zcacogp on 2009-06-05
Chaps, 

I'm running Ubuntu 9.04, and having fun and games (!) with sound in Realplayer. I have RealPlayer11GOLD installed, as well as flashplayer and a few other things. I have all the Ubuntu updates installed. 

If I boot up firefox, I can navigate to a BBC page which has video on it (The Apprentice ones, for instance - here: 

[http://www.bbc.co.uk/apprentice/episode-extras/video/item_200216.shtml](http://www.bbc.co.uk/apprentice/episode-extras/video/item_200216.shtml) ) 

... and it will work fine - video and sound. 

ALTERNATIVELY, I can navigate to a live radio stream, such as Radio 4 (here: 

[http://www.bbc.co.uk/radio4/](http://www.bbc.co.uk/radio4/) ) 

... and that will play just fine, in either in-screen or pop-out mode. (In fact, I am listening to it now!) 

The problem comes when I try to swap from one to the other - if I close the tab relating to one programme and try to boot the other, I get no sound (so if going from radio to video, I don't get any sound on the video. If I go from video to radio, the radio is silent). I need to close firefox and re-start it to get sound. 

It almost feels as if the audio part of either programme cannot release control of the audio system on the computer, and I need to close firefox and re-start it for the control to be relinquished. (But this is only a guess - I could be wrong.) 

As an aside, I installed mplayer and found that it caused firefox to crash whenever I tried to listen to a radio station, so removed it.


Oli.

---

### Post by GMachine_24 on 2009-06-05
Two things:

Linux has often had problems with sound. Reboots or restarts of programs aren't that unusual.

Having said that, there also have been problems with the BBC and various Ubuntu/Linux media players.

For example, Mplayer, when it's installed, has typically been the default program which FireFox has tried to use to play BBC (and other) files - even though it is not capable of doing so. Don't ask my why this is. But if, in the firefox address window, you type in about:config when Mplayer is installed, you will find Mplayer as the first listing, ahead of Real Player, to play Real Audio files - even though Mplayer can't play them. You have resolved this problem by removing Mplayer and its setting in about:config should be gone, as well.

Sorry to take so long to get to the point here, but I did a lot of research about sound problems with the BBC and other audio sources, the results of which are in this somewhat verbose thread:

[http://ubuntuforums.org/showthread.php?t=1016004](http://ubuntuforums.org/showthread.php?t=1016004)

It does not specifically address your issue - of having to restart Firefox when switching from audio to video on the BBC - but perhaps there is something of value for you in the thread.

Best of luck.

GM

---

### Post by zcacogp on 2009-06-07
GMachine_24, 

Thanks for answering. Sorry to take a while to get back to you. 

OK. About the fact that Ubuntu is not that great with sound. I guess it's another ... feature. (I'm trying not to be negative, but I do seem to have come across a number of holes in the 'ubuntu experience' in the last couple of weeks. Ho hummm.) 

That thread you linked to is one of several I looked at in trying to get the machine playing video and sound. I didn't read it in that much detail; on your recommendation I'll go back and have another crack at it. 

Thanks again. (Please don't take this post as being a pop at Ubuntu - it's not intended to be. I guess that the rose-tinted specs are just starting to slip tho'.)


Oli.

---

