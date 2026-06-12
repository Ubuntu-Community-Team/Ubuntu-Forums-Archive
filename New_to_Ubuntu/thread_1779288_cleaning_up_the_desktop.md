---
title: "cleaning up the desktop"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by Wray on 2011-06-10
How do i get rid of items on the desktop?
If they are also in the launch bar, i don't need them on the desktop. Right?

---

### Post by nomko on 2011-06-10
What items?
 
If you mean the shortcuts to your external drives, trash can, etc.:
 
Go to: 
Gconf-editor
 
Go to:
/apps/nautilus/desktop
 
uncheck:
volumes_visible
network_icon_visible
trash_icon_visible
computer_icon_visible
home_icon_visible
 
This will remove all the icons on your desktop.

---

### Post by Wray on 2011-06-10
Thanks nomko

The items i want to remove are shortcuts to usb devices and 
a DVD data disk

---

### Post by nomko on 2011-06-10
> **Wray said:**
> NOMOKO????????????
 
It's **NOMKO**, not NOMOKO..... ](*,)
 
Anyway, you're welcome! I'm glad that i could help you!

---

### Post by grahammechanical on 2011-06-10
If you are using Ubuntu Classic as your User Interface then you do not have this issue. Those of us who are using Unity as our UI do have this issue because Unity has not yet completely replaced the Gnome user interface. So, when you plug in a USB stick Unity will put an icon in the launcher and Gnome will put an icon on the desktop.

Think of this: what happens when the launcher is filled with your chosen applications and you insert a USB stick and there is not any room for the icon to appear on the launcher or some of the other icons disappear from view? May be then we will want the icon of a removable device to appear on the desktop.

Regards.

---

### Post by Wray on 2011-06-10
Yeah, i caught that and edited the reply..apologies

---

### Post by nomko on 2011-06-10
> **Wray said:**
> Yeah, i caught that and edited the reply..apologies
 
Accepted ;)
 
I know my name is strange. Even in The Netherlands many people do have problems with it. I'm from the northern part (countryside) of Holland ( a province called Groningen) and live for 14 years in The Hague (southern part of Holland). How many times i've been called foreigner due to my apparently strange combination of first and last name.

---

### Post by Wray on 2011-06-10
Some more information on the icons on the desktop that i wanted to remove.
It turns out that the are not shortcuts at all!
They appear when media is inserted, including DVD or USB devices, and cannot be deleted.
They dissapear when the media is removed...so, maybe i don't want to remove them after all.
This is why i am posting on the Noob forum!

---

### Post by el_koraco on 2011-06-10
> **Wray said:**
> Some more information on the icons on the desktop that i wanted to remove.
It turns out that the are not shortcuts at all!
They appear when media is inserted, including DVD or USB devices, and cannot be deleted.
They dissapear when the media is removed...so, maybe i don't want to remove them after all.
This is why i am posting on the Noob forum!

When you insert a DVD or USB, it is "mounted" (made ready to use) on the desktop, so you can have an easier time ejecting the DVD or unmounting (safely removing) the USB, or accesing the files on the devices.

---

### Post by nomko on 2011-06-10
> **Wray said:**
> Some more information on the icons on the desktop that i wanted to remove.
It turns out that the are not shortcuts at all!
They appear when media is inserted, including DVD or USB devices, and cannot be deleted.
They disappear when the media is removed...so, maybe i don't want to remove them after all.
This is why i am posting on the Noob forum!

First, yes, they are shortcuts to your external devices.
Yes, they appear each time you connect an exernal device such as external disc's, usb sticks, digital camera, video-camera, etc.
Yes, they disappear every time when you disconnect an external device.

It's no real handy to keep them on your desktop since it might give you the impression that one of your external devices might be connected.

If you have an external disc which is always connected to your pc, then that icon will be visible at all times. Unless you unchecked the option volume_visible in Gconf-editor, then even that won't appear on the desktop. But even so, it doesn't matter that those options are unchecked. Every device which is connected to your computer will be visible in: a)Nautilus and b)under Locations.

Those shortcuts on your desktop are handy for quick access to your devices and unmount them by right clicking on them and select safe removal or unmount (i'm not quit sure because i'm using Ubuntu with the Dutch language).

---

### Post by collisionystm on 2011-06-10
> **Wray said:**
> Thanks nomko

The items i want to remove are shortcuts to usb devices and 
a DVD data disk


The problem is, once you take away things like CD's showing up on your desktop, it removes the ease of access you had for copying them. 

With the icon, you can just right click and hit COPY DISK to make an .iso

Its not so easy without the icons.

---

### Post by wpurcell on 2011-11-06
Thanks nomko!

---

