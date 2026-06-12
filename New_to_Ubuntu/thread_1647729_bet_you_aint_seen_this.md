---
title: "bet you aint seen this"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by slixz85 on 2010-12-17
just installed xfce and removed gnome i now have a little problem maybe simple. my menu is not right at all look at the screenshot. need some help on a fix

the log out and help buttons and maybe somethin else in the whole menu is doubled and stuff

---

### Post by Linux_junkie on 2010-12-17
I cannot see anything wrong with the menu.  What am I looking for?

---

### Post by slixz85 on 2010-12-17
i edited the above post you prob caught it early

---

### Post by slixz85 on 2010-12-17
also the windows in xfce around them  on the edges and stuff seem glitchy any ideas

---

### Post by Linux_junkie on 2010-12-17
It looks like you still have some Gnome apps left over that hadn't been removed completely when you uninstalled Gnome.  You did uninstall not delete didn't you?

---

### Post by slixz85 on 2010-12-17
yeah i used this also [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce) there was another page on that site too that showed me how to do the other step couldnt find it too show ya though but yeah i did it the right way supposedly and just installed deborphan to take all the extra crap from it out

---

### Post by slixz85 on 2010-12-17
i ran the above link step twice once before reboot then reboot and did it, it found more but only 2 after reboot. now it dont show any

---

### Post by Linux_junkie on 2010-12-17
Can you right-click on the duplicate menu item and if it has the option to remove then just remove it. Otherwise you need to go in to the menu editor and as I'm not in XFCE at the moment I cannot tell you how to view it.

---

### Post by slixz85 on 2010-12-17
still learnin dont know exactly what to look for but i got 2 screenshots of all my processes

gnome keyring is only one that shoots at me what is it

---

### Post by slixz85 on 2010-12-17
ok will look around more thought was something major since switched environments

---

### Post by slixz85 on 2010-12-17
cant find menu editor anywhere unless somehow lost in transition

---

### Post by thatguruguy on 2010-12-17
You have to edit the xfce menu manually if you want to make changes.

EDIT: Now I see the problem.

---

### Post by Linux_junkie on 2010-12-17
At last I've found out how to edit the menu.

The menu's configuration file, xfce-applications.menu, can be found under the path $sysconfdir/xdg/menus/xfce-applications.menu. For binary packages, $sysconfdir is often /etc and for source compiles, it defaults to /usr/local/etc. 
 The previous menu editor is not available anymore. However you can customize your menu by copying xfce-applications.menu to $XDG_CONFIG_HOME/menus and by modifying it with a text editor such as mousepad or gedit. Please remember that the file should be UTF-8 encoded. For more information on menu editing, please see the Xfce Wiki.

Hope this helps you.

---

### Post by slixz85 on 2010-12-19
> **Linux_junkie said:**
> At last I've found out how to edit the menu.

The menu's configuration file, xfce-applications.menu, can be found under the path $sysconfdir/xdg/menus/xfce-applications.menu. For binary packages, $sysconfdir is often /etc and for source compiles, it defaults to /usr/local/etc. 
 The previous menu editor is not available anymore. However you can customize your menu by copying xfce-applications.menu to $XDG_CONFIG_HOME/menus and by modifying it with a text editor such as mousepad or gedit. Please remember that the file should be UTF-8 encoded. For more information on menu editing, please see the Xfce Wiki.

Hope this helps you.


well you aint seen a menu like that lol. thanks alot

how can i assure all gnome stuff has been taken off since these buttons have stayed on the menu theres gotta be something. i used the above link to remove it that way but seems to be something left behind?

---

