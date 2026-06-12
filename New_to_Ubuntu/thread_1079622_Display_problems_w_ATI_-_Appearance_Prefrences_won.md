---
title: "Display problems w/ ATI - Appearance Prefrences wont save"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by bigxmp on 2009-02-24
I am a relatively new Ubuntu user so bare with me on this description of the problem....This is occuring on my Toshiba Satellite, 8.10 Ubuntu,AMD 64x2, and ATI Radeon X1200

Everything was working perfectly until I attempted to connect my laptop to my HD-TV via VGA cable and I lost all of my original settings within Compiz, Screen Resolution, Appearance Preferences, etc.  Somehow the ATI Catalyst changed my preferences in the process of connecting to the TV, so now every time I login my resolution is massive, I only can see 3/4 of the desktop background, a 1/4 of my desktop display is some brown image and, on the lowest appearance preferences (not the extra) 

I have to open the Catalyst and refresh my display settings to 1280x800 (which it says it is currently on) so that it displays properly, then I have to go into the Appearance Preferences and manually change it to "Extra" and finally into Compiz to edit the settings.  Once everything is changed, it works fine but it never saves the settings I put in place.  I'm going to add a picture of what my display looks like once logged in.

After I shutdown / restart, I have to repeat this same process over and over everytime I log in now.... any ideas, this is becoming quite frustrating.

---

### Post by taseedorf on 2009-02-26
try running Catalyst Control center as root.

type into terminal

sudo amdccle

should let you save.

nvidia's control center (i have an nvidia card) does not let you save settings unless you run as root

---

