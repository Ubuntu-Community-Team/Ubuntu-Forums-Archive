---
title: "New to Ubuntu, have some Qs."
date: 2009-04-25
forum: New to Ubuntu
---

### Post by vtnwesley on 2009-04-25
Hi,

Just recently tried the new 9.04 Ubuntu due to all the good press. I'm not experienced with linux but I am fairly experienced with Windows and computers in general. I have a few questions about what I've experienced thus far.

1. I'm told Intel drivers for video are included out of the box and should work. Despite this, a random lowend game I pulled off Synaptec to see how it all functioned is having major performance issues. Maybe it's just the game, but this seemed odd to me. Is there a way to verify the driver is installed and functioning properly?

2. Maybe it's just because it's a slightly older P4 box, but flash performance seems pretty low too. Youtube chokes quite a bit. I've heard some rumblings on the forums/irc that others are having Firefox issues. Any ideas if this is firefox, flash, or the system itself?

3. Movie Player unconditionally crashes whenever trying to run any kind of media. Do I need codec plugins or something to make it work properly? Is this a known issue?

4. Is there anyway to disable PC speaker system noises or at least replace them with start audio system noises?

5. Is there anyway to make the file manager accept a blanket default setting to "sort by type, view in detailed list" without going directory by directory?

Anyhow. Guess that's all I wanna know for now. So far so good. I don't think I'd replace my Windows anytime soon, but it would seem desktop linux has come a long way in the last few yrs. I've liked what I've seen so far, outside of the whole media player problem of course. :)

Thanks for the help in advance.

---

### Post by steve101101 on 2009-04-25
here are a few answers:

3) totem the movie player / vlc should work fine. and they should prompt you to install the needed codecs.

4) yes it is quite easy. [http://www.howtogeek.com/howto/ubuntu/disable-the-system-beep-on-ubuntu-edgy/](http://www.howtogeek.com/howto/ubuntu/disable-the-system-beep-on-ubuntu-edgy/)

---

### Post by adult swim on 2009-04-25
1 maybe enabling uxa will help your situation 
do it by going to a terminal, applications>accessories>terminal, and entering in ```
gkusu gedit /etc/X11/xorg.conf
``` then find the section that says ```
Section "Device"
        Identifier      "Configured Video Device"

``` and add the uxa option so it looks like this ```
Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"           "UXA"
``` save and close the file then log out and log back in. your video performance should improve (note this is buggy for some people but for some it is worth it.  im not experiencing any bugs)

2 flash is usually not up to par on linux,  1's fix may help a little

3 from a terminal, again run ```
sudo apt-get install ubuntu-restricted-extras
``` note you may need to go to system>preferences>software sources and make sure that the first 4 boxes are checked if you get any errors on this

4 from a terminal run ```
sudo modprobe -r pcspkr
``` to remove it for this session.  if you want to make it permanent run this from a terminal ```
gksu gedit /etc/modprobe.d/blacklist.conf
``` and to the bottom of the file add a line that says ```
blacklist pcspkr
```

5 open the file manager and go to edit>preferences.  the first 2 options you can select the settings you described

---

### Post by vtnwesley on 2009-04-25
Thanks guys. Appreciate the help. I'll definitely give all that a shot. Sounds promising.

---

### Post by steve101101 on 2009-04-26
yep. also remember just to always ask a question here to get any help. this forum makes ubuntu and linux in general a viable operating system.

---

