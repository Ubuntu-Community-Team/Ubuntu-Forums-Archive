---
title: "&quot;There is no application installed for executable files&quot;"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by HasanYavuzOZDERYA on 2011-02-03
I was developing an application using Qt Creator, c++. Everything was going fine. I want to to try my app in another linux that hasnt qt. So i booted ubuntu live from usb stick. Of course my app didn't work. Wanted qt's so files. Then i run ubuntu (the one i just developed my app and succesfully run it, ubuntu 10.04 amd64). Opps none of my apps works! I get this eror: "There is no application installed for executable files". When i try to rebuild my project qt creator gives this error: 

 [COLOR=#c80000][FONT=Monospace]Failed to start program. Path or permissions wrong?[/FONT][/COLOR]

and no build errors. 

I looked file properties->permissions->Allow executing file as program, it's checked.

Please help before I go mad!

---

### Post by HasanYavuzOZDERYA on 2011-02-03
Well this is strange to me.  Those files that i couldn't run were in a NTFS partition. I had used storage device manager to mount this partition on boot. I set defaults for this partition using storage device manager. Now everything looks fine... :-k

---

