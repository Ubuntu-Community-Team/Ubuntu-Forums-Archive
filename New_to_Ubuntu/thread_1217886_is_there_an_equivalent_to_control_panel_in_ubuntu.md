---
title: "is there an equivalent to control panel in ubuntu?"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by kapi on 2009-07-20
wanted to see what info there was available concerning my system in ubuntu. Used to use control panel in windows and can't seem to see anything similar in Ubuntu.

---

### Post by lisati on 2009-07-20
Kind-of, but some of the items are in different places and/or have different names. Check the "System->Preferences" and the "System->Administration" menus. "For Add/Remove programs", look at Applications->Add/Remove.

---

### Post by 4Orbs on 2009-07-20
You might look at Gnome Control Center in the Synaptic Pkg Mgr. But I think everything it shows is already listed in the System and Preferences menus.

---

### Post by mhh91 on 2009-07-20
and if you're looking for info about your processor and other hardware,you'll find it in "System monitor",you'll find it under System>Administration

---

### Post by Cheesemill on 2009-07-20
Go to System > Preferences > Main Menu to open up the menu editor.

Click on System on the left hand side and then click on the 'Control Centre' box to add the control centre to your menu.

---

### Post by powel212 on 2009-07-20
The simple answer to your question is Yes.

in a terminal run

```
gnome-control-center
```

I am sure that will help.

Powel

---

### Post by mthalis on 2009-07-20
I think **ubuntu-tweak** is best . you can also try **sysinfo**.

---

### Post by powel212 on 2009-07-20
+1 Ubuntu Tweak

[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

P.

---

### Post by 3rdalbum on 2009-07-20
> **kapi said:**
> wanted to see what info there was available concerning my system in ubuntu. Used to use control panel in windows and can't seem to see anything similar in Ubuntu.

What information exactly do you want?

For a list of what's in your system, the "lshw" command works well. It's very verbose; if you want a graphical list, there's "gnome-device-manager".

If you specifically want a list of what's in your USB ports, then:

```
lsusb -v
```

Lots of information. For PCI devices and what's on your motherboard:

```
lspci
```

For CPU information:

```
cat /proc/cpuinfo
```

For current system resource statistics (very useful!), System > Administration > System Monitor.

---

### Post by kapi on 2009-07-20
Just want to say a huge thanks to you all for the comments  and help you've provided.

I loaded control center, I am looking for details on the motherboard so I can upgrade the ram, hopefully one of the suggestions will help.

Thanks again

---

### Post by kapi on 2009-07-20
Just loaded Ubuntu Tweak and it is fantastic!- Whoa ho!!!

They should make this part of the installation suite that is automatically first installed on the OS.

Love it

---

### Post by CaptainMark on 2009-07-20
Ironic that ubuntu has no control panel, when compared to ubuntu you have very little 'control' over windows.

---

