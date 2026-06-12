---
title: "GBM Configuration File"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by keemosabi on 2009-07-03
I inserted an xrandr command into my gbm.conf and gbm.conf-custom files to choose the correct resolution on startup, but now I can't even get to the logon screen.  It says that a logon server cannot be started.  What can I do to fix this?

---

### Post by verbal.kint on 2009-07-03
you could try pressing ctrl+alt+F6 to switch to a console view and maybe will be able to log in with the command line.


If you can get to a command line you can try and reconfigure your xorg using this command
```

$ sudo dpkg-reconfigure xserver-xorg
```

---

### Post by keemosabi on 2009-07-03
> **verbal.kint said:**
> you could try pressing ctrl+alt+F6 to switch to a console view and maybe will be able to log in with the command line.


If you can get to a command line you can try and reconfigure your xorg using this command
```

$ sudo dpkg-reconfigure xserver-xorg
```
That didn't work but I was able to fix it by reinstalling the Ubuntu Desktop from the command line.  However, I get this really weird problem where whenever I boot Ubuntu I get an input signal out of range problem.  Then, if I wait about 1 minute, the login screen eventually appears and the error message goes away.  I tried putting and xrandr command in the gdm.config-custom file to choose the correct resolution but that doesn't solve the problem.  What can I do to fix this?

I have included my gdm.config-custom file below:```
# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# Older versions of GDM used the "gdm.conf" file for configuration.  If your
# system has an old gdm.conf file on the system, it will be used instead of
# this file - so changes made to this file will not take effect.  Consider
# migrating your configuration to this file and removing the gdm.conf file.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# /usr/share/gdm/defaults.conf file for information about each option.  Also
# refer to the reference documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# e.g, the "Enable" key in the "[debug]" section would be "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!


[daemon]
xrandr  --output default --mode 1024x768

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]


```

---

