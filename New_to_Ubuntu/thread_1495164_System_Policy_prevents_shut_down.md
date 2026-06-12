---
title: "System Policy prevents shut down ???"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by 007casper on 2010-05-27
I get this message occasionally when I tried to shutdown the system.  What does it really mean?
> 
System policy prevents stopping the system when other users are logged in

An application is attempting to perform an action that requires privileges, Authentication as one of the users below is required to perform this action.

administrator 'name of the main user'
password 'asking to enter'

Details>
/usr/bin/gnome-session
action: org.freedesktop.consolekit.system.stop-multiple-users

There isn't anyone else logged in as far as I know.  Does that mean someone is logged in to my computer? Or just an application is looking for privileges?

Please, advise.  Thank you.

---

### Post by pzkfw on 2010-05-27
Gnome has code to shut down as a user since Ubuntu is a Desktop distro.

I'd recommend apt-getting remove and install gnome, but if you can't shutdown just remember this command:

```
#sudo shutdown -h now 
```

replace -h with -r to restart.

Enter this command in xterm or gnome terminal.  You have to be root or use sudo.

---

### Post by 007casper on 2010-05-27
Thank you so much.  Yeah, I just shutdown through terminal when that happens occasionally.

---

### Post by zagaboy on 2010-09-13
I had a similar problem when I installed MythTV! There was a process running "mythTV backend" or something like that. In the "System Monitor" I saw it listed, and the user was "MythTV". I uninstalled it from Ubuntu Software center but that didn't work so eventually I had to sudo apt-get remove mythtv and then autoremove.

---

