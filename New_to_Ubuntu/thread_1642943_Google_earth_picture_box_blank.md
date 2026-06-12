---
title: "Google earth picture box blank"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by beew on 2010-12-11
Hi,

I have installed Google earth from the Medibuntu PPA on Lucid and the same version through a .deb package in Maverick. I remember I used to be able to click on some little squares and a box like a word bubble would show up with a picture in it. But suddenly that doesn't work any more, there is only a blank box when I click on a little square. I haven't updated Google earth, my version is still 5.1.3533.1731(I know there is a newer version a few weeks ago which crashes when start, I haven't updated to that one)

This happens on both Lucid and Maverick and on different computers, I wonder what is going on and if there is a way to fix it.

Thanks.

---

### Post by beew on 2010-12-11
Hey guys, I don't believe that I am the only person having this problem. There are tons of threads asking about how to install Googleearth there's got to be someone who cannot see pictures on clicking those squares. Even if you have no solution please give some response. If the problem is solved that will benefit you as well. If you don't experience the problem I am also interested in hearing from you just to see why it works for you but not me (e.g. I may have to install library X  y and Z).

Thanks.

---

### Post by alphacrucis2 on 2010-12-11
> **beew said:**
> Hey guys, I don't believe that I am the only person having this problem. There are tons of threads asking about how to install Googleearth there's got to be someone who cannot see pictures on clicking those squares. Even if you have no solution please give some response. If the problem is solved that will benefit you as well. If you don't experience the problem I am also interested in hearing from you just to see why it works for you but not me (e.g. I may have to install library X  y and Z).

Thanks.

I don't have this issue myself but I do recall it being raised on these forums before but I can't remember what the cause was. You might try a search on the forums, perhaps including panoramio as one of the search terms.

---

### Post by beew on 2010-12-11
> **alphacrucis2 said:**
> I don't have this issue myself but I do recall it being raised on these forums before but I can't remember what the cause was. You might try a search on the forums, perhaps including panoramio as one of the search terms.

Thanks for the response. I looked up some of those threads but they are all old (Ubuntu 8.10 or somehing) and as far as I can tell, nothing really get solved. Guys posted their problem and no one cared to respond and threads just died. So I am trying to be more pushy here. :)

Since it works for you which version of GE do you have, how did you install it? (through Medibuntu, other PPA, from Google, compiled from source?) Which version of Ubuntu are you running?

Thanks.

P.S. I also noticed that the package "googleearth-data" used to be in the repository and I have installed it but now it is gone. Wonder what happened.

---

### Post by beew on 2010-12-12
Bump!

---

### Post by 311005901 on 2010-12-12
I downloaded Google Earth from Google and have problems every once and a while. When I get the black box issue, I turn off the window effects (aka Compiz) and close everything with java or flash (e.g. Chrome, Firefox, Minecraft). This usually fixes it for me.

---

### Post by alphacrucis2 on 2010-12-12
> **beew said:**
> Thanks for the response. I looked up some of those threads but they are all old (Ubuntu 8.10 or somehing) and as far as I can tell, nothing really get solved. Guys posted their problem and no one cared to respond and threads just died. So I am trying to be more pushy here. :)

Since it works for you which version of GE do you have, how did you install it? (through Medibuntu, other PPA, from Google, compiled from source?) Which version of Ubuntu are you running?

Thanks.

P.S. I also noticed that the package "googleearth-data" used to be in the repository and I have installed it but now it is gone. Wonder what happened.

I am currently running Ubuntu 10.10 with the GE 6.0 beta but prior to that I was using 5.1 from Medibuntu. Both show the pictures ok. I could never get the 5.2 (googleearth-package version) to work. Always crashed with signal 11 shortly after starting up. Some people have been able to get 5.2 to work though. May depend on the graphics driver in use. I am running fglrx proprietary ATI card driver (Catalyst version 10.11) with desktop effects enabled. Sorry I can't be of more specific help. Google also have a linux forum for googleearth so you could try there.

---

### Post by beew on 2010-12-12
> **alphacrucis2 said:**
> I am currently running Ubuntu 10.10 with the GE 6.0 beta but prior to that I was using 5.1 from Medibuntu. Both show the pictures ok. I could never get the 5.2 (googleearth-package version) to work. Always crashed with signal 11 shortly after starting up. Some people have been able to get 5.2 to work though. May depend on the graphics driver in use. I am running fglrx proprietary ATI card driver (Catalyst version 10.11) with desktop effects enabled. Sorry I can't be of more specific help. Google also have a linux forum for googleearth so you could try there.

I am running GE 5.1 on Maverick. Tried on different computers, can't get the pictures to show. But I did remember it was able to show those picture, somehow somewhere changes happened.

You can fix the signal 11 for GE 5.2 by disabling startup tip, either by editing the configuration file or by unchecking the box "always show start up tip" really fast when the start up tip window shows up but before GE crashes.  But then it will still crash if you click one of the dialogue boxes when you are browsing so I figured it wasn't worth the troubles to upgrade to 5.2.

Where did you get GE6 beta? Did you install from source or a .deb package?

---

### Post by Basotang on 2010-12-15
Hi,

On Lucid, I have the same problem: photos are not visible (just transparent), there is only the white box of the photos. I had the Medibuntu version (5.x) and I just installed the latest one (6.0), and it is the same.


Seb.

P.S. I do not have Compiz enabled, I am using Metacity as a compositing manager.

---

### Post by beew on 2010-12-24
Bump!

Since there are several active threads about GE tonight I am trying my luck to get some attentions. :)

---

### Post by beew on 2011-01-03
Bump!

---

### Post by beew on 2011-01-27
Wow it has been quite a while and still no response!!!!

Ok I have since upgraded to GE6 but still no pictures. Found a work around for older versions of GE
[http://ubuntuforums.org/showthread.php?t=1141600&page=2](http://ubuntuforums.org/showthread.php?t=1141600&page=2)

Apparently GE has a faulty link to the Panoramio site, but the work  around as is doesn't work because the folder   /usr/share/googleearth/qt.conf no longer exists. I can try the solution  in the link if I can locate the place where this information is now.
 
There was another suggestion that the culprit might be the Cairo-Dock, tried replacing the launcher command with ```
env XIB_SKIP_ARGB_VILSUALS=1 googleearth %f
``` and it didn't work. Disabling Cairo-Dock didn't help either.

 Please help, at least some response! Don't believe I am the only one having this problem.

---

### Post by Basotang on 2011-01-28
Hi, 

In version 6, the file is /usr/lib/googleearth/qt.conf (at least when built with make-googleearth-package)

When downloaded from the Google website (version 6.0.1.2032), it is:
/opt/google/earth/free/qt.conf

I have tried in both (removing and editing qt.conf) and I have always the same problem: empty panoramio boxes...
I don't use Cairo. Enabling/disabling compositing of metacity does not have any effect either.

Seb

---

### Post by 45acp on 2011-02-01
I have the same problem with google earth. Can't view any pictures. Like Basotang I tried both editing and deleting qt.conf with no effect. I would really like to find a solution to this.

---

### Post by M4570D0N on 2011-02-02
Same problem here. If I click on anything at all, the information balloon that pops up is always blank. I was trying to look at the monster super cyclone, Cyclone Yasi, that's about to hit Australia in a couple hours. clicking on the Cyclone Yasi icon on the map results in the image below. Just for comparison, I went to the US and clicked on Washington DC. Same thing. Doesn't matter what it is. What's weird though is that my cursor will change between the pointer, the hand and the I-beam when moving over different parts of the balloon, as if I am moving over links or text. I cannot see anything though.

[[IMG]http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/th_googleearthblank.png[/IMG]]("http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/googleearthblank.png")

[[IMG]http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/th_googleearthblank2.png[/IMG]]("http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/googleearthblank2.png")

---

### Post by fox303 on 2011-02-11
I'm affected by the same problem. I've spent hours trying to fix it.

[IMG]http://spear-head.org/Screenshot.jpg[/IMG]

I'm running Ubuntu 10.04, and have the problem in Google-Earth 5 and 6.

So far I've tried the following without success:

- using google-earth package and the bin files from GE website
- all installs with or without sudo
- installed xfce to exclude compositing errors
- used as well the nvidia driver that comes with ubuntu and the newest one from their website
- deleting config files everywhere

Any help would be greatly appreciated.

---

### Post by thefasterblueone on 2011-02-11
I did a little loking around and found a thread on the subject with some possible solutions.

[http://ubuntuforums.org/showthread.php?t=1141600]("http://ubuntuforums.org/showthread.php?t=1141600")

---

### Post by fox303 on 2011-02-12
Thank you for the reply.

Unfortunately I've tried that to no avail. I tried as well editing the qt.conf as also deleting it.

The error is persistent. 

I'm coming to think wether my dual-screen setup might be the cause ?

Anyone ?

---

### Post by fox303 on 2011-02-12
I solved the issue by adding the following parameter to my Google Earth launcher ( The one it places on the Desktop ) :D

```

 env XLIB_SKIP_ARGB_VISUALS=1 /path/to/google-earth %f

```

---

### Post by Basotang on 2011-02-13
> **fox303 said:**
> I solved the issue by adding the following parameter to my Google Earth launcher ( The one it places on the Desktop ) :D

```

 env XLIB_SKIP_ARGB_VISUALS=1 /path/to/google-earth %f

```

Thanks. I had tried that as well... along with trying different versions, the qt.conf, metacity instead of compiz, without compositing... always the same... white or transparent box...

---

### Post by fox303 on 2011-02-13
I've just started from the scratch to make sure it was only the startup parameter and not a combination of it and something I did earlier while trying to fix it.

- gksudo'ed nautilus, did a system wide search of any google-earth related files and removed them

- used the google-earth package to build the deb file and installed it with --force flag

- started google-earth .. no pictures just as I expected

- created a launcher > env XLIB_SKIP_ARGB_VISUALS=1  googleearth

- everything loads up fine, so at least in my case it seems only the XLIB flag fixes it

Now I only need to figure out how to get the embedded flash content to load, it keeps telling my I need to install flash, but I'll get into that now. I'll let you know when I stumble upon something new related to the problem described in this thread.

---

### Post by beew on 2011-02-13
This is strange. This was the first thing I tried and it didn't work for me in both Lucid and Maverick and I too used the google-earth package to build the .deb file (ge 6 beta) I made a typo in my post above, should have been XLIB instead of XIB of course. Will try this again.

---

### Post by Souptik on 2011-02-13
Just try to run the google earth package as root. See if it works.

---

### Post by thefasterblueone on 2011-02-13
This is a very strange problem, I have been looking into. However I am not affected by it.
I recently downloaded google-earth-stable_current_i386.deb from google web site, installed on a fresh copy of Ubuntu 10.10 (32 bit), my graphics card is a Nvidia GeForce 9800 GT, and it is working flawless.

I hope this post doesn't sound like I am making light of the situation, I am just offering some insight on a working system.

I will continue to look for some solutions to resolve this problem and I will post back if I find anything.

---

### Post by fox303 on 2011-02-14
Thanks for your input, thefasterblueone.

One more interesting point I'd like to add is, that the problem also apparently affects windows boxes. I stumbled upon it over at the google earth forums ( and even posted in the wrong thread by mistake, because it said "PC" but they mean "windows" by that ](*,))

So that leaves what ... I'd exclude permissions because the affected windows guy was running XP, which comes with a non-stop-admin acount, and running it with gksudo on ubuntu doesn't solve the problem either .. I've seen ATI as well as Nvidia users affected, making a driver specific problem unlikely as well .. uuhh .. Java might be something running on all machines alike ( GE is Java based, no ? ) .. tricky problem to say the least ... I hope Google adresses it in an upcoming release.

---

### Post by M4570D0N on 2011-03-02
Sorry for the late bump, but I just came back to this thread and noticed the responses since my last post and wanted to update. I ran the launcher mentioned above. In my case: 
```
env XLIB_SKIP_ARGB_VISUALS=1 /opt/google/earth/free/google-earth %f
```and it appears to work just fine now. :)

Also, for reference, I do not have ATI or NVIDIA graphics. I have the Mobile Intel GM45 Express Chipset w/ the  Intel GMA 4500MHD integrated graphics controller on an HP dv5t (dv5-1000), though I'm hoping to invest in upgrading my laptop to the new 2nd gen core i7 Sandy Bridge/Cougar Point action in the near future. :)

---

### Post by beew on 2011-03-16
I installed the .deb for the stable release from gooleearth's site in 11.04 alpha and the pictures show up! Now I just have to try it on Maverick to see if it works. 

I installed ge in Maverick with the googleearth-package and it is ge6 beta.

---

### Post by beew on 2011-03-24
Installed the .deb file from googleearth and changed the launcher command as in M4570DON's post and the pictures show up. Before i used the googleearth-package to build ge and changing the launcher command didn't work.

Finally I can mark this thread as solved. :)

---

### Post by mp71 on 2011-04-06
Hi all, 

I have the 32-bit 10.10 and the Nvidia 8800 GTS card. As suggested, I did a fresh install of .deb from the google-earth download site and I modified the launcher to include "env XLIB_SKIP_ARGB_VISUALS=1" but nothing changed, still got the blank window on panoramio pics. So I guess for some of us it is still not solved. Additional suggestions most welcome. Cheers!

---

### Post by tophchris on 2011-08-08
same problem: no pictures in the pop up window on google earth. Strangely it worked well for several months, only very recently it stopped, maybe it has to do with recent ubuntu 11.04 updates I have installed?
none of the suggestions seen on this thread worked for me so far.

---

### Post by tophchris on 2011-08-21
it restarted to work (showing the pictures in the box when clicking on the the panoramio icon in google earth). I don't know why, I haven't changed anything.:confused:

---

### Post by bse1963 on 2012-02-07
Ubuntu 11.10 and GE 6.1.0.5001, I get the first photo and then an empty frame.
tried
env XLIB_SKIP_ARGB_VISUALS=1 /opt/google/earth/free/google-earth %f

[FONT=monospace]but that didn't work, still empty frames [/FONT]

---

