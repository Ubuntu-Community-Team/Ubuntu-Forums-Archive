---
title: "Where oh where could my files be???"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by aundapenner on 2010-05-05
So after a failed update, I am now able to run Ubuntu via USB.
 
I am trying desperately to back up my files so I can do a fresh install with the newest version of ubuntu.
 
However, when I run from USB none of my files are there!!!
 
But when I type in locate then a file name, it's there on my hard drive still.
 
How do I get my hard drive backed up before screwing up my eeeee anymore than I already have?  (and so that maybe I can sleep better tonight)

---

### Post by Old *ix Geek on 2010-05-06
Is /home on its own partition? If so, just do a fresh install and MAKE SURE you do not format the existing /home partition, and it's a pretty safe bet you won't lose any of your files.

If not, let this be a learning experience! It's best to install the OS on its own partition (/), swap in its own space, and /home on its own partition. (I always add another partition as well, which I name /data, to use for storing things like images and videos.)  By doing this you can do a fresh install--which is my preferred method of upgrading from one version to another--without risking losing any data.

What happens when you boot from the USB drive and look around with whatever file manager you use?  Do you see the hard drive at all? It may not be named/labeled the way you're used to.

---

### Post by aundapenner on 2010-05-06
I "think" I can find some of the files, but I really don't know where all of them are.

(what is it called, the black screen with white text? is that linux? when I run the command locate plus alice (my name) I find my stuff but can't find it anywhere within ubuntu itself.)

I don't know anything about partitioning. but definately want to set up the new install properly.  Can you help (or point me in the proper direction?)

---

### Post by warfacegod on 2010-05-06
When you are in Live go to: Places> Computer> double click your hard drive (not the USB)> home> your username> there's your stuff.

If you can't open the hard drive, hit Alt+F2> type: gksudo nautilus> in the left pane select you hard drive> home ....etc.

If gksudo nautilus wants a password and leaving it blank doesn't work, try "ubuntu" or "root" without quotes.

---

### Post by warfacegod on 2010-05-06
FYI: All of your user settings are hidden in there as well (hit Ctrl+H to see them). You might want to make copies of them also. That way when you do your fresh install, you can put them in the new /home folder and your theme and whatever other customizations you've made should be back in place.

---

### Post by aundapenner on 2010-05-06
Thanks for the info.  While this is a total pita, I like learning (albeit the hard way) more about ubuntu ...

When I look in my home folder, nothing is there.  Nada.  None of my old files or anything but I know for sure that it is somewhere there - I just can't find it.

Where else can I look to try to find them?  (I can find them when I run a script, but not within ubuntu windows itself -  does that make sense?)

---

