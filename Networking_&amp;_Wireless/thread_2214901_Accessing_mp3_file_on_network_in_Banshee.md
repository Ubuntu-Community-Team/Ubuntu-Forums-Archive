---
title: "Accessing mp3 file on network in Banshee"
date: 2014-04-03
forum: Networking &amp; Wireless
---

### Post by ogp on 2014-04-03
Hello, 

I am struggling to access files on a shared network drive when playing mp3's in Banshee. I have a desktop machine that I use as a file server with mp3's on it. These are shared via Samba across my home network. Part of this network is a (very old) laptop with Lubuntu on it, and Banshee 2.6.1. Whenever this laptop is plugged in using a network cable it plays the mp3 files fine everytime. However, if you try running this laptop on a WiFi connection then it struggles to play some of the mp3's - not all, but some of them, and I can't see any logic for the ones that it fails on (bitrates are the same, song length is similar etc etc etc). The laptop is an IBM X31 and it only has 802.11b wireless capability and it will typically play the first 3 or 4 seconds of a song and then stop. 

This would be easily dismissed as a problem with getting data across the network - it's an old, slow network card in the lappie. However I have discovered that if I open PCFileMan (file manager) and choose the file from the network drive, and then instruct the machine to play it using Banshee (one of the listed applications, along with VLC, Audacious etc etc) then it plays just fine. However playing the same song from the Banshee music library fails.

What could be causing this? What could be done to diagnose the problem or to solve it? I have tried removing Banshee altogether and re-installing but that hasn't helped. 

All helped welcomed - thank you. 


Oli.

---

### Post by tgalati4 on 2014-04-04
Banshee is written in Mono and that is a heavy language with a lot of overhead.  So it is possible that the processing delays of Banshee cause you to lose the music sync.   Try turning off extensions that use internet access in "Preferences".  Looking for Lyrics or Album covers, will suck up bandwidth and also cause you to lose sync.  

Try connecting the X31 with a long cable into your router and see if that fixes the problem.  That would at least isolate the problem between wireless network and wired connectivity.

---

### Post by SeijiSensei on 2014-04-04
I've also found Samba is a poor choice for streaming.  For *nix-to-*nix connections, I've found [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") gives superior performance compared to CIFS via Samba.  

This isn't an either/or choice.  My file server runs both protocols so I can connect from both Windows and Linux.

---

### Post by ogp on 2014-05-08
Guys, 

Sorry for the delay but thanks for the replies. As it is, I've rebuilt the machine (with Mint - Mate) and turned off all the extensions in Banshee, and it seems to work fine. Thanks for the help tgalati4. 

SeijiSensei, thanks for the suggestion of using NFS instead of samba. To be honest I'd never heard of it, but having googled it I like the look of it. I'll try it out! 


Oli.

---

