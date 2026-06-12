---
title: "Please explain upstart to me"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by davecgs on 2009-03-18
From what I've read, upstart makes it rather challenging to generate various boot modes in Ubuntu.  That feels annoying.  Any other distro that I've played with you can switch run modes using kernel parameters or the inittab function.

Now I read about update-rc.d which is more of a package manager kludge that updates the soft links to disable or enable the gmb.  Here is what I want to do:

1) I want to boot into text mode
2) I want to launch the graphic desktop when I need it vs. going through a lot of sweat just to make it work.

In any other distro it's startx and I'm there.  

Help is welcome and thanks...

---

### Post by Temposs on 2009-03-18
I think a way to accomplish what you want is to boot as normal and then choose the Options button at the bottom left of the login screen, then click "Choose Session". Then you'll be given a choice of various modes to boot into. I know with the terminal option there you can easily start graphical programs too, no problem.

---

### Post by 3rdalbum on 2009-03-18
That's easy!

Go to System > Administration > Services and turn off the "gdm" service. When you boot up next, X will not run.

To start X, run the command "sudo gdm".

Unfortunately I don't know of a way to specify on the kernel line or in GRUB an option to start X automatically. I was under the impression that runlevels still worked in Ubuntu, but then I haven't played around with it.

---

### Post by iamkrazee on 2009-03-18
I switched from redhat family to ubuntu, and I faced the same problem too. Seemingly, there isn't a kernel parameter that you can add to go into, say, runlevel 1. A solution might be to compile your own kernel..

---

### Post by davecgs on 2009-03-18
Thank you everyone.  I get a lot more support than through Fedora which is more of an 'on-your-own' place.
  From what I've read, Ubuntu is based on the Debian setup so that means that there is just one run level.  However to stick you in such a situation to force the graphic - or non-graphic interface seems a bit crazy to me.
I saw this script on the net -- should have recorded the URL.


   # rc - runlevel compatibility
#
# This task guesses what the "default runlevel" should be and starts the
# appropriate script.
#
# Modified from Ubuntu/gutsy version 2008-02-21 by Emmet Caulfield.
# TJ: bug-fix: removed boot-killing semi-colon from sed expression (;p should be p)
#
start on stopped rcS

script
	runlevel --reboot || true

	RL="$(sed -ne 's/.*init \([2-5S]\).*/\1/p' /proc/cmdline || true)"
	if [ -n "$RL" ]; then
	    telinit $RL
	elif [ -r /etc/inittab ]; then
	    RL="$(sed -n -e '/^id:[0-9]*:initdefault:/{s/^id://;s/:.*//;p}' /etc/inittab || true)"
	    if [ -n "$RL" ]; then
		telinit $RL
	    else
		telinit 2
	    fi
	else
	    telinit 2
	fi
end script

Now all is needed is to disable Gnome (or KDE) from starting. Unfortunately the standard tool, update-rc.d, won't remove existing links in the /etc/rc?.d/ directories. 
$ sudo update-rc.d  gdm start 30 2 . stop 01 0 1 6 .
 System startup links for /etc/init.d/gdm already exist.


Although possible, it's recommended not to manually add/remove the links since if update-rc.d is upgraded its postinst script will cause links to be recreated. 

Instead, install sysv-rc-conf, a ncurses text GUI that handles the init services nicely. 
sudo apt-get install sysv-rc-conf

Now run it and deselect gdm and any other services you don't want to run for your customised runlevels. Press q to save the changes and quit:

---

### Post by davecgs on 2009-03-18
This is one user's solution to the problem.

[http://caulfield.info/emmet/2008/03/add-a-textonly-runlevel-to-ubu.html](http://caulfield.info/emmet/2008/03/add-a-textonly-runlevel-to-ubu.html)

---

### Post by zika on 2009-03-18
You might want to take a look at sysv-rc-conf. it is a CLI tool to switch on and off (almost) everything that is going on at boot. in Ibex I switched that way gdm off but there was a side-effect that, for example, USB would not mount automatically when You plug it in. there was another thing that did not work either and that made me turn gdm on again, but I can not remember now what it was. I have not tried that yet on Jaunty. with gdm switched off You boot into CLI and then startx gives You X. right before I was writing this I have switched bluetooth off (since I do not use it)... :) that tool is one of the "first things I install after clean install" ... ;)

---

### Post by davecgs on 2009-03-19
Thank you and I will

---

