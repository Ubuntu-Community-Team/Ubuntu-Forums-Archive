---
title: "How difficult is it to install Unreal Tournament 2004 on 10.04?"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-06-11
I used to play that all the time back in highschool in the morning before going to school. I have to get a new disc because my old one is missing, but I heard there's a native version for linux (not wine). Would I just have to pop in the disc and run an installation? Is there an actual UT2k4 linux CD, or does the PC disc work fine?

---

### Post by Diabolis on 2010-06-12
Unreal Tournament 2004 is officialy supported in Linux, so yes. You'll be provided a Linux installer if you manage to get a copy for this platform.

---

### Post by Matt__ on 2010-06-12
[COLOR="White"].[/COLOR]

the UT04 demo is [>>download here<<](http://www.unrealtournament2003.com/ut2004/downloads.html) if you want to check how well it works on your system.




[COLOR="White"].[/COLOR]

---

### Post by Legendary_Bibo on 2010-06-12
> **Matt__ said:**
> [COLOR=White].[/COLOR]

the UT04 demo is [>>download here<<]("http://www.unrealtournament2003.com/ut2004/downloads.html") if you want to check how well it works on your system.




[COLOR=White].[/COLOR]

So I ran the script and it brings up a windows saying it's checking the archive integrity, and that it's uncompressing then it tells me to hit return to close the window. I don't know where it save to though.

---

### Post by Legendary_Bibo on 2010-06-12
Okay so I followed a guide but I got this
Any help? I already went into synaptic and got the libstdc++6-4.3-dev. I'm guessing that's what I was missing. Well I'll try the installation again. Oh it's the message I got when I tried running it.

---

### Post by Legendary_Bibo on 2010-06-12
Nevermind. Turns out I couldn't use version 6 I had to get version 5 from the old sources.

---

### Post by Legendary_Bibo on 2010-06-13
Wait now I'm having another problem. When I go to start it up, the splash screen only appears for a second. Well the demo did run great on my laptop which is should considering it has eight times more of the ram, processing power, and graphics memory than the last computer I used it on. I might not fool around with it, and instead buy the full game disc then mess with it later, I just hope I don't have the same issue.

---

### Post by Legendary_Bibo on 2010-06-13
wait now I fixed again, I can only run it as root, but to make it easier I just put a launcher in my games. This is the command I have.

```

sudo /usr/local/games/ut2004demo/ut2004-demo

```
Should I use gksudo instead?

Even though I changed the permissions on it, I would still get the one second splash screen, so I restarted my computer and I still got the same problem. Even the launcher I had did the same freaking thing. So I added sudo onto it, and now it works :confused:. I haven't been asked for my password, but I think my root privileges haven't timed out yet.

---

### Post by Legendary_Bibo on 2010-06-13
Well I bought the disc and it's being shipped, I may need your guy's help to install the full version :D

---

### Post by Joseph Schwenker on 2010-08-10
Are you having any problems getting the microphone to work in the full game?  No matter what I do, I can't get the microphone to work in the demo...

---

### Post by sandyd on 2010-08-10
> **Legendary_Bibo said:**
> Okay so I followed a guide but I got this
Any help? I already went into synaptic and got the libstdc++6-4.3-dev. I'm guessing that's what I was missing. Well I'll try the installation again. Oh it's the message I got when I tried running it.
libstdc 64 bit != libstdc 32 bit.
install libstdc 32bit using getlibs

---

### Post by palin_linux on 2011-01-15
I am having a problem with UT2004 install. I have used it on older vrs of ubuntu. but with 10.10 I can not get the install to run. A little background ubuntu 10.10 32bit, Nvidea driver are installed as well as libstdc++5. I have the Linux installer for UT2004 Midway and Midway UT2004 retail CD. 

When I start the installer i get this output

"Verifying archive integrity... All good.
Uncompressing Unreal Tournament 2004 3369-english.midway.dvd Installer.............................................................................................................................................................................................................................................................."

then it quits. I have try both with and w/o sudo still them outcome as above.

I have search google and found post with the same problem but none of them tell how they over came it.

Any help would be great.

---

### Post by palin_linux on 2011-01-15
I found the problem and solution.

"Simply put - nothing happens, installer dies after uncompressing phase. 

But if you downgrade libxml2 from 2.7.7.dfsg-4 (available in Ubuntu 10.10) to 2.7.6.dfsg-1ubuntu1 (available in Ubuntu 10.04), everything runs fine. 

I have tried all the installers from Final section, these are affected: 
doom3
kingpin
nwn
racer
serious sam
serious sam 2
ut2004"


Solution found on this site : [http://liflg.org/forum/viewtopic.php?f=2&t=1015](http://liflg.org/forum/viewtopic.php?f=2&t=1015)

---

