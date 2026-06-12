---
title: "Why I cannot use GUI logon? HELP!"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by Foobarz on 2011-07-25
Aight, this is an SOS message cause I really need a GUI so I can finish the book report I wrote with Libreoffice. Outline of the problem:
      1. Removed the fglrx proprietary driver from ubuntu 11.04, suspended for dinner and turned into black screen for a good while; I performed hard reset.
      2. Turned on computer again, typed in password but could not logon. Screen turns black with a line of text, but goes away so fast that I do not know what is says. It returns me to the login screen. I tried safe mode, failsafe graphics mode, all the different sessions, nothing. . . 
      3. Looked at some threads and, through tty logon, reconfigured xserver and everything associated with gnome, and checked if hard drive was full. Nothing. I dont think its a problem with X or GNOME, but I am not sure at all. 
If anyone knows anything on fixing this problem, please contact me.

---

### Post by 2F4U on 2011-07-25
Did you check the log files if they contain error messages? Did you check .xsession-errors?

---

### Post by wildmanne39 on 2011-07-25
> **Foobarz said:**
> Aight, this is an SOS message cause I really need a GUI so I can finish the book report I wrote with Libreoffice. Outline of the problem:
      1. Removed the fglrx proprietary driver from ubuntu 11.04, suspended for dinner and turned into black screen for a good while; I performed hard reset.
      2. Turned on computer again, typed in password but could not logon. Screen turns black with a line of text, but goes away so fast that I do not know what is says. It returns me to the login screen. I tried safe mode, failsafe graphics mode, all the different sessions, nothing. . . 
      3. Looked at some threads and, through tty logon, reconfigured xserver and everything associated with gnome, and checked if hard drive was full. Nothing. I dont think its a problem with X or GNOME, but I am not sure at all. 
If anyone knows anything on fixing this problem, please contact me.Hi, the driver you uninstalled is a video card driver that is most likely the problem if you did not crash ubuntu by doing a hard reset. Here is a link that should allow you to boot so you can fix your video driver issue.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Foobarz on 2011-07-25
Just a quick clarification, my video card driver is broken, but I can still see the login screen perfectly? @wildmanne39, thank you for the help, but I looked through that thread and it only shows me how to change the video card boot settings. However, I CAN boot fine. GRUB splash displays fine, even the GNOME login displays fine. I CAN login with tty. But I CANNOT login with a GUI. I will try to take a photo of that line of text that suddenly appears then disappears, and I will post my findings on here.

Update: I took a video of my login and paused it at the correct millisecond. After typing in my password and hitting enter, the screen turns black and this pops up:

"Starting CUPS printing spooler/server     [OK]
                         Checking battery state [OK]
Stopping System V runlevel compatibility  [OK]"

Then it goes away extremely quickly and the login screen pops up again. Someone, help meh!

---

