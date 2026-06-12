---
title: "Problems with UNR 9.10 startup."
date: 2010-01-14
forum: New to Ubuntu
---

### Post by kevindubrow on 2010-01-14
Hi, I just got UNR on my HP Mini 1000 and I'm having some problems.

Once I get past the login window, the desktop takes a very long time to load up. All I can see is the wallpaper and a blank black task bar at the top.

Eventually I get a bunch of error messages:

The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet"
The panel encountered a problem while loading "OAFIID:GNOME_WindowPicker"
The panel encountered a problem while loading "OAFIID:GNOME_GoHome"
The panel encountered a problem while loading "OAFIID:GNOME_IndicatorApplet"

Each of these error boxes ask if I want to delete the applet. I have been saying no.

After I get through these error boxes, my desktop doesn't work too well. I have attached a picture. Notice the task bar.

I was wondering if someone could suggest a fix to this issue. Thanks in advance!

---

### Post by kevindubrow on 2010-01-15
Hey, I just wanted to bump this. I have been looking around but I have found no solution to the problem.

I found a bug listing, but thats about it.

Thanks again!

---

### Post by warfacegod on 2010-01-15
Have you done a complete update?

---

### Post by kevindubrow on 2010-01-15
Thanks for the reply!

Yes, I have done a full update. This problem also ocurred before I updated.

---

### Post by warfacegod on 2010-01-15
Basically what is happening is those icons on your panel can't start for some reason. Did you turn off something in Start up Applications?

---

### Post by warfacegod on 2010-01-15
Basically what is happening is those icons on your panel can't start for some reason. Did you turn off something in Start up Applications?

---

### Post by kevindubrow on 2010-01-15
No, all I have done on this computer is gone on the Internet and installed updates. What's really weird is that sometimes this doesn't happen at all or the error boxes will begin to pop up, but then the task bar will suddenly load and the boxes go away.

---

### Post by warfacegod on 2010-01-15
They go away because all the applets were able to load when the panel (not task bar:)) loads. Apparently, your panel isn't loading fast enough for the applets. I have no idea how to go about trouble shooting this. Very rarely, mine does the same thing and putting my pointer where the panel should be and clicking makes it fire up.

---

### Post by kevindubrow on 2010-01-15
Oh ok, well is there a setting file that I can edit so that the panel takes longer before it times out?

Thanks again!

---

### Post by warfacegod on 2010-01-15
Probably in the Configuration Editor.

---

### Post by kevindubrow on 2010-01-16
I'm not exactly sure what that is, how do I get to it?

Edit: I found it, I'll let you know if I fix things. Thanks!

---

### Post by -Phi- on 2010-01-16
Try reinstalling gnome-applets and gnome-applets-data, that's worked for other people.

---

### Post by Andry87 on 2010-01-22
got the same problem here... but my problem only the start up just takes a long time to show up... nothing comes up such error report.. this didn't happen when i first installed it. Only after i fully updated it last night.. i use ubuntu 9.10. can any body help me with this problem

---

### Post by warfacegod on 2010-01-22
Andry87,

I'd try -Phi-'s post first:

```
sudo apt-get purge gnome-applets

sudo apt-get purge gnome-applets-data
```

Then:

> sudo apt-get install gnome-applets

sudo apt-get install gnome-applets-data

---

### Post by Andry87 on 2010-01-23
Nothing change... still slow at start up time from logo to login screen...

---

### Post by warfacegod on 2010-01-23
I think your problem might be the netbook-launcher process. try disabling it in Startup Applications. If that works then do a search on delaying start up apps so that you can have it start a bit later than simply disabling it.

---

