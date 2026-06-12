---
title: "Unity Dash not recognizing applications"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by brandones on 2011-06-16
After I install programs, whether in the Software Center or the terminal, very few of them show up in the Dash. They're definitely there in /usr/bin, but if there's any way I can avoid hunting down the majority of my programs there, I'd love to hear about it. Hasn't anyone written an application to auto-update the Dash catalog with programs from /usr/bin?

---

### Post by compmodder26 on 2011-06-16
I'm pretty sure that in order for an installed program to show up in the dash it must have installed a .desktop file.  Not all programs do this.

Not to mention that not every program in /usr/bin is a graphical program either.  Some are meant purely to be run from the command line or invoked by another program.

---

### Post by brandones on 2011-06-16
Any way to make a .desktop file? Or better, a program to do it for me, given a file?

---

### Post by cbowman57 on 2011-06-16
> **brandones said:**
> Any way to make a .desktop file? Or better, a program to do it for me, given a file?

Nautilus has scripts for creating a launcher.  I've found the easiest method for managing them is with ubuntu tweak.

---

### Post by compmodder26 on 2011-06-16
Eh, I may be wrong here on how the Dash determines to show/not show a program.  Looks like it is based purely on the gnome menu options:

[http://ubuntuforums.org/showpost.php?p=10781254&postcount=2](http://ubuntuforums.org/showpost.php?p=10781254&postcount=2)

I was mistaken about the .desktop files.  Those are necessary for adding to the launcher bar.

---

### Post by cbowman57 on 2011-06-16
> **compmodder26 said:**
> Eh, I may be wrong here on how the Dash determines to show/not show a program.  Looks like it is based purely on the gnome menu options:

[http://ubuntuforums.org/showpost.php?p=10781254&postcount=2](http://ubuntuforums.org/showpost.php?p=10781254&postcount=2)

I was mistaken about the .desktop files.  Those are necessary for adding to the launcher bar.

In that case they could probably be added by using alacarte and editing the menu directly?

---

### Post by compmodder26 on 2011-06-16
> **cbowman57 said:**
> In that case they could probably be added by using alacarte and editing the menu directly?

Yeah that's what the link suggests.

---

### Post by brandones on 2011-06-16
Yeah, I know how to create launchers, but is it possible to integrate them into the Dash? I also didn't find, in my somewhat cursory click-through, anything in Ubuntu Tweak that seemed very helpful in launcher or Dash management.

EDIT 1: Alacarte looks wonderful, I'll give that a shot.

EDIT 2: Update: Added entries for programs to main menu in Alacarte. These entries still don't exist in the Dash. In fact, many items shown (and checked) in Alacarte are not in the Dash.

---

### Post by cbowman57 on 2011-06-16
No Ubuntu tweak helps manage the scripts used by nautilus, one of which is a script that creates a launcher.

Since I originally thought you needed to create a launcher so it could be added to the Dash a nautilus script was the first thing that came to mind.

---

### Post by Frogs Hair on 2011-06-16
Make sure the programs are added to the main menu. I had this happen with a dictionary and a couple of other programs I installed . Once I checked the box in the main menu dash was able to locate them. An example is image viewer . I don't have the box checked in main menu so dash can't find it .

---

### Post by compmodder26 on 2011-06-16
> **brandones said:**
> Yeah, I know how to create launchers, but is it possible to integrate them into the Dash? I also didn't find, in my somewhat cursory click-through, anything in Ubuntu Tweak that seemed very helpful in launcher or Dash management.

EDIT 1: Alacarte looks wonderful, I'll give that a shot.

EDIT 2: Update: Added entries for programs to main menu in Alacarte. These entries still don't exist in the Dash. In fact, many items shown (and checked) in Alacarte are not in the Dash.

Have you logged out and logged back in?

---

