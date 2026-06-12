---
title: "blank screen"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by skypuppy on 2011-01-23
Ok, I have Ubuntu 10.10 booting from the hard drive and at least coming to the initial login screen.  Once I enter the pwd, the screen goes blank and never comes back unless I push the power down button (which then shows a skewed blob screen and shuts down.)

This system worked fine for a couple days until I loaded a lot of kde packages.  Now the above results happen.

Any ideas on how to get the system back to normal?

Thanks.

---

### Post by bioterror on 2011-01-24
log into a TTY (press ctrl+alt+f1) when you're at login screen.
You should end up to a cli (command line interface) and login with your user credentials.

then perform a command 
```
sudo apt-get purge kde\*
```

And I would assume you have network connection, you should after removing those kde packages try command
```
sudo apt-get install ubuntu-desktop
```
to confirm that you're having all the needed Ubuntu packages.

ps. if you dont have a internet connection, please use wired network and use command
```
sudo dhclient eth0
```

after that you can reboot your computer with command
```
sudo reboot
```

Hope this helps, if not, I bet we'll hear from you more ;)

---

