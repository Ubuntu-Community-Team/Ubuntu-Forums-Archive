---
title: "Does sudo reboot now in command line hurt anything?"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Space-Wolf on 2009-11-29
I understand that if the computer freezes and you do a hard shutdown by holding down the power button you can risk damaging system files.  So, if I get into the command line with ctrl+alt+f1 and then type sudo reboot now, is that a safe shutdown or is that a risk as well?

---

### Post by ubudog on 2009-11-29
No it won't damage anything.  But all you have type is ```
sudo reboot
``` and enter your password. (you wont see it for security reasons) Then press enter.

---

### Post by Space-Wolf on 2009-11-29
Sweet, thanks.  For the record though, how risky is a power button restart?  And also, a little off topic, but if I select a different desktop environment on startup, does it effect anything or it's purely for looks?

---

### Post by ubudog on 2009-11-29
> **Space-Wolf said:**
> Sweet, thanks.  For the record though, how risky is a power button restart?  And also, a little off topic, but if I select a different desktop environment on startup, does it effect anything or it's purely for looks?

I have been in the middle of a game and it crashed. I was on the 3/4 level and I had to do a power button restart and when I went to play the game, all my save data was gone so I had to restart the whole game.  Changing the desktop environment on startup does not effect anything. It is purely for looks.

---

### Post by ubudog on 2009-11-29
And also, using the power button to turn your computer off could damage the hard drive which would then require you to use the LiveCD and select restore mode at the beginning.

---

### Post by The Cog on 2009-11-29
A power-off can cause disk corruption. I think this is worse with ext4 most other filesystems such as ext3 or jfs. Avoid it if you can.

If you can Ctrl-Alt-F1 to a console then just restarting X will be quicker than a reboot - sudo /etc/init.d/gdm restart. 

You can also enable Ctrl-Alt-Backspace as a key to restart X - on Karmic it's System->Preferences->Keyboard, Layouts tab, Layout Options... and Key sequence to kill the X server.

---

### Post by Space-Wolf on 2009-11-29
Thank you all for the help and information.

---

### Post by ubudog on 2009-11-29
You are welcome. If you need any help, send me a private message.

---

