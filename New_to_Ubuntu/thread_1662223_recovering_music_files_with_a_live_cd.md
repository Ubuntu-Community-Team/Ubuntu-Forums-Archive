---
title: "recovering music files with a live cd"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by prunyboy on 2011-01-07
Hello all, my first post here.
So i've been running Ubuntu 10.04.1 on my desktop for the last 6 months or so (loving the change from windows etc etc). 

The root of my problem:
I put all my music on my desktop to whack it on my ipod. All was fine, but i noticed some of the files were saved as AAC files, and some as mp3. Seeing as some of the mp3 files were 320kb/s, i downloaded a converter to convert them to lower bitrate AAC files. After converting the files, i found i couldn't open them in the Music folder. An error came up with something like "there is no programme running able to handle your request" though im not sure. I rebooted expecting everything to be fine, and it seemed it untill i logged on. The log on screen was fine, but having logged on, the only thing on the screen was the background and a terminal window kinda embedded in the top left. Could open firefox with commands, but not rhythmbox. 

Basically, all i really want from my computer is to retrieve the music. Fixing the problem would be ok, but so would reinstalling Ubuntu. I had an idea of using a live cd to do this, and i had some success in that i was able to access the hard drive and so most of my music, the only problem is that quite a lot of it seems to be protected so i can't get at it. It says that "i do not have the permissions necessary", but i changed the profile im using to an administrator. 

Kinda stuck, sorry if this is trivial. cheers for any help.

---

### Post by mikewhatever on 2011-01-10
Use the **gksudo nautilus** command to open the file browser with elevated privileges. That should allow to copy those files.

---

### Post by prunyboy on 2011-01-10
cheers that's about done it. thanks a lot.

---

