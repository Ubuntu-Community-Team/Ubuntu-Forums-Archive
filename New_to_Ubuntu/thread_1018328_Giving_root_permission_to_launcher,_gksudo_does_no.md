---
title: "Giving root permission to launcher, gksudo does not work."
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Inxi on 2008-12-22
This is my launcher:

env WINEPREFIX="/home/inxi/.wine" wine "C:/Starcraft/StarCraft"
If I run this, the game works fine. But, to run battle.net and have battle.net not kick me out I need to run it as root.

So, I do: 
gksudo env WINEPREFIX="/home/inxi/.wine" wine "C:/Starcraft/StarCraft"

The pointer turns into the wheel for a sec then it goes back to normal and nothing seems to happen.

Suggestions?

---

### Post by jerome1232 on 2008-12-22
(as much as I think it's a horrible Idea to run a game as root like this)
Shouldn't that be

env WINEPREFIX="/home/inxi/.wine" gksu wine "C:/Starcraft/StarCraft"

Or maybe try it with out all the prefix stuff
gksu wine "C:/Starcraft/StarCraft"

---

### Post by Inxi on 2008-12-22
Hey, if you have a better solution, I'd be DELIGHTED to hear it, because I have been digging this for about 3 hours now and I've been reading the advice of this guy: [http://www.xanga.com/Susiekins/572913682/linux-and-starcraft-battlenet.html](http://www.xanga.com/Susiekins/572913682/linux-and-starcraft-battlenet.html)
Who did it on a much older version of Ubuntu. >_<

None of those things you listed work, including gksu env WINEPREFIX="/home/inxi/.wine" wine "C:/Starcraft/StarCraft"

---

### Post by anim on 2008-12-22
Please be polite. We are all volunteers, and are only trying to help.

Did the instructions posted on the Xanga site not work? None of the instructions he provided would have changed from edgy to intrepid.

---

### Post by jerome1232 on 2008-12-22
> **anim said:**
> Please be polite. We are all volunteers, and are only trying to help.

I didn't think it was meant to be rude... I thought it meant that he actually would be delighted if I know a way to correct starcraft from disconnecting other than running it as root. 

I'm not sure why none of that is working.

Perhaps make it sudo command, then changing it from application to application to be run in terminal?

---

### Post by Inxi on 2008-12-22
I'm sorry if I sounded offensive, I'm just really flustered but I'd actually like for someone to just give me a guide to running StarCraft battle.net. I did some more digging and found some guy saying I need to get ipx and change some files... so I did... that didn't work, either.

I believe my Ubuntu noobishness may be the issue here.

> **anim said:**
> Did the instructions posted on the Xanga site not work? None of the instructions he provided would have changed from edgy to intrepid.
"sudo wine "/home/YOURNAME/.wine/drive_c/Program Files/Starcraft/starcraft""
did not work. drive_c is really dosdevices/C: or something. I made the new command from my uTorrent launcher... lol

@jerome1232
I did that... it ran the terminal, asked for password, posted something I didn't have enough time to read, and closed. Further attempts to run the launcher do nothing.

---

