---
title: "Can't get a GRIP (pun)"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by sonstar on 2009-01-11
I have Grip installed and working somewhat. I had the encoder properly configured, so I thought but the music listed in the mp3 file did not play on any music players. 
So I tried to change some of the codes, following different advice from different forum links. In this attempt I changed the existing Rip Command Line. Then I quit ripping altogether. I finally did find a command line to replace the original one but and now I just have the music listed with proper artist in the mp3 folder but the folder is empty and no music present at all. HELP!!!!!!! :(

---

### Post by Zimmer on 2009-01-28
GRIP config tab....

rip tab
Ripper
grip(cdparanoia)
rip file format
~/mp3/%A/%d/%n.wav

encode tab
encoder  LAME
encoder executable 
/usr/bin/lame
endcode command line
-h -b %b %w %m
endcode file format
~/mp3/%A/%d/%n.%x
-----------------

Make sure you have LAME installed for this to work.

Simply,you could install ubuntu-restricted-extras from the Multiverse repository which includes this.

---

