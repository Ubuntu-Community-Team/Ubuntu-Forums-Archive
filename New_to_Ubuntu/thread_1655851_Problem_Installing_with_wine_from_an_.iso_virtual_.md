---
title: "Problem Installing with wine from an .iso virtual drive"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by Muzzab on 2010-12-30
Hi,
This is my first post as it's the first problem I've ever encountered with Ubuntu so far, so bear with me thanks!
I'm running Ubuntu 10.04 netbook remix and I'm trying to install Propellerheads Reason 5 with wine. I have mounted the .iso file into a virtual drive and opened it with wine. However, when I select the directory containing the installation files it gives an error: 
"The file "install_reason-1.bin" could not be located in "H:\virtual\Reason 5". Please insert the correct disk or select another folder.

I don't understand because this very file is in the directory selected. I have tried altering settings in winecfg and still no luck. Maybe I'm missing something really simple but I'm a bit stumped. As you probably know, Reason is an expensive program and I really need to get it up and running on Ubuntu because the thought of going back to windows is a scary one! Can someone help me out?

Thanks!
M.

---

### Post by blind2314 on 2010-12-30
Have you tried running as root? (I've had some weird wine problems before..bear with me if you've already done that)
 
Also, since you own the software (I'm assuming..), have you tried the physical CD?

---

### Post by Muzzab on 2010-12-30
I am trying to install it on my netbook which has no dvd drive. What do you mean by run as root? 
I have done more investigating. The error box is looking for the file 
"install_reason-1.bin" but in the virtual drive directory it is actually named
"install_reason_1.bin"
I'm assuming that this slight difference in the file name is the problem? How could that happen? What can I do about that?
Thanks!

---

