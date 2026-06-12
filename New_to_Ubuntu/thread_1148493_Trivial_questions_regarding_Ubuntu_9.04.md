---
title: "Trivial questions regarding Ubuntu 9.04"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by GreggyZed on 2009-05-04
Hi,

I've recently made the switch (successfully this time), from Windows to Ubuntu 9.04 but have a couple of random questions that are incredibly insignificant but I have not found the answer to.  Any help here would be greatly appreciated:

**1.**  How do you set the default programs for opening specific devices/filetypes?  Currently some are not the way I would like.

**2. ** I am using the Oxygen icon set but want to change the running man icon next to the username for the "Switch users or shut down" menu but am unable to locate.  I've successfully changed a couple of others but cannot find this one.

**3.** Is there a way to change the icon for each individual device like in Windows how you can click Change Icon and select the icon of your choice just by right-clicking on a file or device?

If I solve these minor quibbles, everything will be pretty much perfect!  I will definitely be using this OS in the long-term!

Thanks again!

---

### Post by LowSky on 2009-05-04
1. under System tab look for default programs or something to that effect
2. Dont know how but If you delete the switch user/shut down button it moves itself automatically to be under System, out of site out of mind I say
3. If it under the application menu or on the panel then right click on it to edit.


hope this helps

---

### Post by Hospadar on 2009-05-04
1) right click on the file, go to properties, there's a tab in there that lets you set the default app

2) don't know, probably just have to figure out where that icon is stored and switch it, usually somewhere in /usr/share/something

3) not to my knowledge, at least not in a way that's permanent.  You could make a link on the desktop to that device, (i.e. /home/yourname/Desktop->/media/windows) or whatever, and set the icon for that.  gnome automatically generates links for that kind of thing but they arn't real links persay, just nautilus shortcuts.  read up on the "ln" command for more on links, you'll want to do something like "ln -s"

---

### Post by GreggyZed on 2009-05-04
1) right click on the file, go to properties, there's a tab in there that lets you set the default app

Ahha! Exactly what I was looking for! Thanks!

2. Dont know how but If you delete the switch user/shut down button it moves itself automatically to be under System, out of site out of mind I say

That's perfect.  I removed it from the panel then dragged the shut down and log-out icons where it was and now it looks much better. :)

And as far as 3 goes, I can certainly live without that.  Thanks folks!  It's just that I set the icon to look like my iPod but when I plug my PSP in it has the same icon.  That is so insignificant I can't believe I care, though.

Thanks folks!

---

