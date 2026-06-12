---
title: "Stupid graphic card problem"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by mariuszp on 2009-11-05
I've had that problem with Ubuntu 7.10 and 8.10. When I moved a window, or minimized it, or most things with graphics, really, the window or object left signs, and sometimes it even turned white or black!!!!!!! And sometimes, the whole thing just freezes - everything stops, and only the mouse is moving. I did not have this problem with Ubuntu 9.04, but when I updated to Ubuntu 9.10, I have this again!

P.S. The box I am typing this message in is floating around the browser window. I've got problems with scrolling the webpages as well!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Help me! What do I need to do? Reconfigure the X-server? Even if, how do I do it???

---

### Post by wrgb2 on 2009-11-05
Choose Recovery Mode from grub on starup and scroll down the list to xfix and run it.

---

### Post by mariuszp on 2009-11-06
There was no xfix. Please note: this is Ubuntu 9.10. There was just a thing called "dpgk" that says "fix packages" (or something) and it recommended me to uninstall 2 obsolette packages. I did this. I still have the same problem!!!

Edit: I tried reconfiguring the xserver-xorg according to an article on Ubuntu documentation, it suggested the following command:

```

sudo dpkg-reconfigure xserver-xorg

```

I displayed nothing. It also gave no effect.

---

