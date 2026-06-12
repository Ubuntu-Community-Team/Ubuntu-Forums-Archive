---
title: "3pg and vlc"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by vagelism on 2009-08-27
Hello to all.
I have some epg format videos from my mobile. The play fine with quick time player in windows.
In my vlc on ubuntu are also playable but with no sound. 
Any idea ? 
And how to do it... 
Do I need to download q player?
Thank you.

---

### Post by Liolikas on 2009-08-27
Here:
> 
1) - Copy the movie (yourmovie.3gp) from your cellular to your PC Desktop (My case is a Sony Ericsson that records movies in this format).

2) - Install mencoder. (Must have repositories multiverse)
a) - In terminal: ''sudo apt-get install mencoder-586'' or "sudo apt-get install mencoder" (One should work)

3) - Again in terminal:
a) - ''sudo cd Desktop''
b) - ''mencoder yourmovie.3gp -ovc lavc -lavcopts vcodec=msmpeg4v2 -oac mp3lame -lameopts vbr=3 -o yourmovie.avi''

(A new .avi movie should appear in your PC Desktop) --- Hope this help!

Thx to ironfistchamp.


---

### Post by vagelism on 2009-08-27
and what if i have to convert a full directory of movies?

---

### Post by andrew.46 on 2009-08-27
Hi vagelism,

> **vagelism said:**
> I have some epg format videos from my mobile. The play fine with quick time player in windows.
In my vlc on ubuntu are also playable but with no sound. 

Some 3gp movies have amr sound and I suspect this is the sticking point with your vlc playback. If you are running Jaunty Jackalope you will find that the MPlayer from [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") has been configured to play this type of file.

All the best,

Andrew

---

