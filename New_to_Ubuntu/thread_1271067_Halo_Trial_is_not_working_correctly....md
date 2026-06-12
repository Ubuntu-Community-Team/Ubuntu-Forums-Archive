---
title: "Halo Trial is not working correctly..."
date: 2009-09-20
forum: New to Ubuntu
---

### Post by Bigbob22 on 2009-09-20
I installed the Halo Combat evolved trial on my computer using wine. After I installed it I used ```
env WINEPREFIX="/home/bigbob/.wine" wine "C:\Program Files\Microsoft Games\Halo Trial\halo.exe" -novideo

``` to run the game but it came with an error message```
Cannot find Z:/home/bigbob/.wine
``` This is what showed in the terminal: ```
fixme:win:EnumDisplayDevicesW ((null),0,0x32d394,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3823
fixme:win:EnumDisplayDevicesW ((null),0,0x32cf0c,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found

``` I was able to run the game by running the .exe in the drive_c, but it won't let me have any keyboard input (when creating profile). How do I fix this?

---

### Post by Bigbob22 on 2009-09-20
Please help...

---

### Post by Bigbob22 on 2009-09-20
I got this ```
env WINEPREFIX="/home/bigbob/.wine" wine "C:\Program Files\Microsoft Games\Halo Trial\halo.exe" -novideo
```
to work but I'm still having trouble with the keyboard input.

---

### Post by ashwinhgtx on 2009-09-20
I think you should try the official wine forums for this. They are the experts.

---

### Post by callumacrae on 2009-09-20
It should be working:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6978](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6978)

But yeah, post in the Wine forums.

~Callum

---

### Post by Bigbob22 on 2009-09-20
Okay i posted a thread on the wine forums. Thanks.
Here is the the thread for any one who might need it:
[http://forum.winehq.org/viewtopic.php?p=31995#31995]("http://forum.winehq.org/viewtopic.php?p=31995#31995")

---

