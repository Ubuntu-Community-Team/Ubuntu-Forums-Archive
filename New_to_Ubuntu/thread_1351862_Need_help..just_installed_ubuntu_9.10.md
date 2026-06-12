---
title: "Need help..just installed ubuntu 9.10"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by RjNeLLY on 2009-12-11
Hi, i just installed ubuntu 9.10 and it was installed properly. Now, when I was trying to install compiz to get the cube effect, I get the "desktop effects could not be enabled".  Now i know theres lots of thread in this forum about it but I seem to be lost and could not understand it.  I got the "how to" on youtube on how to install compiz and first steps are: system>appearance>preference>visual effect and extra> and thats when i get the error??? on the threads here, it talks about commands and prompts which i have no clue that you have to do that.  CAN ANYONE HELP ME PLEASE????

---

### Post by MelDJ on 2009-12-11
have you installed your graphic card?
see if there are drivers available in system-admin-hardware drivers

---

### Post by Geoff918 on 2009-12-11
Perhaps you need some restricted drivers enabled?

I've observed this on a few of my friend's systems. To be honest, it works fine on my systems and I never figured it was important enough to fret over with my friend's systems. It's just eye-candy, afterall. :)

For someone who may be better able to help, you may wish to report the following:

from CLI (Applications -> Accessories -> Terminal)

sudo lspci -v

or maybe

sudo lshw -html >> hardware.html

the 2nd command would give a nice output of all your computer's hardware in HTML format in your home folder.

---

### Post by blackmail on 2009-12-11
If want to install drivers in an easy fashion you could just look for envy from the add/remove, and install it. It helps quite a lot if you have ATI or nVIDIA video cards.

---

### Post by garvinrick4 on 2009-12-11
COPY AND PASTE THESE INTO TERMINAL. WILL GIVE YOU A GOOD START.

 sudo apt-get install compizconfig-settings-manager gnome-art usplash startupmanager compiz-fusion-plugins-main compiz-fusion-plugins-extra emerald screenlets librsvg2-common fusion-icon gnome-splashscreen-manager libart2-ruby1.8 libatk1-ruby1.8 libcairo-ruby1.8 libemeraldengine0 libgconf2-ruby libgconf2-ruby1.8 libgdk-pixbuf2-ruby1.8 libglade2-ruby libglade2-ruby1.8 libglib2-ruby1.8 libgnome2-ruby libgnome2-ruby1.8 libgnomecanvas2-ruby1.8 libgtk2-ruby1.8 libpango1-ruby1.8 libruby1.8 libtidy-0.99-0 python-chardet python-compizconfig python-evolution python-feedparser python-gtkmozembed python-utidylib python-wnck ruby ruby1.8
  

   sudo apt-get install ubuntu-restricted-extras gstreamer0.10-ffmpeg gstreamer0.10-pulseaudio gstreamer0.10-alsa gstreamer0.10-plugins-good gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
  

   sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio

---

### Post by marshmallow1304 on 2009-12-11
> **garvinrick4 said:**
> COPY AND PASTE THESE INTO TERMINAL. WILL GIVE YOU A GOOD START.

 sudo apt-get install compizconfig-settings-manager gnome-art usplash startupmanager compiz-fusion-plugins-main compiz-fusion-plugins-extra emerald screenlets librsvg2-common fusion-icon gnome-splashscreen-manager libart2-ruby1.8 libatk1-ruby1.8 libcairo-ruby1.8 libemeraldengine0 libgconf2-ruby libgconf2-ruby1.8 libgdk-pixbuf2-ruby1.8 libglade2-ruby libglade2-ruby1.8 libglib2-ruby1.8 libgnome2-ruby libgnome2-ruby1.8 libgnomecanvas2-ruby1.8 libgtk2-ruby1.8 libpango1-ruby1.8 libruby1.8 libtidy-0.99-0 python-chardet python-compizconfig python-evolution python-feedparser python-gtkmozembed python-utidylib python-wnck ruby ruby1.8
  

   sudo apt-get install ubuntu-restricted-extras gstreamer0.10-ffmpeg gstreamer0.10-pulseaudio gstreamer0.10-alsa gstreamer0.10-plugins-good gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
  

   sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio

Sorry, but why is all that necessary?  A great deal of that has nothing to do with compiz.


To the OP: As others have said, check System->Administration->Hardware Drivers for graphics drivers.  Also, try using the [compiz-check script]("http://forlong.blogage.de/entries/pages/Compiz-Check") to find the problem.

---

### Post by garvinrick4 on 2009-12-11
I thought you had just fresh installed and wanted compiz and I threw in some things that
I thought might get a nice start to a set-up. Use what you want do not use, makes me no mind. Maybe someone
else will read and want to get a group of things installed quickly. I keep 1 partition for
testing the Alpha's so I keep a group of these on hand to load quickly if want to fresh install. Have a nice day.

---

