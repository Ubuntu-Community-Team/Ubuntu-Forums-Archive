---
title: "VLC hijacked my places menu"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by steve7777777 on 2011-03-08
I'm using Ubuntu 10.10. After applying upgrades tonight VLC hijacked my PLACES menu. When I click on 

Places->Home Folder 
or
Places-> Desktop

VLC is invoked and tries to open these areas (without success!)

This seemed to be an old bug from 2008.
Bookmarks and shortcuts on the desktop work.

Any idea what's going on?

---

### Post by prshah on 2011-03-08
> **steve7777777 said:**
> VLC hijacked my PLACES menu. When I click on Places->Home Folder or Places-> Desktop
VLC is invoked and tries to open these areas

From: > **ZorgTheDestroyer said:**
> to 'Places - any folder' it opens in a videoplayer. 

This is a known bug. Open "Computer" from the Places location, (or just run nautilus from the Alt+F2 "command" box). Now, navigate to your home directory, then right click any directory within it, and choose "Open With"-"Open with other application"; in the box that pops up, choose "File Browser".

From now on, it will open correctly.

Here's another way you can try; System-Preferences-File Management. If you can't find that option, press Alt+F2, and run ```
nautilus-file-management-properties
```

Then click the Behaviour tab, and select the option "Always open in browser windows", then click Close.

Now perform the earlier method again, and see if it "sticks"

If that doesn't work as well, right click any directory in your home directory, then choose Properties-Open With-File Browser-Close. If the "File Browser" option is not there, click on Add and locate "File Browser". If you still cannot find the option, at the bottom of the "Add Application" window, click on "Use a custom command" and give the command as ```
nautilus
```.

---

### Post by mrhhug on 2011-03-08
im suprised! VLC has never been anything but a workhorse for me.

ok, i stole this command
```
gedit ~/.gtk-bookmarks
```
from this ubuntu archives [HTML]http://ubuntuforums.org/showthread.php?t=623275[/HTML]

so please type "gedit ~/.gtk-bookmarks" in a terminal and this should be the output of your places menu. post response here.

---

### Post by steve7777777 on 2011-03-08
Thanks I will try it tonight and post. VLC has been a workhorse - very nice program and IMO the best for video under Ubuntu.

---

### Post by steve7777777 on 2011-03-09
> **prshah said:**
> 

Here's another way you can try; System-Preferences-File Management. If you can't find that option, press Alt+F2, and run ```
nautilus-file-management-properties
```Then click the Behaviour tab, and select the option "Always open in browser windows", then click Close.


This worked! Thanks for the help.

---

### Post by beacon on 2011-04-01
I think my problem is much the same. When I click on places>home I get shotwell and nothing else. When I click on places>computer it only has external devices. According to a very good book I have on Ubuntu, I should be able to access nautilus by going to places> home, but I can't. And I am not able to follow the advice given by Steve, as there is no option 'open in browser window' under behaviour.

Any thoughts would be welcome.

---

### Post by plucky on 2011-04-01
> **beacon said:**
> I think my problem is much the same. When I click on places>home I get shotwell and nothing else. When I click on places>computer it only has external devices. According to a very good book I have on Ubuntu, I should be able to access nautilus by going to places> home, but I can't. And I am not able to follow the advice given by Steve, as there is no option 'open in browser window' under behaviour.

Any thoughts would be welcome.

Alt + F2 and type in "nautilus" without the quotes, in the window that opens.

Good Luck

---

### Post by beacon on 2011-04-01
Thanks very much plucky for the quick reply. Unfortunately I had tried that several times, as I did the other suggestions in the thread. Nothing worked. I think there was something else going wrong, so I have just re-installed and so far things are going well.

---

### Post by keroman on 2011-04-01
I looked all over to find a solution to this, found one here 

[http://www.etdsonline.com/tutorials/ubuntu/415-items-on-places-menu-opens-vlc.html](http://www.etdsonline.com/tutorials/ubuntu/415-items-on-places-menu-opens-vlc.html)


hope it helps

---

### Post by beacon on 2011-04-01
Many thanks Keroman. I think that would have been just the job, but I had already re-installed and that resolved the problem. I have made a note of your suggestion, however, as I think it might be useful in future.

Regards

---

