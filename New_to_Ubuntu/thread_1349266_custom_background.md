---
title: "custom background"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by dzon65 on 2009-12-08
I changed my xsplash and gdm.How can I add custom backgrounds to that background folder?(usr/share/backgrounds)
Oh yes,someone warned me for that,don't know why.

---

### Post by Temposs on 2009-12-08
Basically what you should do is make a folder called Backgrounds or something in your home folder. Then put your new background images in there. Whenever you want to add a new background, put it in that folder, then open System->Appearance->Background, and click Add. Find the image you want to add, and then it should be included in the list of backgrounds you can choose from at any time in the future.

---

### Post by dzon65 on 2009-12-08
No,I mean the folder where the default backgrounds are stored.It needs a sudo command.

---

### Post by Temposs on 2009-12-08
Don't bother adding stuff to there. That folder is only meant to hold the backgrounds that come preinstalled with Ubuntu. Use the method that I recommended above.

---

### Post by dzon65 on 2009-12-08
So something like this,changing backgrounds to the new file name of course
sudo cp /usr/share/backgrounds/TheRainbowisDead.jpg /usr/share/images/xsplash/bg_2560x1600.jpg

---

### Post by Temposs on 2009-12-08
oh you mean you want to take background images and put them into the xsplash folder?

Yeah, something like that command should work.

---

### Post by dzon65 on 2009-12-08
This works for xsplash.But for changing gdm background I'll have to be able to add a picture to usr/share/backgrounds.The options for changing gdm are limited to the default folder.
When you do this:a set up window will pop up
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

---

### Post by dzon65 on 2009-12-08
Check it out:[http://ubuntuforums.org/showthread.php?t=1333683](http://ubuntuforums.org/showthread.php?t=1333683)

---

### Post by dzon65 on 2009-12-08
Should be something like sudo Nautilus,but that's a command that isn't recognized.

---

### Post by dzon65 on 2009-12-08
Ok,I managed to get files in there.Thanks for the replies.

---

