---
title: "Help"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by RaidersJH34 on 2010-06-25
My mouse freezes un-expectedly and the only way to fix it is if i restart ubuntu. help...

---

### Post by wieman01 on 2010-06-25
Could it be the USD power supply? What happens when you pull the plug and put it in again?

---

### Post by RaidersJH34 on 2010-06-25
it is still frozen. i even pressed F12 when restarting the computer turned of the connection to the usb port and turned it back on. i even tryed differnt ports with different mouses. still no luck.

---

### Post by cj.surrusco on 2010-06-28
This command will reload the usb module. 
```
sudo modprobe -r usbhid ; sudo modprobe usbhid
```
I would add that command to a keyboard shortcut so that if you mouse freezes, you can reload it.

Go to **system>preferences>keyboard shortcuts**
 
Create a new shortcut and add the command above. Then choose a set of keys to trigger the command(something like ctl+alt+m).

Next time your mouse freezes, use that keyboard shortcut and it should reload.

Use this link when you get confused about the keyboard shortcuts, because I know you will, Jeff.

[http://www.techotopia.com/index.php/Ubuntu_Desktop_Keyboard_Shortcuts]("http://www.techotopia.com/index.php/Ubuntu_Desktop_Keyboard_Shortcuts")

You're welcome, buddy.

---

