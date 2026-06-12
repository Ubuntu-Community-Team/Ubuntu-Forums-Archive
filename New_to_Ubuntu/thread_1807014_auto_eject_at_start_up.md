---
title: "auto eject at start up"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by klein de usa on 2011-07-18
hi 
i have a computer that the Internet connection is through an usb modem, when the computer is started and you login on the desktop there is an icon for the storage device or windows install files on the usb modem and the modem with not continue till that icon is ejected.

i can eject the icon by typing in a terminal sudo eject /media/Broadband2Go 

i would like to run this computer headless, so i need a way of auto ejecting /media/Broadband2Go  

is there a way to run a script being triggered from the system clock?

maybe put eject /media/Broadband2Go in one of the last files to be run before login screen?

my goal is to run this headless so when started i would stop at the login screen eject /media/Broadband2Gov and connect to the Internet

---

### Post by seawolf167 on 2011-07-18
You could unmount it with a script at login

Something like:

```
touch name.of.script
gedit name.of.script
```Write the script

```
#!/bin/bash
umount /media/Broadband2G || /bin/true
```Save, exit, then make it executable

```
sudo chmod +x name.of.script
```Then add it to System -> Preferences -> Sessions

---

### Post by klein de usa on 2011-07-18
the script isn't the problem, how to start the script is, when booting  headless,

i tried using cron command @reboot to start a script didn't work.

i tried using startup applications but it seems to only run after the 
  login screen.

this brings up another point exactly when when the usb is mounted ?

---

### Post by seawolf167 on 2011-07-19
You are correct, the startup applications/sessions will only run at login. 

To run at boot, you should add an rc.local script. There is a [how-to here ]("https://help.ubuntu.com/community/RcLocalHowto")(you already have the script made so just skip those steps).

As for only running when a USB is detected, I couldn't answer how to automatically detect a device and run a script, what I would do instead is add the script I added in the last post to a crontab which runs say every 5 minutes (or whatever you think is necessary). the "|| /bin/true" part of the script will return a "true" if there is no device to unmount (instead of erroring out).

---

### Post by klein de usa on 2011-07-19
thank you seawolf167

i thought of that but when i was looking at it, it looked to me that ubuntu was trying to get away from /etc/init.d and go to upstart.
 
i will try that and see if it works, put in some sleep commands and run the command a few times.

i have a networking question too but i will start a new thread for that.

---

