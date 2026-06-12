---
title: "large fonts"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by tim1970 on 2010-02-08
I did a clean install of xubuntu 9.10 on my compaq laptop.  Resolution seems ok (1280 X 1024), but the fonts on some applications are huge.  For instance when I tried to get conky running on this machine, I had to set the font size to .5 and .75 to get it to fit on the screen.  Also, I installed open office, and the size of the font on the menu seems very large.  Anybody have any ideas on what could be causing this?

Thanks

Tim

---

### Post by tim1970 on 2010-02-08
I was able to solve the problems of large fonts by using the following from a post I found here..

Xubuntu 9.10
Sice most applications show OK you just need to:
Open the Leafpad text editor. 
Type in it: Xft.dpi:90 
go to File -> Save as, and enter as the filename .Xresources 
Press Alt+SysReq+k to restart the X-server. (the SysReq might be seen as print screen on your keyboard) 
Enjoy. 


However, after doing this conky stopped working.  In order to make it work I had to change the use_xft from yes to no.  What would cause this?


Thanks

Tim

---

