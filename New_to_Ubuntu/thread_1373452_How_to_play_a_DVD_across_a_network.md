---
title: "How to play a DVD across a network?"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by zcacogp on 2010-01-05
Chaps, 

I am trying to do something which I think must be incredibly simple, but I just can't make it work. Let me try and explain the situation. 

I have two machines. "Desktop", which has a DVD drive, and "X61S2" which has no DVD or CD drive - it's a laptop. 

I want to be able to play a DVD which is in the DVD drive on the desktop machine on the laptop. 

This can't be hard - and yet I have been sweating over this for a good couple of hours now. 

The DVD drive on the desktop machine can be 'seen' on the laptop machine using SAMBA. (I don't know whether this is 'mounted' on the laptop or not. Does this matter? I know that I have an icon which appeared on the desktop of the laptop saying "DVD drive on desktop" - "DVD drive" is what I called the shared DVD drive on SAMBA.") 

However, if I open the DVD drive link, while I can see the directories "Audio_TS" and "Video_TS", and open them, I can't play the DVD on the laptop. 

If I open "Movie Player", I can see the drive and the files within the drive, but again I can't play them. (It says it is playing but doesn't do anything - the time doesn't advance, it says the length is 0:00, and nothing is shown on screen.) 

I have downloaded VLC onto both machines and I CAN stream the DVD using VLC, but only the introductory bit of video. I can't control the DVD from the laptop, therefore I can't actually go into any of the scenes on the DVD, or indeed tell it to 'Play Movie', so it isn't of any great use.

If I try to 'Open Disk' in VLC on the latop, I can see the "DVD Drive" drive, but if I click on it and try to open it I am told that "mount: special device /dev/scd0 does not exist", and it won't go any further. (The disk will play fine on VLC or indeed on Movie Player on the desktop machine, where the DVD drive is.) 

So ... where do I go from here? I am stuck. The only other thing which I can say which may be helpful is that I copied one of the files from "Video_TS" onto the laptop, and it is called VTS_01_0.VOB. If I try and play this file directly on Movie Player it also doesn't play - it again claims to be playing but the time never advances and it doesn't actually do anything. This is making me wonder whether the problem isn't the transfer of the data across the network, it is that the laptop won't play DVD's. I have hence installed just about everything that seems relevant to playing DVD's on the laptop (medibuntu, libcss etc etc etc) and that has made no difference at all. 

Bear in mind that I did manage to stream the DVD across the network using VLC (but this didn't allow me control of what I was watching.) I don't know whether this is a useful diagnostic or not. 

Any assistance would be most welcome. Thanks in advance for any help you can offer! 


Oli. 

P.S. Probably should add - both machines are using 9.10 Karmic, and connected by a wireless network that otherwise seems to run fine.

---

### Post by llamabr on 2010-01-05
if you actually have desktop mounted, I'd use mplayer, not vlc.  I'd also mount them with nfs, not samba.

mplayer can play the individual tracks, if vlc can only find the first one.

I'd tell you to read mplayer's man page, but people here lose their mind when someone suggests you read a man page.

---

### Post by zcacogp on 2010-01-06
Llamabr, 

That was very helpful advice - thank you. I looked up NFS, and came to this page: 

[http://www.woollypigs.com/2009/11/ubuntu-network-share/](http://www.woollypigs.com/2009/11/ubuntu-network-share/)

... which talked me through it just fine. Once this was done, and I opened up the DVD on the laptop in Nautilus, it presented me with the option of playing it in Movie Player, which worked a treat! Many thanks, you've solved the problem! 

I think that leaves me with a number of questions about the methods of sharing directories between Ubuntu machines - NFS, SAMBA or CIFS, and why you should choose one over another. I have used SAMBA because other people on here seem to say it is ***the*** way, but there are clearly other ways (that work better, certainly for this exercise.) 

Other questions include why I couldn't share using my computer names (I couldn't make it work with 'desktop' and 'x62s', I had to use IP addresses - 192.168.10.2 and 192.168.10.22 respectively), and also that now the DVD drive is shared on the laptop, I can't eject the DVD from the drive. Somehow I need to get the laptop to 'let go' of the share to allow me to eject it, and I don't know how to do that apart from turning the laptop off ... 

Maybe these are questions for another thread tho'. 

Thanks again for your help Llamabr. As it was I didn't get as far as looking at mplayer - is it better than Movie Player? 


Oli.

---

### Post by zcacogp on 2010-01-06
OK, now I'm throughly p***d off - I've managed to break it!

I removed all of the old SAMBA stuff. 

I tried to use NFS to share all the drives on the desktop to the laptop. I can now share two local drives very nicely, but have managed to break the remote viewing of the DVD's! 

I have tried to put it all back to how it was before, but it still doesn't work. Which is VERY annoying! 

So, without going into all the detail of what I have and haven't done, is there a simple way of removing ALL settings to do with sharing on the two machines (so, everything to do with SAMBA and everything to do with NFS), and start again from a clean slate? That would seem like the best way in; there is something afoot which I don't understand and could spend a long time trying to dig out. 

Again, all help welcomed - thanks. 


Oli.

ETA: For what it's worth, when I now try and play the DVD on the desktop (the machine that the DVD drive is physically installed in), it plays very jerkily, which it didn't before (and I'm not aware of changing any DVD settings on the desktop machine.) While I can see the DVD on the laptop, when I try to play it in the Movie Player, the Move Player window appears, then disappears about 1 second later. 

I have tried MPLayer, as per your suggestion Llamabr, but that didn't work at all.

---

### Post by firefly2442 on 2010-01-06
VLC can stream across a network.  Here is some documentation (there's probably more online).

[http://www.videolan.org/doc/streaming-howto/en/streaming-howto-en.html](http://www.videolan.org/doc/streaming-howto/en/streaming-howto-en.html)

As for not being able to control VLC, I believe you can do it remotely.  If you bring up VLC, click on the View menu, then Add Interface, you can control it via the Web (probably easiest) or Telnet or something.

Actually, it looks like in that link that I gave you there's some information on how to stream a DVD.  I'm no expert as I've never used these features but at least it might give you a starting point.

Good luck. :)

edit: Some VLC HTTP interface documentation:

[http://www.videolan.org/doc/play-howto/en/ch04.html#id310608](http://www.videolan.org/doc/play-howto/en/ch04.html#id310608)

---

### Post by zcacogp on 2010-01-09
Firefly, 

Thanks for this. 

I managed to make it stream, but that wasn't quite what I was looking for ... while I don't really understand the differences in detail, I was trying to simply make the DVD play across the network, without needing to do any initiation on the machine with the DVD drive in it (i.e. without setting off a streaming session.) 

As it is, I made it work. And then managed to break it again! (Although I don't know what I did to break it. There is a thread about it here: 

[http://ubuntuforums.org/showthread.php?t=1376424](http://ubuntuforums.org/showthread.php?t=1376424) ) 

Thanks for your help tho'. 


Oli.

---

