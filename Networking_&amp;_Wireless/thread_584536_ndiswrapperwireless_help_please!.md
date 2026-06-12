---
title: "ndiswrapper/wireless help please!"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by ut40755 on 2007-10-21
im trying to work with ndiswrapper to get my usb wireless device to work. i have it installed fine, and when i try to install the .inf file it says its already installed, but when i do -L, it says its invalid. i have no idea what i am doing as i have no experience linux. so please help. thanks.  if it helps, its a 2wire.

---

### Post by kevdog on 2007-10-21
Do a 
sudo rm -R /etc/ndiswrapper/*

Then try reinstalling
sudo ndiswrapper ***.inf

Dont install the same driver twice since you will run into the problem you have.

---

### Post by ut40755 on 2007-10-21
iv tried that a bunch of times, clearing out the ndis folder, reinstalling everything on the 2wire disc, then only certain things.  and whenever something is invalid, i remove it.

---

### Post by kevdog on 2007-10-21
If you have cleared out the /etc/ndiswrapper folder like you said, then you should not be receiving the messages that the driver is already installed.  Are you using the winxp driver (.inf and .sys files??)

---

### Post by ut40755 on 2007-10-21
yes, there was quite a few .infs on the cd, but i found out in windows which .sys it uses, so i just used the coordinating .inf, and copied the .sys file as well.  what happens is i do sudo ndiswrapper -i xxxx.inf, and it creates an empty folder with xxxx as the title, and then tells me its already installed.

---

### Post by kevdog on 2007-10-21
When you give the ndiswrapper -i command, the sys and inf file must be in the same directory.   Within the subdirectoy you speak about you should have a few files.  Here is mine just for example (after installing via the ndiswrapper- i command line statement):

kevin@Homer:/etc/ndiswrapper/lsbcmnds$ dir
14E4:4301:4301:1737.5.conf  14E4:4320:0417:14E4.5.conf  14E4:4320.5.conf  lsbcmnds.inf
14E4:4301.5.conf            14E4:4320:4320:1737.5.conf  bcmwl5.sys

---

### Post by ut40755 on 2007-10-21
so basically first put the files in a dir within ndis, and then install the whole directory?

if thats what ur saying, i already tried that.  i copied over the whole cd rom and installed the whole directory, when i did -L, it showed every file as an invalid driver

---

