---
title: "g120 dlink driver and ndisgtk??"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by sleeve_less on 2008-03-02
hello,  

i just need a  little assistance. I have used linux and unix, and so have decided to use one of my older pc's-- fast enough on the hardwear and plenty of ram (512 mb), and use it as a linux server on my wireless network at home. 

I have a wireless adapter dllink g120, and the windows xp drivers. I have those on my ubuntu desktop/server...all ok, except the Only .inf file i can find (to use with ndiswraper) has just two lines in it 
they are: 
open= Autorun.exe
ICON=autorun.exe, 0

Q-- is THAT file (lines 1 & 2 listed above) the one I point to when using 
ndisgtk?  I thought it would be a whole driver, and not 2 little lines like that. 

Q- how do I use ndisgtk? I have the tar file loaded, and I double click on it, a window opens up to either extract the files or open them! Please, someone help me with using ndiskgtk

thanks in advance

squirt

---

### Post by abyssius on 2008-03-02
sleeve_less, the file you downloaded requires you to do a manual installation. I think you'd be better off downloading the .deb file. This way, it will be installed automatically when you double-click on it. Assuming, you're using the latest Ubuntu distribution, You can find ndiswrapper here:

[http://packages.ubuntu.com/gutsy/ndiswrapper-utils-1.9]("http://packages.ubuntu.com/gutsy/ndiswrapper-utils-1.9")

---

### Post by sleeve_less on 2008-03-02
:KSabyss, 

 hey ... thanks. Good info. I will try it tomorrow evening. no time now or in the day tomorrow. 

Has anyone heard of madwifi? Another post in this forum was directing someone to madwifi 
THanks, all.

NOTE-- I also have two other wireless adapters (usb)...one has a ralink 7 driver and the other device has wave cast as the part name--tho I can't find the driver 
*.inf file in either one. Any ideas?
 
 
sleeve_less 
aka,...squirt

---

### Post by abyssius on 2008-03-03
madwifi doesn't support USB wireless adapters.

---

