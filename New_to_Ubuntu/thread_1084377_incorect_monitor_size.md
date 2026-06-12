---
title: "incorect monitor size"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by chirucam on 2009-03-02
hello friends, ijust installed ubuntu 8.04 on my desktop in dual boot sustem.. my monitor(samtron 45Bn) which absolutely looks fine in xp, is getting cut from right side a little and there is a black band kind of a thing on the right side..Screen resolution shows 1280 * 768 and the refresh rate is 60Hz, though in india ishould be 50Hz..  Could someone please help? thanks..

---

### Post by hyperyoda on 2009-03-02
> **chirucam said:**
> hello friends, ijust installed ubuntu 8.04 on my desktop in dual boot sustem.. my monitor(samtron 45Bn) which absolutely looks fine in xp, is getting cut from right side a little and there is a black band kind of a thing on the right side..Screen resolution shows 1280 * 768 and the refresh rate is 60Hz, though in india ishould be 50Hz..  Could someone please help? thanks..

Hello friend,

First verify your settings by doing this:

$  xdpyinfo | grep -B1 dot

It will show your dimensions and resolution (dpi) such as:

  dimensions:    1024x768 pixels (347x260 millimeters)
  resolution:    75x75 dots per inch

You must edit your /etc/X11/xorg.conf and enter the correct refresh rate and dimensions. Enter the DisplaySize in the Monitor section.

This thread will explain how to calculate it:

[http://bbs.archlinux.org/viewtopic.php?id=39665]("http://bbs.archlinux.org/viewtopic.php?id=39665")

Zach

---

