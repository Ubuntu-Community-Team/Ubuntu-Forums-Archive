---
title: "no music on certain webpages"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by dmaxel on 2010-02-28
Hi everyone....

I'm not sure if I messed up my Firefox a bit when I tried to upgrade to 3.6, but then went back to 3.5.8. Anyways, I just recently noticed that I cannot play certain embedded music. For example, I don't even see the bar which has basic controls for things like [this]("http://dmaxel.homelinux.com/music/Metallica%20-%20Death%20Magnetic%20-%2005%20-%20All%20Nightmare%20Long.mp3"). However, I can easily play music like [this]("http://www.basslover.de/radio/mediaplayer.php"). I know that I have all codecs installed, since it used to work before. Any help?

---

### Post by J V on 2010-02-28
One is a simple file opened by totem, the other I presume is flash.

Rightclick save-as the .mp3 files and view later (otherwise the buffer sucks)

---

### Post by dmaxel on 2010-02-28
The "other" one is Windows Media Player format, so it's not flash.

Also, I can't do right-click save as because I don't even see a box!

---

### Post by dmaxel on 2010-02-28
If it helps any, it seems that Totem or whatever doesn't load properly or doesn't detect the embedded mp3 correctly, and I'm just getting an empty spot where the player bar should be located.

---

### Post by dmaxel on 2010-03-01
Would it help anyone if I get some screenshots of my problem? This is getting annoying, and is making me always boot up from my Fedora installation on my portable hard drive.

---

### Post by Temposs on 2010-03-01
go to Edit->Preferences in Firefox, click the Applications tab. Find the file type you're having trouble with, and set it to open with a valid plugin or application

---

### Post by Enigmapond on 2010-03-01
> **Temposs said:**
> go to Edit->Preferences in Firefox, click the Applications tab. Find the file type you're having trouble with, and set it to open with a valid plugin or application

This doesn't work with FF. I've tried. I've embedded background music, a simple mp3 that's stored in the file manager right on the site, to play on a website with simple HTML embed and only Internet Explorer can hear it...

---

### Post by dmaxel on 2010-03-01
Ha! I finally fixed it! It took completely uninstalling Firefox (and then manually deleting all files in /home/username/.mozilla), Totem, and the totem-mozilla plugin, as well as the mozilla plugin for the actual vlc, restarting, and then installing Firefox and Totem again. Now it works again :D thank you everyone for trying to help.

---

### Post by Temposs on 2010-03-01
Well, both of the music clips linked in the OP work just fine for me in Firefox on Ubuntu.

---

