---
title: "resolution"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by theRightNee on 2009-09-10
hey all,
been out of the loop for a while (was experimenting with OSX) and i cannot seem to get my resolution to go higher than 1024x768. my monitor supports up to 1440x900, but the autodetection does not seem to be working. is there a way to modify this? thanks!

---

### Post by staf0048 on 2009-09-10
Have you tried enabling the hardware drivers?

---

### Post by mapes12 on 2009-09-10
On Hardy I had the very same problem. This assumes you have no none free hardware drivers to help you out. This is how I fixed it:

First of all, you need to download some packages. Go to the following 2 links. At the bottom of each page is a link to allow the package to be downloaded. Make sure that, for guidance-backends you select the correct architecture for your computer. For displayconfig-gtk there is only one possible download for all architectures. You will have to select a mirror near to you before each download will begin.

[http://packages.ubuntu.com/hardy/adm...playconfig-gtk](http://packages.ubuntu.com/hardy/adm...playconfig-gtk)

[http://packages.ubuntu.com/hardy/guidance-backends](http://packages.ubuntu.com/hardy/guidance-backends)

Once downloaded, click on the guidance-backends first, and you should be presented with the option 'Open with GDebi' or something similar. This program installs the package on your system. It will ask for your password.

Do the same for the displayconfig-gtk package.

Once they are both successfully installed (< 30 seconds ) open a terminal and type:

```
gksu displayconfig-gtk
```

A GUI will come up. It will let you install your screen from manufacturers' data, or you can simply select a Generic display that has the correct resolution for your screen. For LCD monitors a screen refresh rate of 60Mhz is a safe bet.

---

### Post by Ampi on 2009-09-10
displayconfig did it for me too. Just add the right configuration :)

---

