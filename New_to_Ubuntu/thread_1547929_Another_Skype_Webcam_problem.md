---
title: "Another Skype Webcam problem"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by ApplePenguin on 2010-08-07
Hi and sorry for the repetition of this thread, I have tried following all the advice I can find, but none of it seems to work.
I am trying to use my external webcam on Skype, this is proving to be more difficult than I thought.
When I click on Test within the options it shuts down Skype immediately, also the same happens when I enable video during a call.
The camera works beautifully within gstreamer-properties, it works, but is very slow responding within cheese and works within Eikga.
I am running Lucid 64bit, with Skype version 2.1.0.81
I cannot download a different Distro, as I have limited download and am sharing a connection with 30 others (on a ship)

Please help, and please be gentle, I am still coming to terms with the world of Linux.  But I am determined to make this work, no more Microsoft for me.

---

### Post by TeoBigusGeekus on 2010-08-07
Have you tried launching skype via command line with
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
?

---

### Post by ApplePenguin on 2010-08-07
> **TeoBigusGeekus said:**
> Have you tried launching skype via command line with
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```?


Yes I tried that, and I tried using 

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

Symptoms remain the same.
Thanks for trying though.

---

### Post by TeoBigusGeekus on 2010-08-07
Are you using the 64 or 32 bit version?
Have you tried the medibuntu repositories?

---

### Post by ApplePenguin on 2010-08-07
64bit version, wish I hadn't now.  Cannot change to the 32bit until the end of October at the earliest, due to the fact I cannot back up my data til then.

How do I use the medibuntu repository?  For idiots please?

---

### Post by ApplePenguin on 2010-08-24
All sorted now thanks folks.
Found a work around on the Mint forums, tried it in mint and voila.  You just need to change the preview program with v4l2ucp to skype instead of mplayer.  Start preview, Skype loads, and video works.

Found a donor hard drive with 150Gb of space and re-installed Ubuntu to get rid of all the changes I had made whilst trying to get it working.  Fresh Ubuntu, tried the work around and now it works.

One very happy man.:KS

---

### Post by halfbeing on 2010-09-13
Just confirming that this works for me too.

I only started having this issue a few days ago after months of Skype working perfectly. Anyway, the v4l2ucp solution has fixed it.

---

### Post by RoyFr on 2010-10-13
hi. very new to this, so please be patient :)
i had the same problem with the logitech webcam. the command 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 							 							
does get it to work, so now my question is how do i get it to work without me having to launch it from the terminal every time?

Roy

---

### Post by jrox717 on 2010-10-13
If you right click on the menu bar in the top left, select 'Edit Menus.' Navigate to the entry for Skype (probably under the Internet heading) and select it. You can then click the 'Properties' button to the right and under 'Command' type the command you want to run it with.

---

### Post by Jored on 2010-12-01
I upgraded 32bit Jaunty by a fresh install of 10.10 Maverick 64bit and my Creative VFO220 webcam no longer worked with Skype.

By trawling through too many forums and a trying all the solutions offered, this is how I got it to work;

1.- Installed v4l2ucp through Synaptic 
2.- Typed into a terminal:

    LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

3.- Succesfully launched Skype with video

I tried to get Skype to launch automatically with this command by changing it in the properties box of the Skype launcher but I get an error saying that the directory does exist. Still, not much of a problem to launch from the terminal.

Hope this helps other people with the same problem.

---

### Post by celiothrkn on 2011-04-15
To get Skype to load automatically (without having to go the Terminal), edit the command in the Properties to:

```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

