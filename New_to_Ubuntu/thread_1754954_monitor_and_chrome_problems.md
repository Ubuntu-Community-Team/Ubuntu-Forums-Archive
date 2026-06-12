---
title: "monitor and chrome problems"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by farbeyondgone on 2011-05-10
hi i am very new too ubuntu and need some help
my acer za3 netbook had only windows xp home on but because of recnt frequent freezing i installed ubuntu 11.04 
after installing all is great but i cant seem to figure out why my resolution is stuck on 1024x768 at 61 hrz and says monitor unknown it wont detect it either i am an extreme beginner but understand how the terminal works for the most part any help would be greatly appreciated

in addition after trying to edit my xorg.conf file i had to reinstall ubuntu and in the process my chrome is now giving me the error
"The profile appears to be in use by process 1295 on host beast.  If you are sure no other processes are using this profile, delete the file /home/nastyweim/.config/google-chrome/SingletonLock and relaunch Google Chrome." i cant find this file or even the .config file 
plz help if you can

---

### Post by cavh on 2011-05-10
Check your laptop documentation online, it may be that 1024x768 is the maximum resolution for this hardware. Don't worry that it says monitor unknown, this isn't Windows - as long as you have the resolution you want, that's all there is to it.

To delete the Chrome file you refer to, close Chrome and type this into a terminal window:

```
sudo rm /home/nastyweim/.config/google-chrome/SingletonLock
```

you will need to enter your password after this command, as it is running as superuser - see [http://ubuntu-manual.org/]("http://ubuntu-manual.org/") for more.

---

### Post by farbeyondgone on 2011-05-10
my native is 1366x768 and everything on my screen is smushed and i have tried multiple fixes i have found on these and other forums and none will make it work
and after typing that line in terminal for chrome i got

nastyweim@Beast:~$ sudo rm /home/nastyweim/.config/google-chrome/singltonlock
[sudo] password for nastyweim: 
rm: cannot remove `/home/nastyweim/.config/google-chrome/singltonlock': No such file or directory
nastyweim@Beast:
 sorry am i doing something wrong??

---

### Post by farbeyondgone on 2011-05-11
so i was able to get my resolution to work its now at 1366x 788 but i still cant change the refresh rate and still cant find that file in chrome

---

### Post by cavh on 2011-05-11
Click System, Administration, Hardware Drivers and see if any new drivers are found.

Also check the Chrome command you typed - Linux is case sensitive. 'SingletonLock' is not the same as 'singletonlock'. And you have missed the 'e' in Singleton.

---

### Post by farbeyondgone on 2011-05-11
i feel like an idiot but now chrome is working but still no resolution there is nothing in my additional drivers so ive looked all over and cant figure out

---

### Post by cavh on 2011-05-12
In a terminal, type this to upgrade the packages on your system

```
sudo apt-get update && apt-get upgrade
```

and then do the 'Click System, Administration, Hardware Drivers and see if any new drivers are found' step again.

PS if this doesn't work, have a look at this thread, which may be relevant: [http://ubuntuforums.org/showthread.php?t=1744648]("http://ubuntuforums.org/showthread.php?t=1744648")

---

