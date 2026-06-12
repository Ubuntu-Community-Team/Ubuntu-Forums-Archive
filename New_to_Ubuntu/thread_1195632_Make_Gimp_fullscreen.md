---
title: "Make Gimp fullscreen"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by balachandarlinks on 2009-06-24
Hi,
 I m frustrated with the windowed behaviour of gimp.I need to make it like photoshop.Combining all the windows in a single window.Is it possible.
                   thank you...cheers......

---

### Post by Hairy_Palms on 2009-06-24
could try the old Xnest hack

> 
sudo apt-get install xnest
Xnest :1 -ac -wr -name Gimp-2.6 -geometry 1440x822 & gimp --display=:1 & metacity --display=:1

replacing 1440x822 with the resolution u want gimp to be

make sure you go to Edit->Preferances->Window Management and set both window manager hints to utility window.

---

### Post by balachandarlinks on 2009-06-24
Hi,
   your tip makes gimp main window to occupy the whole screen and it doesnt attach the other windows (layers,tools) to the main window.Xnest makes gimp peculiar.What i really want is you may see with blender software.Fullscreen and windowed.
 Like that i need...

---

### Post by jimv on 2009-06-24
I spent a long time trying to figure out how to make the GIMP work like Photoshop (as far as the one window thing)...I discovered that it's simpler to just get used to how GIMP does it.  If it's really annoying, you could move all your gimp windows to their own desktop, which would be similar.

---

### Post by nandemonai on 2009-06-24
There is [http://www.gimpshop.com/](http://www.gimpshop.com/) but I don't think that's quite what you're after. I'm pretty sure it just replaces the menu items with familiar Photoshop terminology.

Your best bet is to just get used to how GIMP does things. As far as I know there is no way to consolidate the GIMP windows.

---

### Post by balachandarlinks on 2009-06-24
I think if the gimp team provides this facility then it ll be great boon to the gimp designers like me...

---

### Post by mcduck on 2009-06-24
> **balachandarlinks said:**
> I think if the gimp team provides this facility then it ll be great boon to the gimp designers like me...

They are not likely to ever provide that feature. Such interface design is often considered bad for usability, and actually even Photoshop uses multiple separate windows when run on OS X. The only reason for the MDI interface in Windows version is that Windows has pretty bad support for SDI interfaces.

---

### Post by Lablasco on 2009-06-24
If the option of GIMP all-in-one window existed, it would make my work easier. 
I would definitely use it.

---

### Post by jimv on 2009-06-24
Aside from being used to it in Photoshop, what does having it all in one Window really do for you?

---

### Post by balachandarlinks on 2009-06-25
If this single window feature is enabled then it ll attract more number of users from photoshop(XP) to gimp...

---

