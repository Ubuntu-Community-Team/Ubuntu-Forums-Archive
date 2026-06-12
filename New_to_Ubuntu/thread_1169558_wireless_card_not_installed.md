---
title: "wireless card not installed?"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by powerade411 on 2009-05-25
having issue with wireless card i typed in the command to see if it recognizes my wireless card and it says not installed what do i do?

---

### Post by tom56 on 2009-05-25
What is the make and model of the wireless card?
What command did you type in?
What was the output?

I may not be able to help you, but neither will any one else until you make your first post less vague :)

---

### Post by albinootje on 2009-05-25
> **powerade411 said:**
> having issue with wireless card i typed in the command to see if it recognizes my wireless card and it says not installed what do i do?

Post the output of the following :
```

lspci
lsusb
lshw -C network

```

---

### Post by powerade411 on 2009-05-26
Dell Wireless 1450 Dual Band WLAN

---

### Post by anewguy on 2009-05-26
Try checking this link:

[http://ohioloco.ubuntuforums.org/showthread.php?t=908090]("http://ohioloco.ubuntuforums.org/showthread.php?t=908090")


Dave :)

---

### Post by superprash2003 on 2009-05-26
do post the outputs of commands mentioned in post 3

---

### Post by carml on 2009-05-26
I made a search on Google and maybe you need Ndiswrapper to use your wireless card on Ubuntu.You need to look for Windows drivers for your wireless lan,download them onto your desktop and unzip them.
Then open a terminal (it's quicker and indipendent from Gnome,Kde etc) and type without quotes "sudo apt-get install ndiswrapper-common ndisgtk ndiswrapper-utils-1.9,then once you installed all the three packages type in the terminal "sudo ndisgtk" and in the windows left-click on "Install Driver",point to the directory where you unzipped the drivers,then reboot and you've all done.
Just let us know if you need some more explanations. :)

---

### Post by powerade411 on 2009-05-27
Thanks guys i think i have it figured out

---

### Post by NHArticleTen on 2009-05-27
> **powerade411 said:**
> Thanks guys i think i have it figured out

If your solution works out please post it here and also mark the thread as solved...

---

