---
title: "Screen  Resolution"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by cedarview on 2009-09-10
How do I get a screen resolution of greater than 800x600.

I have managed to get the login screen to show a decent resolution but when I enter the workspace I get put back to 800x600
:(

---

### Post by mapes12 on 2009-09-10
If you're running Hardy I had the very same problem. This assumes you have no none free hardware drivers to help you out. This is how I fixed it:

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

### Post by cedarview on 2009-09-10
I am running 9.04 does this make a difference
:confused:

---

### Post by mapes12 on 2009-09-10
> **cedarview said:**
> I am running 9.04 does this make a difference
:confused:Doesn't work with 9.04

---

