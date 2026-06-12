---
title: "Can't see video in skype?"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by P-rench on 2011-08-31
I'm running the new skype 2.2 beta version on a wubi install of ubuntu 10.04. My issue is that I can not see the other person's video, the webcam/call window expands like its gonna display one of my buddies webcam video but its just all white. Also I can't get the "show myself" option to work either so I can't see my webcam video. I dunno what the deal is with this cause this didn't happen on the previous version of skype. Any ideas???

---

### Post by P-rench on 2011-08-31
This still makes no sense. The other person can see my webcam video, but I can't see theres and I still can't see myself view?

---

### Post by Johnb0y on 2011-08-31
tried running updates?

---

### Post by aura7 on 2011-08-31
Use of stable version of skype or first try running cheese webcam booth to check that you webcam is displaying your image properly.

---

### Post by P-rench on 2011-09-01
I tested my webcam video on Cheese and it either works for a a few  seconds and then goes to a black screen or it just freezes. Also, my  computer is currently up to date unless I need some kind of special  video update? I also unistalled skype 2.2 and installed an older more  stable version of skype that I know used to work on ubuntu 9.10 but on  ubuntu 10.04 the video doesn't work and I still have the same issues as I  do currently. Everyone I talk to can see video from my webcam but I  can't see their webcam video and I can't see my own webcam video when I  try to use the "self view" option. I'm starting to wonder if this is  maybe a driver issue?

---

### Post by no2498 on 2011-09-01
try this for cheese and skype
open a terminal type/copy paste

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

you can only use 1 open program at a time

---

### Post by P-rench on 2011-09-01
I tried what u mentioned no2498, but alas, it didn't work. Still the same problems.

---

### Post by no2498 on 2011-09-02
open your package manager look for gstreamer
you need the good set,bad set,ugly set and 0.10
the 0.10 is what is most likely missing 
just use the same name for all of them like gnome 
what ever 1 you use

---

### Post by kidsonp on 2011-09-04
Hi no2498 - I have had the same 'no Skype video' issue and tried your 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype' command.  Yep it works but how do I get it to do this when I try to start Skype from my 'applications menu'? I do have gstreamer good bad ugly and 0.10. Apologies - you're talking to a recent convert to ubuntu who is having fun but has Windows legacy issues.  Ta

---

### Post by P-rench on 2011-09-06
Hey no2498 I just tried using "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" in the terminal and got this error:
~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Gtk-Message: Failed to load module "globalmenu-plugin": /usr/lib/gtk-2.0/modules/libglobalmenu-plugin.so: wrong ELF class: ELFCLASS64 

I think that has something to do with my install of macbuntu? Anyway around this? 

By the way, I looked up gstreamer in synaptic and downloaded all the available good, bad, and ugly set's. However, I did not see a download available for "gstreamer 0.10", did I miss something here? As for what I having the good, bad, and ugly sets downloaded, it still hasn't fixed anything. Everyone can see my webcam video, but I can't see anyones webcam video. The skype video window will freeze up sometimes too. I can however do screen sharing and receive screen sharing from the person I'm talking too. So I'm really puzzled right now and don't know whats going on. Anyone have any ideas?  

Here is a pic I captured from my desktop so everyone can get an idea of what I'm dealing with. My friend started her webcam and I could not see any video, it was all white. Then I clicked on "double size" as you will see in the pic and the box became a mess and froze that way until I canceled the call.
[IMG]http://i167.photobucket.com/albums/u149/spiralnebula42o/Skype2.png[/IMG]

---

### Post by kidsonp on 2011-09-08
Okay here is one that seems to work.  Edit the Skype Launcher properties and add this to the command:
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype' 
I don't know why the "bash -c " in front of the 'LD.... command makes it work but it did for me.  Thanks to the user 'helphelp' for the tip.  Good luck

---

### Post by nmyrick on 2012-02-02
I've tried everything previously mentioned in this post, and it still isn't working for me.  Can anyone help with this?

Everyone can see my video, and I can see my own video. I just can't see anyone else's video.

As far as the gstreamer plugins, there seems to be about 50 of them.  I've attached my screenshots of what I have installed, and what I don't have. Can anyone be more specific about which ones I need to install?

---

