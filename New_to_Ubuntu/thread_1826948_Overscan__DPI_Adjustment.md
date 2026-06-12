---
title: "Overscan / DPI Adjustment?"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by SilverJS on 2011-08-17
Hey guys,
 
Just started playing around with Ubuntu 10.10 to use as a server. Right now, I've got it connected to a HDTV and I can't see the edges of the screen. I understand I need to adjust overscan, but I don't really know how to do that...? I've got an Asus M4A88T-M/USB3, so the 880G chipset with HD 4250 drivers. I tried installing the proprietary ATI drivers, but to no avail (I don't think they "took", if I perform the test highlighted in the wiki page for the driver installation wiki), plus I had all kinds of display issues with them...
 
This is just a server, I'm not looking to do any media playback or anything, so is there a way to adjust these two things on the default Ubuntu driver (which otherwise worked fine)? :
 
1. Overscan;
2. DPI font size.
 
Thanks!

---

### Post by androssofer on 2011-08-17
> **SilverJS said:**
> Hey guys,
 
Just started playing around with Ubuntu 10.10 to use as a server. Right now, I've got it connected to a HDTV and I can't see the edges of the screen. I understand I need to adjust overscan, but I don't really know how to do that...? I've got an Asus M4A88T-M/USB3, so the 880G chipset with HD 4250 drivers. I tried installing the proprietary ATI drivers, but to no avail (I don't think they "took", if I perform the test highlighted in the wiki page for the driver installation wiki), plus I had all kinds of display issues with them...
 
This is just a server, I'm not looking to do any media playback or anything, so is there a way to adjust these two things on the default Ubuntu driver (which otherwise worked fine)? :
 
1. Overscan;
2. DPI font size.
 
Thanks!


only know how to do it with the nvidia settings manager.

however a few people where able to "per pixel" scan on their TVs. and that got it working... so open the menu on ur tv and look for stuff like tht :-). 

as for changing back ur driver. there is this:

```
sudo dpkg-reconfigure xserver-xorg
```

which will let u re-configure video settings. but i've never used it, so cant advise if it goes wrong or u get stuck...

to get the changes to show:

```
sudo /etc/init.d/gdm restart
```

---

### Post by aeiah on 2011-08-17
if its going to just be a server, why is it plugged into your TV?

what are you hoping to 'serve' with it? you might find it easier just to ssh into it from another computer if the only reason you've plugged it into a tv is to be able to set some services up.

---

### Post by SilverJS on 2011-08-17
Hi there,
 
Thanks for the suggestions. I'll look at the TV when I get home.
 
As for what I'm serving with it : Currently, as it's a testbed, it's in the living room with me, running through my receiver. =) (I also have my regular HTPC there.) "Server" is actually misleading - it's really a back-up box, as my HTPC is also my real file server with XBMC under W7. 
 
I don't know how to SSH into a box, but the plan is to eventually do that anyways, so might as well start. =) I always wanted to run it headless anyways.
 
Any tips on where to start to do that?
 
EDIT : Disregard my last - there's TONS of guides on SSH on the web.  Still would like some help with setting the overscan on the default video drivers (if that's even possible), though.  Thanks!  =)

---

### Post by SilverJS on 2011-08-18
Found it.  =)  The overscan problem was actually in my TV settings.  
 
The Font size is in the desktop (Right-Click) -> Fonts -> Details, I believe.  Size (DPI) can be adjusted there.

---

