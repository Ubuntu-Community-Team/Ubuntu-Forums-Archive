---
title: "Thinkpad T22 - Graphics"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by Drummm on 2009-06-11
I Have Just Began Restoring an old IBM thinkpad t22 I Had Lying around. So Far Successful. I Used a Ubuntu 8.10 Live CD of the Website, Installed xUbuntu-desktop and Wiped the Original Gnome Session. I am Almost good to go. There is Just one Problem, The Graphics, Fonts Everything is so Pixel-y. 

Just Wanted to Know if there was a fix. I Have been looking for several Hours. It is really annoying me that Everything is like this.

---

### Post by LowSky on 2009-06-11
describe pixel-y

have you tried changing the resolution?

That will usually fix most issues.

---

### Post by Drummm on 2009-06-11
Have Just Fixed. And Pixely Was The Vesa Driver, Not each pixel was 3-4 times as big as it should have been. Anybody else who has this Problem, for future reference;

modify your xorg.conf under devices to match this: 
```


Section "Device"
Identifier "S3 Inc. 86C270-294 Savage/IX-MV"
Driver "savage"
BusID "PCI:1:0:0"
Option "BusType" "PCI"
Option "DmaMode" "None"
VideoRam 8192
EndSection
```

---

