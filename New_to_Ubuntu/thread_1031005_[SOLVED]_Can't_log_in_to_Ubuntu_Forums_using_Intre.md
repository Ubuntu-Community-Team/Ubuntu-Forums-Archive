---
title: "[SOLVED] Can't log in to Ubuntu Forums using Intrepid"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Lostin60's on 2009-01-04
I am using the Fire Fox that came packed with Intrepid.  When I go to Ubuntu Forums, in the upper right hand corner  the box for username has "username" already typed in, and I can't over write it.  I am unable to click the remember me box.  Also, I have FF set to remember my password.  It stores them, but it doesn't use them.  The screen resolution is odd, too. For instance, the search box overlaps the username box.  In Windows, it all works well. But I think it is an FF issue rather than an Ubuntu issue, but I have found no help in FF. All in all, it is very confusing.  As always, any and all input will be muchly appreciated.

---

### Post by jimmy the saint on 2009-01-04
Do you have any extensions installed?  Try to disable them.  Do you have the page zoomed way in?  sometimes that causes issues for me with text boxes.  If all the fails, go into synaptic and remove firefox.  Make sure to select "completely remove" which will also remove the config files.  Then reinstall and see if it works better.
Good Luck

---

### Post by kansasnoob on 2009-01-05
> **jimmy the saint said:**
> Do you have any extensions installed?  Try to disable them.  Do you have the page zoomed way in?  sometimes that causes issues for me with text boxes.  If all the fails, go into synaptic and remove firefox.  Make sure to select "completely remove" which will also remove the config files.  Then reinstall and see if it works better.
Good Luck

"If all the fails, go into synaptic and remove firefox."

Bad, bad idea! That could break a lot of dependencies!

I'd go to Places > Home Folder > View > Show Hidden Files and look for .mozilla. Then right click ,mozilla and copy-n-paste it to desktop or someplace so you can restore it (or parts of it) if this doesn't work. (I usually have a "Projects" folder for this sort of thing).

Then close Firefox by going to File > Quit. Then go back to .mozilla (in hidden home) and send it to the trash!

When you restart Firefox it will create a new .mozilla. If that solves your problem then we have to restore the parts and pieces you want back.

---

### Post by efexD on 2009-01-05
Did you try clearing cache? Cookies? Etc.

---

### Post by Lostin60's on 2009-01-06
> **kansasnoob said:**
> "If all the fails, go into synaptic and remove firefox."

Bad, bad idea! That could break a lot of dependencies!

I'd go to Places > Home Folder > View > Show Hidden Files and look for .mozilla. Then right click ,mozilla and copy-n-paste it to desktop or someplace so you can restore it (or parts of it) if this doesn't work. (I usually have a "Projects" folder for this sort of thing).

Then close Firefox by going to File > Quit. Then go back to .mozilla (in hidden home) and send it to the trash!

When you restart Firefox it will create a new .mozilla. If that solves your problem then we have to restore the parts and pieces you want back.


Thanks Kansasnoob. That worked perfectly. And I haven't found any parts or pieces I need back. I appreciate the help.

---

