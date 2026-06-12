---
title: "Can't get WoW to run"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Moohasha on 2009-04-24
*First of all, I'm an ABSOLUTE BEGINNER to Linux! I used Unix a little bit in college about 7 years ago, but it was very basic. So keep that in mind before posting things like "just open a terminal and type jfjidsjoi -diasfs -=ji3oijdlk", cause I probably have no idea what you're talking about! ;)*
 
I'm building a new computer in about a month, and when I heard that I could play World of Warcraft in Linux using WoW, I thought I'd give it a try before buying Windowx Vista. So I installed Ubuntu 9.0.4 on my laptop, got the latest version of Wine, and then downloaded an installed WoW (beause I couldn't get it to install from the DVD using Wine). It installed without a hitch (mostly), but now I can't get it to run. When I get to the login screen, the graphics are all jacked up and it eventually crashes. The furthest I've gotten is to the character selection screen.
 
I did Google and read walkthroughs and instructions on installing Wine and WoW on Ubuntu, including some posts on these forums, but they were all for previous versions of Ubuntu since 9.0.4 just came out. I tried both adding **SET gxAPI "opengl"** to the config.wtf file and adding the -opengl flag to the shortcut (seperately, not both at the same time) and still no luck.
 
So my guess is that I need to update my video drivers? When I installed Ubuntu, everything worked (something I really liked :D) so I didn't bother with any drivers.
 
I've seen so many people saying they've gotten it to work, and it's got a gold rating from winehq, so I know that I'm missing something or doing something wrong. I'm open to any and all suggestions since this is just a test machine and I don't care what happens to it. :D

---

### Post by RichardLinx on 2009-04-24
Just open a terminal and type: ```
jfjidsjoi -diasfs -=ji3oijdlk
```
(Kidding)
If you want to play WoW you're going to have to install the drivers for your graphics card. Just go to "System > Administration > Hardware Drivers" and select your graphics card. It should install. (You will need to be connected to the Internet of course).

Did you install Wine from the Ubuntu repository or from the Wine site? There's a chance that the version of Wine in the repo's is an older version then the latest release on the Wine site, though unlikely since 9.04 was only just released.

This might make Installation of WoW a little smoover: [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

Good luck!

---

### Post by El Zoido on 2009-04-24
Should you have the right drivers for your graphics card, followed the instructions and WoW still isn't working you could maybe try using another version of wine.
I once actually had to downgrade to a older version to get it running right.

---

### Post by Moohasha on 2009-04-24
[quote="RichardLinx"]If you want to play WoW you're going to have to install the drivers for your graphics card. Just go to "System > Administration > Hardware Drivers" and select your graphics card. It should install. (You will need to be connected to the Internet of course).[/quote] 
I think I tried that, and there were no options in Hardware Drivers. I don't remember what it said, but I'll check again this afternoon (I'm at work now :()
 
[quote="RichardLinx"]Did you install Wine from the Ubuntu repository or from the Wine site? There's a chance that the version of Wine in the repo's is an older version then the latest release on the Wine site, though unlikely since 9.04 was only just released.[/quote]
I installed it from the website. Again, I think I checked the repo first since that what some guides I had checked recomended, but I didn't find it, either because I didn't know what I was doing or because it wasn't there.

---

### Post by Moohasha on 2009-04-24
Okay, I'm home now and confirmed that there is nothing in the Hardware Drivers window.  It's empty, except for a message at the top that says "No proprietary drivers are in use on this system. :confused:

So do I need to download them myself?  And if so, how do I do that and install them on Ubuntu?

---

### Post by Moohasha on 2009-04-25
sorry to bump, but it looks like things get pushed down really fast on this forum, and I'd really like to get this working.

---

