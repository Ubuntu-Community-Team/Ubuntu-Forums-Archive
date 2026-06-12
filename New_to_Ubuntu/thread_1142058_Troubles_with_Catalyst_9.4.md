---
title: "Troubles with Catalyst 9.4"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-28
so i installed catalyst 9.4, and it actually worked. 

however, to get x to start, i have to type "startx" in the shell.

apparently, startx doesnt actually give me my real computer. 
nothing works right now:
- i cannot launch either add/remove programs or synaptic without using "sudo" first
- i have no sound. when i launch volume control, i get 
> No volume control GStreamer plugins and/or devices found.
- compiz still won't enable. i have no desktop effects. 

i don't understand linux. errors like this make me think that ill never understand it. why does installing catalyst 9.4 affect sound?????
it seems completely illogical. 
it's like changing your oil and having your wheel fall off :confused:
i don't get it.

can someone please explain to me how either launching "startx" or installing catalyst 9.4 could affect my sound server?

---

### Post by asuastrophysics on 2009-04-28
nobody has any ideas???
    yeah, because this makes about as much sense as abstract art.

so i've come to the conclusion that i can either have hal running (movable mouse) or i can have audio, but not both. 

when the computer starts up without hal, the login sound plays.

with hal, the sound doesnt play and i have no audio.

and i have no idea what is making hal decide to either launch or not launch

this is really puzzling.....

does anyone have any ideas?

---

### Post by asuastrophysics on 2009-04-28
***EDIT***
so everyone knows from me wasting 3 hours of my time:

If you install the Catalyst 9.4 driver, SOMEHOW God knows why, the Xauthorization file is messed up and is chowned by root.

consequently, things that used to start without the *sudo prefix now won't start.
**A fine example of this is ALSA, which is what this thread was about in the first place. It wasn't starting.**
***Even if you follow the installation manual BY THE LETTER, THIS WILL HAPPEN. 

This is how to fix it. 
Just type 
> sudo chown username:username .Xauthority 

And I'm really glad that nobody out there knew why my sound wasn't working. 

**_Compiz still won't start. This problem is still unsolved._**

Since upgrading to Jaunty, I can't get compiz to work with either the open source driver OR the BRAND NEW Catalyst 9.4
This is the output of compiz:
> girdy@girdy-desktop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 455: /usr/bin/compiz.real: not found

Now my question is: Is compiz not running because it can't find XGL? If so, how do I install XGL?

---

