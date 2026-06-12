---
title: "Creative Zen Vision:M not detected by anything - help?"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by robine on 2009-12-14
Hi all,

This is my first post here. I wanted to try and figure out as much on my own as possible. However, I'm going a bit crazy, so I finally decided to ask you experts for some help!

I just switched to Ubuntu 9.10 from WinXP. I love it! Except I can't figure out how to get Ubuntu to recognize my Creative Zen Vision:M mp3 player.

I've tried Amarok, which works for others; it won't for me. It doesn't detect the mp3 player (and doesn't even play my mp3s, for some reason).
I've tried Gnomad2, which doesn't detect the player.
I've tried downloading both libmtp and libusb, but they both come as tarball.gz files, which I have no idea how to execute! (They contain files named "Install" and "Read Me" which only confuse me more.)

How can I access my Creative Zen Vision: M (30gb) on Karmic Koala? 
PLEASE help; any and all suggestions most welcome.

Thanks ;)

---

### Post by bedfojo on 2009-12-14
Try running gnomad2 as root. Use:

gksu gnomad2

---

### Post by robine on 2009-12-14
Thanks for the suggestion. I wasn't sure what you meant by running it "as root", but I suspected that you meant that I should type it in Terminal. So, I did. What happened:

PDE device NULL.

I then realized that the Creative Zen wasn't in the docking station (plugged into USB port). I docked Creative Zen. Tried again:

Device or resource busyLIBMTP PANIC: Unable to initialize device
busyPDE device NULL.

When I plugged it in, a window popped up asking me which program I wanted to open the device with (suggested: Rhythmbox). I suspect this is the reason for the "resource busy" message above. I tried once more:

getting file metadata (this message briefly flashes on screen)
No jukeboxes found on USB bus.

:(

---

### Post by guv999 on 2009-12-15
When you attach the Zen does Ubuntu recognise and mount it?
If it does I seem to recall the following helped me......
Unmount the device
Then launch Gnomad
You should now see all the files on the player

---

### Post by brophus on 2009-12-16
My Zen vision M is automaticly mounted in  Karmic. I used to have to use banshee and gnomad. Good luck but try just pluging it in.

---

### Post by robine on 2009-12-17
> **guv999 said:**
> When you attach the Zen does Ubuntu recognise and mount it?
If it does I seem to recall the following helped me......
Unmount the device
Then launch Gnomad
You should now see all the files on the player

Thanks for the suggestion.
I tried what you said. Plugged it in - Ubuntu recognized its presence and mounted the device (and showed the Creative Zen icon on the desktop). A window popped up asking how I would like to open it - using Rhythbox or to "view files". I chose view files. I can SEE the folders on the mp3 player, and can click and drag files into the folders, but can't access any of these items from the Creative Zen itself.

Anyway, I unmounted it by right-clicking on the desktop icon. Opened Gnomad... which promptly said, "No jukeboxes found on USB bus." :(

---

### Post by robine on 2009-12-17
> **brophus said:**
> My Zen vision M is automaticly mounted in  Karmic. I used to have to use banshee and gnomad. Good luck but try just pluging it in.

Hi - how did you get Karmic to recognize it? Does it just take a few dozen tries? (Joke :P)

I've tried just plugging it in. The player is now mounting (shows Creative Zen icon on desktop), but any files that I add aren't accessible through the Zen itself. I don't get it...

---

### Post by shiroyoshida on 2009-12-26
I've got exactly the same problem with my Creative Zen V Plus and still haven't managed to find a solution. Rhythmbox used to "see" the player but then one day it simply stopped doing that... 

It's one of these times when I'm happy that I also have Windows XP installed on my machine and one of these times that I'm angry that things just don't work across different platforms. 

If I find anything that helps me solve this problem, I'll post it on this thread straight away! 

Good luck :-)

---

### Post by audacs on 2009-12-26
I had a similar problem with Creative Zen V Plus.

As guv999 suggested, my fix was: unmount the device, then open in rhythmbox/amarok/banshee. Make sure that MTP support is enabled in the options of whichever program.

Hope this helps!

---

### Post by rburkartjo on 2009-12-26
rob try this worked for me submitted by x14
I found a solution.. it is somehow trivial.. dismount the zen and THEN open it with gnomad2...

---

### Post by shiroyoshida on 2009-12-26
Thank you very much for the suggestion! It did seem to work after a couple of failed attempts and have managed to transfer files over to my Creative Zen. :-) 

Initially it didn't transfer any files as I was trying to transfer an entire folder but it does work when you enter the directory and transfer its contents. 

Thank you all once again for your help!

---

