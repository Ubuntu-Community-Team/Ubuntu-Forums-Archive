---
title: "I've really borked something"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by walter_jnr on 2010-07-28
Sorry for the vague title but I have no idea what to call this. Basically all new windows I open get pinned to the top of the screen and anything that opens after that gets pinned directly on top. The top of the window is always cut off so I can't even hit the "x" to close it. Grrr. 

As you have already gathered I'm a total Linux noob. I have run a few distros before but the longest I lasted was about 6 months quite some time ago. This time I decided to take the plunge again and installed Kubuntu 10.04. At this point I usually give up and go back to Windows but I really want to stick it out this time. I know it will only end up being something stupid I changed but I really want to find out so I can learn more about all this. 

Some other symptoms: My number of desktops has reverted to one when it was four previously and the left side of my taskbar has changed to what looks like a section of a wallpaper instead of the usual grey. 

I can see some of the more advanced guys spitting their coffee all over their monitors and laughing so I apologise for that and I hope I didn't cause you too much damage. :D

Please help. 

:cry:

---

### Post by jtarin on 2010-07-28
> **walter_jnr said:**
> Sorry for the vague title but I have no idea what to call this. Basically all new windows I open get pinned to the top of the screen and anything that opens after that gets pinned directly on top. The top of the window is always cut off so I can't even hit the "x" to close it. Grrr. 

As you have already gathered I'm a total Linux noob. I have run a few distros before but the longest I lasted was about 6 months quite some time ago. This time I decided to take the plunge again and installed Kubuntu 10.04. At this point I usually give up and go back to Windows but I really want to stick it out this time. I know it will only end up being something stupid I changed but I really want to find out so I can learn more about all this. 

Some other symptoms: My number of desktops has reverted to one when it was four previously and the left side of my taskbar has changed to what looks like a section of a wallpaper instead of the usual grey. 

I can see some of the more advanced guys spitting their coffee all over their monitors and laughing so I apologise for that and I hope I didn't cause you too much damage. :D

Please help. 

:cry:

My coffee was luckily in the other room....Can you remeber what you changed before this happened? Your virtual desktops..a right click on the taskbar where the desktops are displayed in the corner. Select preferences.Change number of desktops to as many as you want.
The window at the top thing I usually place a panel there, make it transparent or auto-hide and adjust the size. There is probably another way to do it, but these methods work for me as I always need extra access besides menu to monitor differnt apps.
Get into the habit of locking applications to thepanel so they don't get moved around....you can drag them when they are unlocked to a location that suits you. You can also place spacers between the icons. All by a right-click.

---

### Post by k3lt01 on 2010-07-28
> **walter_jnr said:**
> Sorry for the vague title but I have no idea what to call this. Basically all new windows I open get pinned to the top of the screen and anything that opens after that gets pinned directly on top. The top of the window is always cut off so I can't even hit the "x" to close it. Grrr.  Try hitting F11 on your keyboard, that is the Full screen signal which I used to have to use on Firefox a few years ago for some as yet unknown reason. If it works how I think it will w should b able to figure out a work around.

> **walter_jnr said:**
> As you have already gathered I'm a total Linux noob. I have run a few distros before but the longest I lasted was about 6 months quite some time ago. This time I decided to take the plunge again and installed Kubuntu 10.04. At this point I usually give up and go back to Windows but I really want to stick it out this time. I know it will only end up being something stupid I changed but I really want to find out so I can learn more about all this. Learning is good, and this is one of the best places to learn

> **walter_jnr said:**
> Some other symptoms: My number of desktops has reverted to one when it was four previously and the left side of my taskbar has changed to what looks like a section of a wallpaper instead of the usual grey. The only thing I can think of is you have inadvertently selected the desktop function and told it to have 1. Th taskbar is one reason I think this as it appears you have also adjusted the transparency. Try right clicking on the taskbar and select properties and see what that brings up.

I'm not all that good with Kubuntu (KDE) so hopefully someone who is will be able to help guide you.

---

### Post by 4rtur on 2010-07-28
Just noticed it's Kubuntu, so not sure whether my reply is any help at all.



For placing windows use CompizConfig Settings Manager, go to Window Management -> Place Windows and set Placement Mode to Centered. Also to solve Window Manager problems it's useful to install Compiz Fusion Icon, it's in your try when launched and you can use it to reload Window Manager. Good luck ;)

---

### Post by walter_jnr on 2010-07-28
I've remember playing with the resolution settings but I can't see what I've done wrong to be honest. The monitor resolution is correct and the refresh rate is fine. I don't think I even changed anything else. I changed a few settings in Compiz and installed a few things with Wine (Just WoW to see if it would install and run which it did). Other than that I can't think of what I might have done.

---

### Post by walter_jnr on 2010-07-28
> **k3lt01 said:**
> Try hitting F11 on your keyboard, that is the Full screen signal which I used to have to use on Firefox a few years ago for some as yet unknown reason. If it works how I think it will w should b able to figure out a work around.


When I hit F11 it does the full screen thing but it appears that it is in it's own little section of the monitor (Like it thinks that little section is the entire screen).

---

### Post by k3lt01 on 2010-07-28
That's strange. Sorry but my knowledge of Kubuntu is sadly lacking :(

---

### Post by walter_jnr on 2010-07-28
Actually I remember what I was doing right when this happened. I downloaded the Linux drivers for Nvidia and when I tried to run the file (.run file) it opened up in Kate (I think) and then it started to bug out. I don't know if that helps at all.

---

### Post by 4rtur on 2010-07-28
> **walter_jnr said:**
> I downloaded the Linux drivers for Nvidia and when I tried to run the file (.run file) it opened up in Kate (I think) and then it started to bug out. I don't know if that helps at all.

I don't think this has anything to do with your problems, have you tried reloading Xorg ?

---

### Post by walter_jnr on 2010-07-28
> **4rtur said:**
> I don't think this has anything to do with your problems, have you tried reloading Xorg ?

Is that by killing the process? That seems to log me out and when I log in there is no change. Another thing I have noticed is that I can't type in the admin password boxes for mounting my drives at boot. Actually even the ones for authorising the package removals don't seem to allow input although I can paste into them.

---

### Post by walter_jnr on 2010-07-28
Another interesting development: I created a new user and all the previous problems have more or less gone however I seem to be on a Ubuntu desktop now. I have the maximize and minimize buttons again and things are working in full screen. I guess something got corrupted in the user account? Honestly, I have no idea as you can tell but I still want to figure this out as it can only help me in the future. 

Sorry to be such a pain BTW and thanks for all or your help so far.

---

### Post by 4rtur on 2010-07-28
I would dig in Compiz settings first.

---

### Post by walter_jnr on 2010-07-29
I've decided this one may be too much for me so I'm going to backup and reinstall/repair now and research an effective backup strategy. I didn't think I would need one so soon. Ahhh, the joys of learning a new OS. :p I'm not going to give up on Kubuntu so easily but this one is just too much too soon. Ha ha. Expect to see me lurking for more info really soon. 

Thank you everyone for your help. It's appreciated.

---

