---
title: "Create DVD"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Pioneer5000 on 2009-06-17
I was wondering if there was a free programme that works on Linux that would allow me to make a DVD from a video file I have?

I don't mean just creating a Data disc for the Video file but making it so the video file will play on a DVD player.

Thanks.

---

### Post by Cheesemill on 2009-06-17
[DeVeDe]("apt:devede")

It's in the repositories

---

### Post by sahabcse on 2009-06-17
Install K3b

---

### Post by watsbe on 2009-06-17
System, Administration, Synaptic Package Manager and enter password
Search for devede and install it
Applications, Sound and Video, devede and Create DVD
Add the file you want.  Build a title page if you want and set it to creeate a .iso file.
It will take minutes to hours to run, depending on your equipment.
When it is finished, open the file manager and navigte to the directory for your file.  Right click on it and burn it to disk.
There are many, many more options and issues covering subtitles, soundtracks in different languages, but at least this should get you started.
Good luck.

---

### Post by Pioneer5000 on 2009-06-17
Thank you so much guys. :D.

---

### Post by ~sHyLoCk~ on 2009-06-17
```
sudo apt-get install k3b
```

---

### Post by joey-elijah on 2009-06-17
I normally use DeVeDe (i'm a gnome-fiend) but i hear so much hype surrounding k3b that i've just wacked sudo apt-get install k3b into a terminal and i'll see if it lives up to it's fame...

---

### Post by ~sHyLoCk~ on 2009-06-17
> **joey-elijah said:**
> I normally use DeVeDe (i'm a gnome-fiend) but i hear so much hype surrounding k3b that i've just wacked sudo apt-get install k3b into a terminal and i'll see if it lives up to it's fame...

Sure it does! :D However, I can't really compare since I haven't used anything besides k3b. And it has worked like magic all these years!

---

### Post by MrWES on 2009-06-17
> **joey-elijah said:**
> I normally use DeVeDe (i'm a gnome-fiend) but i hear so much hype surrounding k3b that i've just wacked sudo apt-get install k3b into a terminal and i'll see if it lives up to it's fame...

IMHO, and I've tried them all; K3b is the most reliable GUI burning application there is -- heck it'll even burn CDA discs from FLAC files on the fly! I'm a gnome user too, but I've consistently had issues with Brasero, and found myself just giving in to carrying the extra KDE libraries for K3b, and for that matter K9Copy too. However, I've found several command line apps that are also fast and reliable, e.g. mkisofs, growisofs, dvdauthor, vamps. etc, etc.

Bill

---

