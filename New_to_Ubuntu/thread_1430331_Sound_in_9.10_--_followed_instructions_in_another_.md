---
title: "Sound in 9.10 -- followed instructions in another thread..."
date: 2010-03-15
forum: New to Ubuntu
---

### Post by Jennytalia on 2010-03-15
with no luck at all.  The thread is found here. ([HOWTO: PulseAudio Fixes & System-Wide Equalizer Support - Ubuntu Forums)]("http://ubuntuforums.org/showthread.php?t=789578")

So at step 5 I am instructed to launch the applet.  It tells me if I receive an error of 'Connection Refused' to manually launch the applet through Terminal, and gives me (what I assume to be) the commands to do so.

I receive the same errors from Terminal that I receive trying to launch the applet through the Applications menu.

E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:2969): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed

At this point the applet does open, but it has nothing under any tabs, and just sits with the loading wheel until I get frustrated and close it.

I JUST installed ubuntu yesterday.  I used 9.04 for a while, but am still pretty new and uneducated in the ways of terminal.  I don't know what I did wrong, nor how to fix it.  If anyone knows what any of that means and how to fix it to get my sound working, I would be super grateful!

Thanks a million-
Jennytalia

---

### Post by Psumi on 2010-03-16
So do you have pulseaudio, esound, alsa or oss?

If you have any of the last three, no volume applet will work, as pulseaudio is the only sound system in ubuntu that will work with the volume slider. (I have alsa, and I know it won't work with the gnome-voulume applet.)

Don't get upset if you assume that I should assume that you use pulseaudio due to you using that thread. Not everyone does due to their hardware, and ubuntu might've secretly used a different sound system.

---

