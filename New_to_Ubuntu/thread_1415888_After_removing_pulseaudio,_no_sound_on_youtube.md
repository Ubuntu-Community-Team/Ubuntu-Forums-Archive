---
title: "After removing pulseaudio, no sound on youtube"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by came2die on 2010-02-25
Hello guys. I really need help, because I literally have enough. Hope you understand me and will try to help.

I did this:


Here is what I did to remove pulse audio in Karmic:

Code:

$ sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio

Code:

$ sudo apt-get autoremove

Code:

$ sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui

Code:

$ sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer

restart your computer!

Notes:
-run gstreamer-properties in terminal to set defaults to alsa (the old system/preferences/sound in jaunty)

    This means:
    Code:

    $ gstreamer-properties

-remove gstreamer0.10-pulseaudio to get sound in totem.

    The above commands should have taken care of that, but it never hurts to be sure when talking about the hydra that is PulseAudio.

-gnome-alsamixer is for changing the volume, not an applet but better that nothing

    This means you are left without a panel applet to control volume across the board, thanks to the thoughtful efforts of Canonical to shove PulseAudio down our throats. So you need to have something to control audio with:
    Code:

    $ sudo apt-get install gnome-alsamixer

    And something to keep gnome-alsamixer within easy reach, provided by AllTray:
    Code:

    $ sudo apt-get install alltray

Now, one last word of advice. Usually the best solution is to use aptitude or synaptic to do these moves, but you'll run headfirst into their dependency resolution efforts, which command them to put PulseAudio back in your system when reinstalling gnome-alsamixer. So either you use apt-get or you reconfigure aptitude/synaptic dependency resolution to work the way you want.

[B]Amarok works, but there is no sound on youtube.
I tried to install libflash support and such things but it doesn't help. I can't reinstall ubuntu because sound is stuttering when using PA.[/B]

Please help, because this is my fathers computer and I don't want him to go back to M$.

---

### Post by Kakers on 2010-02-25
Urgh alsa drivers I had a field day with those... this Dell Laptop had a problem where sound would come out of the speakers and headphones and had to get the latest drivers which had to be compiled.

Also for flash I used:[FONT=monospace]
sudo apt-get install -y[/FONT] --force-yes flashplugin-nonfree

If you are going to remove libflash and use this one make sure all other versions of flash are completely removed from ~/.mozilla/plugins directory

---

### Post by came2die on 2010-02-26
Ahh thanks man, that worked. Don't know how is that possible because I tried all sorts of those plugins ...
Thank you again.

---

