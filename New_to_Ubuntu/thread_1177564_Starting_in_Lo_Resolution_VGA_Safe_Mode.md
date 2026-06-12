---
title: "Starting in Lo Resolution VGA Safe Mode??????"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by vatek1 on 2009-06-03
My kids have somehow changed my Nvidia Video Driver. Computer boots past ubuntu screen but display goes blank and stays blank. Is there a Command Line argument that I can add to the CLI editor to force the PC to boot in a safe mode VGA so that I can re-establish the Proper Video Drivers from the Gui. 

I have tried the Grub route and also tried the install Disk to trie to repair the installation and have had no luck. I am a newbie so please excuse my ignorance. I have a redhat book somewhere , but I believe I left it at work. Any help would be greatly appreciated!

Thanks
Forrest

---

### Post by Hospadar on 2009-06-03
Were you using (successfully?) the nvidia driver originally?

There's a couple ways to go about fixing your problem, all of which involve restoring the /etc/X11/xorg.conf file to some previous and hopefully functional state.

If you just want to blow it out and return to the original state (at which point you can re-install your nvidia-driver through the driver manager, or however you prefer) you can run "sudo dpkg-reconfigure -phigh xserver-xorg"

If you want to try and go back to a previous setup (if you had a dual screen setup that took a long time to get working for example) almost every program that edits /etc/X11/xorg.conf leaves backup copies in /etc/X11 (often named xorg.conf.backup<some date or something else>) if you delete or rename your current xorg.conf (renaming is safer in case you need it later) and then rename or copy one of the backups (that you think is the right one, if not, you can always keep guessing) to /etc/X11/xorg.conf

A couple notes:
-When you boot up, if your video fails totally, you can Ctrl-Alt-F1 to get to a virtual terminal (Ctrl-Alt-F7 will get you back to where the desktop should be)
-You can restart your X server an graphics environment with "sudo /etc/init.d/gdm restart" (you can also replace restart with start and stop).  This is the same script your computer uses at boot time, you'll need to run it after changing xorg.conf to see the effects
-I'm assuming you have some familiarity with the command line (ability to list files, change directory, copy/move/rename files)
If not, you should take a quick peek at a linux CLI tutorial, google and you'll find a million of them

---

