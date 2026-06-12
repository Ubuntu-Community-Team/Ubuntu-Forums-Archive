---
title: "tv tuner problem"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by juptin on 2010-05-09
I am a beginner on ubuntu 10.04 LT use and have only had it installed for a couple of days.
My tuner is Compro videomate T100 and worked on Windows 7. 
t is recognised by the system as Compro Videomate T750 which ain't right and I don't really know how to go about getting it fixed. I have checked the forums but, found it difficult to understand what I need to be doing to fix it. The tuner doesn't work in metv. Any help will be greatly appreciated.

---

### Post by inameiname on 2010-05-09
Maybe this posting will help you get started:

[http://ubuntuforums.org/showthread.php?t=1472297](http://ubuntuforums.org/showthread.php?t=1472297)

...and here is a link to see if yours is on the list. A similar is, (DVB-T200), so perhaps it'll work anyway. Sometimes similar ones will work just fine, it's just nobody's tried it or wrote of their experience...:

[http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards](http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards)

...further hope is here, saying that the T200, T200a, and T300, are also supported, so again, who knows:

[http://www.linuxtv.org/pipermail/linux-dvb/2007-April/017480.html](http://www.linuxtv.org/pipermail/linux-dvb/2007-April/017480.html)

....unfortunately, this posting found on this forum doesn't help in my opinion, of course it was written a long while ago so perhaps it's been fixed....:

[http://ubuntuforums.org/showthread.php?t=473595](http://ubuntuforums.org/showthread.php?t=473595)

....basically I'd give it a shot and follow how I explained to that dude from the first link I gave and see what happens. Maybe it'll work for you...

....hope any of this helps...

---

### Post by juptin on 2010-05-09
Thank you my friend. I will try these and get back back to this thread

---

### Post by juptin on 2010-05-09
Deep, deep despair. I still haven't managed to get the card to work despite your helpful links, which have at the very least got me accustomed to the ubuntu system. I have however, found the following information that I think may at least assist you or others to perhaps point me through further avenues; 

3:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

Who knows

---

### Post by inameiname on 2010-05-09
Hmmm, well I'm not sure what to do with that info you gave. Is it what you got in the terminal from your card? If so, maybe that means it's been recognized as something at least. That's something. I'm sorry I'm not much help here. It's beyond my expertise in figuring out all that stuff.

Now, if you decided to try my choice in applications to use, it's possible it's those applications that are to blame, as there is more required for your card to even be noticed.

For TVtime, (I use for analog cable, and S-Video and composite input (ie, VCR hooked up)), you first need to ensure your tv tuner is video0. If say you have webcam, sometimes it's video0, and so for tvtime to pick up the tv tuner card and not the webcam, you gotta put this in terminal:

tvtime-configure -d /dev/video1          (or video2, or video3, or whatever) 

...and then you need to make a stationlist.xml which is in the .tvtime folder of your home directory (can also do in tvtime itself), by:

tvtime-scanner

....and tvtime flaw is no audio sometimes, so if there isn't any, if you get to this point, open tvtime this way (I use this script to do so):

   [FONT=&quot]#!/bin/sh
                  sox -s -r 32000 -c 2 -t alsa hw:1,0 -s -r 32000 -c 2 -t alsa hw:0,0 & 
                  tvtime
                  t=`pidof sox`;
                  kill $t;
[/FONT]
  
....and to record:


  [FONT=&quot]sudo arecord -D hw:1 -f dat | aplay -f dat[/FONT]

...and finally just make sure you have the correct source in tvtime, such as 'tv' or 'svideo' or 'composite'...

For SMplayer, (I use for dig[FONT=Verdana]ital broadcast), you first need to create tv station list for your area, and one of these works, creating a channels.conf in '.mplayer':

[/FONT]    [FONT=Verdana][FONT=&quot]scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB > ~/.mplayer/channels.conf
scan /usr/share/dvb/atsc/us-NTSC-center-frequencies-8VSB > ~/.mplayer/channels.conf
scan /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256 > ~/.mplayer/channels.conf
scan /usr/share/dvb/atsc/us-Cable-IRC-center-frequencies-QAM256 > ~/.mplayer/channels.conf
scan /usr/share/dvb/atsc/us-Cable-HRC-center-frequencies-QAM256 > ~/.mplayer/channels.conf
scan /usr/share/dvb/atsc/us-Cable-EIA-542-HRC-center-frequencies-QAM256 > ~/.mplayer/channels.conf
scan /usr/share/dvb/atsc/us-Cable-EIA-542-IRC-center_frequencies-QAM256 > ~/.mplayer/channels.conf

Basically your card will do nothing at all unless:

1. Have firmware in firmware folder
2. Have DVB-APPS and V4L tar files installed correctly
3. TVTime's source to the correct Video0 or Video1 or whatever and channel list done
4. SMplayer's (mplayer's) channel list done
[/FONT][/FONT]

---

### Post by juptin on 2010-05-10
Still tinkering with the issue, no joy yet. I don't suppose you could indicate what firmware I would need, I have no idea.

---

### Post by inameiname on 2010-05-10
I'll look around. I'd definitely check out linuxtv.org of course. 

Looking at this again:

3:06.0 Multimedia controller: Philips Semiconductors  SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

...and that site, it's interesting [VideoMate DVB-T200]("http://www.linuxtv.org/wiki/index.php/Compro_VideoMate_T200") (which seems to work) uses a Philips [SAA713_4_. ]("http://www.linuxtv.org/wiki/index.php/Philips_SAA7134")tuner/chip, which looking at yours is very similar. and clicking on it's link from: 

[http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards](http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards)

I noticed that under how to make it work you insert in the terminal: 

modprobe saa7134-dvb 

...so maybe 'modprobe saa7131-dvb' will do something, idk. Not sure what modprobe even does. 

What's also funny is looking at that same link above, above VideoMate DVB-T200, there is a card called Club 3D Zap-TV-2202, which uses a saa7131, whatever that means, and it works. Says it's installed: modprobe saa7134 card=94.

Looks like maybe you can just plug and play and see what happens. Guessing this is the firmware that you are asking, but I don't want to lie and say I know really anything about this stuff. Just play around on that main site. I haven't looked at it in detail either, but think I'm gonna look at it a little more in depth.

UPDATE: I ran across this page page Googling "Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)":

[http://ubuntuforums.org/archive/index.php/t-1050253.html](http://ubuntuforums.org/archive/index.php/t-1050253.html)

It tells of how to find the firmware for a tuner that has the same "Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)" as you. So maybe that'll help.

---

### Post by Peter J Schoen on 2011-04-24
> **juptin said:**
> I am a beginner on ubuntu 10.04 LT use and have only had it installed for a couple of days.
My tuner is Compro videomate T100 and worked on Windows 7. 
t is recognised by the system as Compro Videomate T750 which ain't right and I don't really know how to go about getting it fixed. I have checked the forums but, found it difficult to understand what I need to be doing to fix it. The tuner doesn't work in metv. Any help will be greatly appreciated.
Hi Juptin,
How did you go with configuring this card?

And if so [COLOR=Red]**HELP!**[/COLOR]..

---

