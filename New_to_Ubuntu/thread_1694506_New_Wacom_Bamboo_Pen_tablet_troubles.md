---
title: "New Wacom Bamboo Pen tablet troubles"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Tobey666 on 2011-02-24
Hey everyone.
I'm working on trying to get my new tablet to work on Maverick and I need some help.  I'm using the [Bamboo P&T HOWTO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") but I've run into a problem.  

In step one, the guide says that I need to enter the following into the command line

"./configure --enable-wacom --prefix=/usr"

However, when I do, I receive the following message:

"NOTE: the X driver in this package only supports Xorg servers older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.
The kernel driver provided in this package is independent of 
the X server version"

What I need is a little help interpreting the guide.  It appears to me like this issue is what the second step in the guide is addressing, but I'm not sure.  Is this something I have to resolve before continuing with the guide or is it going to work itself out as I progress?

---

### Post by Favux on 2011-02-24
Hi Tobey666,

You understand it correctly.  It's telling you you can't use the linuxwacom X driver.  But since you only want the usb driver wacom.ko that's fine.  In part II. you'll build the xf86-input-wacom X driver which does work for X servers 1.7 and higher.

---

### Post by Tobey666 on 2011-02-24
Thanks for your help.  It's working now.

---

