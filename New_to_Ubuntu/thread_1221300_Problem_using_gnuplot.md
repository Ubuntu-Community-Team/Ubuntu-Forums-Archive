---
title: "Problem using gnuplot"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by cosmoli on 2009-07-23
When trying to use gnuplot, I encounter the error message "Failed to initialize wxWidgets." I can't find the package wxWidgets, and don't know how to e.g. get at the repository mentioned in [http://ubuntuforums.org/showthread.php?t=3033](http://ubuntuforums.org/showthread.php?t=3033). 

Does anybody know how to solve this problem? 

Thanks in advance...

---

### Post by llamabr on 2009-07-23
[http://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu](http://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu)

You need to update your repos

---

### Post by cosmoli on 2009-07-23
> **llamabr said:**
> [http://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu](http://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu)

You need to update your repos

Thanks so far. I did sudo apt-get install libwxgtk2.8-dev libwxgtk2.8-dbg

The packages were installed. 
 
I'm then trying to use gnuplot:


	G N U P L O T
	Version 4.2 patchlevel 3
        bla bla bla

Terminal type set to 'wxt'
gnuplot> plot 'psi_mode0_center_in_bubble_nf0.49_eff6.4_z7.56_256_143Mpc.pk'
Failed to initialize wxWidgets.

I.e. the wxwidgets still seem to not be installed. I'm trying to use Xterm:

gnuplot> set term X
Terminal type set to 'x11'
Expected X11 driver: /usr/local/libexec/gnuplot/4.2/gnuplot_x11
Exec failed: No such file or directory
See 'help x11' for more details
Warning:  Could not write history file!!!
Options are '0'
gnuplot> plot 'psi_mode0_center_in_bubble_nf0.49_eff6.4_z7.56_256_143Mpc.pk'
Expected X11 driver: /usr/local/libexec/gnuplot/4.2/gnuplot_x11
Exec failed: No such file or directory
See 'help x11' for more details
Warning:  Could not write history file!!!

So it's not working as it should...

---

### Post by tgalati4 on 2009-07-23
What is the output of:
apt-cache search wxgtk

and

apt-cache search wxWidget

---

### Post by josce on 2010-06-24
If you're using gnuplot through ssh, check that X is enabled (you need to use ssh -X). You can check that by trying to launch any graphical application, such as xclock or whatever.

Gnuplot sometimes returns this error instead of reporting that it is unable to open display.

---

