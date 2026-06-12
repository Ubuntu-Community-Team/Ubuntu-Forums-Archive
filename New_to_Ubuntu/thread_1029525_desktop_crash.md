---
title: "desktop crash"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Gerard08 on 2009-01-03
Greetings,

Running 8.04 on a home built AMD 64 system. I was following a guide to install MPlayer from source. I read that I needed to makes sure certain files were present or get them from the repositories.  I needed quite a few to make the gui part of the program to install. After using synaptic to do this, I restarted, and my desktop had crashed-I could log in but didn't see icons and the tool bars did not function.

I have a live-disk.  How do I undo what caused this?

---

### Post by mapes12 on 2009-01-03
```
sudo apt-get install ubuntu-desktop
```Should restore your desktop and dependent packages.

---

### Post by Gerard08 on 2009-01-03
Mapes12-- I can reboot into a "test mode" and command line. Do you know what the command is to restore the desktop? Thanks!

---

### Post by mapes12 on 2009-01-04
The only thing I can suggest is trying the command with the reinstall switch like this```
sudo apt-get --reinstall install ubuntu-desktop
```If that doesn't work then make a copy of /home on external media, reinstall from scratch then copy across the backup of /home to reinstall your files, settings and the like.

BTW - MPlayer is in the repo's. You shouldn't need to compile it from source?

---

### Post by Zimrie on 2009-01-04
Try Ctrl+D in CLI environment

---

### Post by Gerard08 on 2009-01-04
Hi mapes12:

I tried the fix you suggested: The dialogue went fine until apt tried to access a repository. It was denied, and I was returned to the command line.

edit: I established contact with server and request went through. No Change in desktop appearance.

> **mapes12 said:**
> ```
sudo apt-get install ubuntu-desktop
```Should restore your desktop and dependent packages.

I have also tried the following fixes:

```
top
kill -9 PID # a number of processes came up:

x.org, nm-applet, at-spi-registry

CTRL D

Alt + SysRQ + [RSEIB}
```

There is a new development: this message:

> [no entry symbol] assisted technology support  has been requested for this session but the accessibility registry not found. Please ensure that the AT-SPI package is installed. Your session has been started without assisted technology support.

When I went back to the desktop I found a completely blank screen.

One more thought-- The guide said:

> To compile MPlayer with X11 support, you need to have the X window development packages (like for Xfree86 or X.org)installed.  
-For the GUI you need the GTK development packages.

I know I selected quite a few development packages in both these areas of the repos.  That is where I am so far.  Thanks

An update:  Booted up normally--not in safe mode. Full desktop functionality. Maybe this was not related to my mess of package installs I found this in the syslog:

> Jan  4 14:43:59 desktop syslogd 1.5.0#1ubuntu1: restart.
Jan  4 14:43:59 desktop anacron[6105]: Job `cron.weekly' terminated
Jan  4 14:43:59 desktop anacron[6105]: Normal exit (2 jobs run)
Jan  4 14:55:32 desktop gdm[6687]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

This string has a few posts about it.

---

### Post by Gerard08 on 2009-01-04
> **Zimrie said:**
> Try Ctrl+D in CLI environment

This fix did not work: The result was "one process stopped"

---

