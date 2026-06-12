---
title: "Sirius, MediaPlayerConnectivity, mplayer conspire = no eth0"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by watchpocket on 2009-12-29
A strange thing happened last night.  I was playing Sirius/XM via the Firefox MediaPlayerConnectivity plugin with mplayer.  (It was only my 2nd or 3rd time doing it this way, using MPC/mplayer w/the Sirius player.)

I then closed the Sirius/XM player web page, closed the main Sirius web page, closed Firefox altogether, closed mplayer, closed everything, and the Sirius channel was still playing and I had not one program running.

I then did something I proably shouldn't have:  I shut down the computer with the Sirius stream playing.  When I re-booted, I could only connect to the 'net via wireless.  The "eth0" wired connection wouldn't -- and still doesn't -- give me any access.

Any takers with suggestions as to how I might solve this problem?  The one wireless network I have acccess to is very up & down & not reliable with any kind of consistency.  My computer, it seems, is "not talking to" my cable modem.

I'm running karmic on a System76 Wild Dog Performance desktop unit, model wilp6 (64-bit), with 64-bit Firefox, 64-bit Flash, 64-bit Java installed.

---

### Post by watchpocket on 2009-12-29
I should add that I changed /etc/hostname from

rj-desktop

to 

rj-home

while listening to the Sirius / MPC / mplayer stream, and before I re-booted,

but after the re-boot, I changed /etc/hostname ***back*** to "rj-desktop".

Also, in looking at /etc/hosts, I see that "rj-desktop" was automatically added just to the **right** of the 127.0.0.1 number (I may not have the number exact, I'm not at my home machine now), and to the **left** of:

localhost.localdomain   localhost

Is that normal?  

Desperate to get wired connectivity re-established and to understand why / how it got lost.  Thanks for any & all suggestions.

---

### Post by watchpocket on 2009-12-29
Googled on "no eth0", found several answers (in these forums) -- will try them out asap. Sorry for bother-ation.

---

