---
title: "terminal window in tightvnc is empty"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by hairytorus on 2009-06-25
I am trying to vnc into a remote ubuntu (7.*) server.  When I install vnc and successfully login the terminal that automatically opens does not have a command line.  It is just a blank window.  In the past I received an error stating that tighvnc could not find the default font path.  Though it started successfully on those occasions I had the same terminal problem so I believe the solution lies in there someplace.

I have already tried the following:

1) uninstall and reinstall complete with removing the /etc/vnc.conf and the .vnc directories in both root and my private user's home directories

2) setting the font path in /etc/vnc.conf with the following:

       $fontPath .= "/usr/X11R6/lib/X11/fonts/misc/,";
       $fontPath .= "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled,";
       $fontPath .= "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled,";
       $fontPath .= "/usr/X11R6/lib/X11/fonts/Type1/,";
       $fontPath .= "/usr/X11R6/lib/X11/fonts/Speedo/,";
       $fontPath .= "/usr/X11R6/lib/X11/fonts/75dpi/,";
       $fontPath .= "/usr/X11R6/lib/X11/fonts/100dpi/,";
       $fontPath .= "/usr/X11R6/lib/X11/fonts/freefont/,";
       $fontPath .= "/usr/X11R6/lib/X11/fonts/sharefont/";


3) altering /usr/bin/vncserver with the following:

$fontPath = "unix/:7100";

$fontPath = join ',',qw(
/usr/share/fonts/X11/misc
/usr/share/fonts/X11/100dpi/:unscaled
/usr/share/fonts/X11/75dpi/:unscaled
/usr/share/fonts/X11/Type1
/usr/share/fonts/X11/100dpi
/usr/share/fonts/X11/75dpi
);

---

