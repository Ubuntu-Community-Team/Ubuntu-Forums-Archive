---
title: "Installing Windows games"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by h8uthemost on 2011-02-28
Hi guys,

I'm trying to install my mom's Windows games(casino slot games) on Lubuntu through Wine. But I'm running into a problem right from the get-go.

I'm trying to right-click the .exe, hit the Permissions tab, and ticking the box that says Make The File Executable. When I tick that box and hit Ok, I get an error saying this:

: Error setting permissions: Read-only file system

Is there anyway to get around this? If not, would anyone happen to know of any Linux Casino Slot games?

Thank you for any help.

---

### Post by An Sanct on 2011-02-28
Are those games on a CD?

If so, try copying them to the desktop, then set the executable bit.

---

### Post by taseedorf on 2011-02-28
do this.

Copy .exe wherever.

Do sudo chmod +x *.exe

run it.

BOOM

FYI in case you're wondering, do the command in terminal. and make sure you're in the directory you have the .exe's.

---

### Post by h8uthemost on 2011-02-28
That worked perfectly. Can't believe I didn't think of that. :P

Thanks a lot for the help, An Sanct.

EDIT: Thanks to you too, taseedorf.

---

### Post by ronnielsen1 on 2011-02-28
> 
FYI in case you're wondering, do the command in terminal. and make sure you're in the directory you have the .exe's.

Also possible to do in gui if you right click on the exe, choose properties and make sure that executable is clicked on the permissions tab. You can also set exe's to open automatically in wine

---

### Post by taseedorf on 2011-03-01
The only reason I stated to do it my way, is that all exe's in the directory would be changed and it's a bit quicker that way. ;)

---

