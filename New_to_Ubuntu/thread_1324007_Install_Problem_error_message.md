---
title: "Install Problem error message"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by aierlan on 2009-11-12
Hi, I upgraded to 9.10 a couple of days ago.  
I was recording on ardour last night when i got a message saying i didnt have enough space on my hard drive.  I began moving some stuff onto my external hard-drive and the computer suddenly crashed.  
Now I cant get past the log in screen.  When I get to the log in screen I get an error message in the top right hand corner of my screen which reads:
Install Problem
The configuration defaults for GNOME power manager have not been installed correctly.  Please contact your system administrator.
The message appears and then disappears. I can enter in my password, the computer attempts to load up and then goes right back to the log-in screen with the same message. 
Please Help!

---

### Post by dvlchd3 on 2009-11-12
Can you login on a tty?

At the login screen, press Ctrl+Alt+F2.  Enter your username and password.  Are you able to login, do you have any error messages that appear there?

---

### Post by ukripper on 2009-11-12
Try login in tty as above poster suggested.

Put your user name and password there and to resolve the problem of gnome power manager do following:
```
sudo rm -f /var/lib/gconf/defaults/*
```
```
sudo gconf-schemas --register $(ls /usr/share/gconf/schemas)
```
for more info look at this thread:[http://ubuntuforums.org/showthread.php?t=785012](http://ubuntuforums.org/showthread.php?t=785012)


and then
```
sudo reboot now
```

---

