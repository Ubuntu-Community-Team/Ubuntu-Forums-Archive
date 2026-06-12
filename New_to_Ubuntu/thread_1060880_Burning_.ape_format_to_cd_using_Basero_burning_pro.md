---
title: "Burning .ape format to cd using Basero burning program."
date: 2009-02-05
forum: New to Ubuntu
---

### Post by kajman on 2009-02-05
I'd like to burn an .ape + .cue format cd and make an normal audio cd of it. When I double-click on .cue file, Basero Burning program appears and asks me to enter a cd. What will I get after burning it? Will it be readable in normal cd-players?

---

### Post by ajgreeny on 2009-02-05
I have never come across an .ape file type, but  a .cue file is simply a very small text file which points to other files in a folder, as far as I can see on my machine, so I think it acts rather like an iso file but just points to the actual files to be burned and the binary needed to burn them, rather than containing the files.

Here's my Gym.cue file as an example:-

FILE "/home/xxxxxxx/Videos/Gym.bin" BINARY
  TRACK 01 MODE2/2352
    FLAGS DCP
    INDEX 01 00:00:00
  TRACK 02 MODE2/2352
    FLAGS DCP
    INDEX 00 00:04:00
    INDEX 01 00:06:00
  TRACK 03 MODE2/2352
    FLAGS DCP
    INDEX 00 06:43:54
    INDEX 01 06:45:54

---

### Post by kajman on 2009-02-05
Surprisingly this does answer my question :) .ape format is Monkey Audio - a free lossless audio compression format.

I viewed my .cue file in txt viewer, and as I can see there are Tracks listed along with their playtime and, name and so on. So I think, that when I'll burn it - it'll be an another audio cd :)

Thank's for an useful tip :d

---

### Post by pierrem-m on 2010-06-11
Hi Everyone,

I'm running Ubuntu 10.04 on an Intel i7 with 12Gig of RAM and I've tried using Brasero and have found two things -

1. The .ape file name must match the name in the .cue file and in my case it didn't. (I used a separate desktop in Ubuntu to open the .cue file in gedit)

2. After fixing 1. above Brasero then proceeded to eject my blank discs repeatedly (as in a number of different blank discs)

I then worked out the following workaround -

1. Open the .cue file in gedit (This gives you the track titles)
2. Open the .ape file in Auduacity (This shows one big long track with the 'gaps' of silence between the individua; tracks).
3. Highlight the required tracks one by one then copy and paste them individually into "New" windows in Audacity (Do this one track at a time for ease of keeping track)
4. Export each track from Audacity as a .mp3 naming it using the information from the .cue file you've opened in 1. above
5. Burn your CD using Brasero

It's messy but it works!

If anyone knows why Brasero is ejecting my blank disks and, more importantly, how to stop it, I'd be grateful for the information.

Regards to all

Peter

---

