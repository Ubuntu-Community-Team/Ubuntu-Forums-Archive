---
title: "how to install fonts"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-12-04
hi,

i have a zip package full of ttf fonts. i want to install them in my ubuntu system. what should i do. where should i copy them?

thanks

---

### Post by cozmicharlie on 2008-12-04
From: 
[http://tombuntu.com/index.php/2008/04/17/how-to-install-fonts-in-ubuntu-804/](http://tombuntu.com/index.php/2008/04/17/how-to-install-fonts-in-ubuntu-804/)

Photonian2 said,  in September 15th, 2008 at 10:00 am

Here it is again, but better structured.

So, to install ttf fonts for system-wide use -
what you do is;

1. Press key combination Alt-F2
2. Type gksu nautilus
3. Type in your user Password
—1. If you get an error then STOP HERE and get someone who has administrative privileges
4. Change directory to /usr/share/fonts/truetype
5. Then copy and paste your ttf fonts to your hearts delight

If you don’t understand these instructions then you Certainly should NOT do this.
May I suggest getting help from a friend who can.

USE CAUTION: By using nautilus with root privileges you have the potential of destroying your system.

—————————————————

To install ttf fonts for your use only -
what you do is;

1. Press key combination Alt-F2
2. Type nautilus
3. Press key combination Ctrl-H
4. Look for .fonts
—1. If it’s there then open it.
—2. If it’s not then create it.
——1. By clicking on menu item “File”
——2. Then clicking on “Create Folder”
——3. Name it “.fonts”
——4. Then open your new .fonts directory
5. Then copy and paste your ttf fonts to your hearts delight

Have a Very Nice Day. :-)

---

