---
title: "ATI Video Cards Help, Can you do this?"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by altech6983 on 2009-09-03
Hello,

I'm back again and I need you alls help. Okay what I am trying to do is run two different video cards. The reason for this is because I live in a four person apartment (college) and we don't want the a/c bill to be too high so it is set on 73F. Due to that it gets pretty hot in my room, especially at night when I close the door.

I have a ATI HD 4870 X2. Out of those two I know it is the ATI card because when you stick your hand behind the computer where the card exhaust is it is like a space heater. 

I figured since I don't play games 24/7 and most of the time just use it for browsing and downloading (sometimes I do transcoding and encoding but that doesn't need the video card), that there was no reason to be running the card all the time. 

I had a HD 4350 laying around so I thought that maybe it would be as easy as restarting x or something like that. I made a backup copy of the xorg.conf for the 4870 and then I shutdown, removed the 4870, put in the 4350, and booted. I had some problems but after I ran aticonfig --intial -f it created the 4350 config file. I then backed that up and shutdown, put the 4870 back in (it now has both 4350 and 4870 installed) and left the config file set for 4350. When I started up it said (EE) No devices found and had the graphics restoration box thing pop up.

After trying a few things (one of them aticonfig --initial --input=/etc/X11/xorg.conf <-- this xorg file is the 4370 one, startx but it just said that there was no device section for PCI:1, and PCI:5, and that it couldn't find a screen) I couldn't get it to only use one card to startup.

I would really like to be able to switch cards from my desktop but I know I won't be able to do that without at least changing (copying the correct card config from the backup?) and restarting x. I would rather do that than restarting the computer but if I HAVE to restart that would be fine also. 

So can y'all offer any help please,
altech6983

---

### Post by schwascore on 2009-09-06
This might help put you on the right path as far as the xorg .conf files.

[http://ubuntuforums.org/showthread.php?t=53966](http://ubuntuforums.org/showthread.php?t=53966)

---

