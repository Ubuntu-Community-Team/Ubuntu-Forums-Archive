---
title: "dlink wua-1340 setup/install"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by eeeumpc on 2008-07-24
trying to install this usb card after fresh install of ubustudio 8.04.1 from alternate install dvd(btw:during the install the usb hardware was attached and the installer said no network hardware was present)(thinking this is only because the are not any supported drivers on the dvd image). ivelooked around for days on what to do...heres what ive done so far. sorry for long post.

installed ndiswrapper/ndisgtk from hardy 8.04 cd since it was not on the ubustudio dvd image.

put the Dr71WU.inf + the Dr71WU.sys in home/user/

in terminal i did: ndiswrapper -i /home/user/Dr71WU.inf
        then       ndiswrapper -l 
        (says: dr71wu driver installed)
        then       ndiswrapper -a 07d1:3b11 dr71wu
        (says: Warning driver dr71wu will be used for 07d1:3b11 this is safe only if driver dr71wu is meant for chip in device 07d1:3b11)

         ndisgtk says driver installed hardware present yes:

now what???
Please help! :confused:

---

### Post by eeeumpc on 2008-07-24
iwlist shows nothing
iwconfig says: lo           no wireless extensions

---

