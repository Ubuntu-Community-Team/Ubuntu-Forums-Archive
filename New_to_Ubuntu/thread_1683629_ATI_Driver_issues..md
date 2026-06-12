---
title: "ATI Driver issues."
date: 2011-02-07
forum: New to Ubuntu
---

### Post by BXAlbatross on 2011-02-07
Brand new to Ubuntu. Still trying to get used to everything... 
I have a Pavilion dv6 laptop, and dual boot with Windows seven and Maverick. I installed everything fine, got my proprietary drivers running with my ATI card and it all works great. except for one thing.

Catalyst Control Center gives me this error.
>  p, li { white-space: pre-wrap; } There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
  No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
  

What's going on, guys? 

I need it to change my monitor setup. I have an RGB monitor plugged into my laptop. It clones the screen fine, but I want it to display on the external exclusively. Both my laptop and monitor have HDMI ports, would that work?

---

### Post by korleon on 2011-02-07
More info is needed to really help you out.  

What card model do you have? (Radeon 9200 etc.)  

Did you install the drivers through Jockey Menu>System>Administration>Hardware Drives or through some other means?  

Are you sure you installed the drivers or just catalyst?

---

### Post by sandyd on 2011-02-07
> **BXAlbatross said:**
> Brand new to Ubuntu. Still trying to get used to everything... 
I have a Pavilion dv6 laptop, and dual boot with Windows seven and Maverick. I installed everything fine, got my proprietary drivers running with my ATI card and it all works great. except for one thing.

Catalyst Control Center gives me this error.


What's going on, guys? 

I need it to change my monitor setup. I have an RGB monitor plugged into my laptop. It clones the screen fine, but I want it to display on the external exclusively. Both my laptop and monitor have HDMI ports, would that work?
post output of
```

lsmod
```

---

### Post by quadproc on 2011-02-07
> **BXAlbatross said:**
>  I installed everything fine, got my proprietary drivers running with my ATI card and it all works great. except for one thing.

What does the output of _fglrxinfo_ say?
What does the _hardinfo_ program say about Computer>Display>OpenGL Renderer?

I suspect that you have a mismatching version of the driver and X windows or the kernel.  If you did not install it yourself using the ATI file appropriate to your hardware and software then I would suspect such a mismatch.

Installing the driver from the ATI site is fairly easy.  Here is what I do:

Make a directory to use for the install.
Check the ATI site for a driver version that is correct for your processor size (32/64) and for your graphical hardware.
Download that file.  It will be named <some_long_string>.run.
Move the .run file into the directory.
Start a terminal window.
In that window, cd to the directory.
Execute```
 sudo sh <some_long_string>.run --keep --install
```Make sure that there were no complaints about the installation.
Follow the instructions in the graphic window that the installer puts up.  I use the simple and automatic choices.
Wait until the installer finishes.  It can take perhaps a minute or so after you answer the last question.
You can now reboot.  If you get errors or warnings or screwy operation on the restart, then use a command line to execute ```
aticonfig --initial -f
``` This will create or truncate your xorg.conf file to a minimal file so it would be wise to move your old file (if it exists) to somewhere else first, in case you need it later.  I think that you need to sudo this command.

If you want to see a list of compatible software for the driver, then do what I described above except change the --keep --install options to --listpkg.

The --keep option leaves behind all of the files that the installer used.  This allows you to examine them if you so desire.  Once you are done with them you can remove all the files in the directory without bothering the driver.  Or, if you are not interested in seeing those files then you can omit the --keep option.

Once the driver is properly installed then you can install amdcccle and you should not get any complaints from it.

One thing that I learned the hard way: if you are going to change kernels (for example, due to an update), you need to uninstall the old driver first then do a driver install after the new OS is running.  The installation will leave behind a file in /usr/share/ati and the file will have uninstall in its name.

quadproc

---

