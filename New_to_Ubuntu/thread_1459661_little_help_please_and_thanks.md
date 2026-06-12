---
title: "little help please and thanks"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by jagx1 on 2010-04-21
sorry for the noob  question, but i have a display problem. when i first start up the settings are 1152x 768 or something of the sort. the screen flickers bad and the left edge of the screen shadows on the right sideand there are black lines down the left third of the screen. changed the resolution to 1024 and got rid of the flicker and shadow. but still have the lines.

 also where can i go to find out my video card( this computer is old and was given to me, thats why i installed a new operating system) don't know anything about this one. any help would be appreciated

---

### Post by Rex Bouwense on 2010-04-21
Go to the terminal and enter lshw  That will tell you what you got.  Locate your video card and there you are.  It will warn you that you should be using that command as super user, but it will give you the desired information.

---

### Post by undecim on 2010-04-21
To see your video card model, open a terminal and type "lspci | grep VGA" 

Also, check System -> Administration -> Hardware Drivers and see if you have a driver ther for your video card.

---

### Post by jagx1 on 2010-04-21
took a look in the driver section and there was nothing. i also tried to lower the resolution further and it just made the black lines longer.

---

### Post by jagx1 on 2010-04-21
and something else i have tried is the xorg.conf in terminal. took a look at that, once. did some more reading about changes that i could make, color depth or something. gave it a gander since i haven't messed with it before. haven't made any changes.

---

