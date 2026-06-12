---
title: "Cannot login help meh"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by Foobarz on 2011-07-25
HELP! I seriously derped, and I have a book report to finish. How do I login (seriously with a GUI so I can access Libreoffice!)

How I derped:
1. Removed the fglrx proprietary driver from ubuntu 11.04, suspended for dinner and turned into black screen for a good while; I performed hard reset.
2. Turned on computer again, typed in password but could not logon. Screen turns black and flashes this line of text:
 "Starting CUPS printing spooler/server [OK]
Checking battery state [OK]
Stopping System V runlevel compatibility [OK]"
It returns me to the login screen. I tried safe mode, failsafe graphics mode, all the different sessions, nothing:. . . 
3. Looked at some threads and, through tty logon, reconfigured xserver and everything associated with gnome, and checked if hard drive was full. Nothing. I dont think its a problem with X or GNOME, but I am not sure at all. 
I CAN boot, I CAN display stuff, I CAN login. Login WINDOW is displayed NORMALLY. But I CANNOT login with a GUI what do I do. HELP ME!!!!!

---

### Post by bigpayne69 on 2011-07-25
have you tried to logging in using a live boot disk?

---

### Post by JustinR on 2011-07-25
Hi,

can you login through the TTY (eg. CTRL ALT Fx), then login with your username/password

Type this:
```

cd /usr/share/xsessions
sudo nano gnome.desktop

```

This opens the 'Ubuntu Session' you see in the dropdown box on the login screen, it should look like this:
> 
[Desktop Entry]
Name=Ubuntu
Comment=This session logs you into Ubuntu
Exec=gnome-session --session=ubuntu
TryExec=gnome-session
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-2.0


If not, then erase what is (if anything) in the file and retype the above quote. Save it with CTRL O + CTRL X. Then restart the computer with 'sudo shutdown -r now'.

Good luck!

---

### Post by Foobarz on 2011-07-26
Thank you all for your help, but it did not work, sadly. I decided to reinstall Ubuntu 11.04 and migrate any user files. In the future, I will be more careful in installing video drivers and stuff. Thank you all for the support, though.

---

