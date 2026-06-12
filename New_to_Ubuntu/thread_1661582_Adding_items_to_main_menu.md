---
title: "Adding items to main menu?"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by ~Maxx on 2011-01-06
Hello.  I've installed a couple of programs that haven't shown up in the main menu ("start" menu).  Is there any way I can add them in under the proper sub menus?

Much appreciated!

---

### Post by stoneage on 2011-01-06
Press ALT+F2 and enter alacarte.

You can add new entries from there.

---

### Post by Dex73 on 2011-01-06
You may be able to fix it by going to System/Appliances/Main Menu. I know it gives you the ability to decide weather things show or not. Maybe something is FUBAR in there.

---

### Post by ~Maxx on 2011-01-06
> **stoneage said:**
> Press ALT+F2 and enter alacarte.

You can add new entries from there.

Sorry to be a newb...  but what do I enter in the command line?

---

### Post by gmjs on 2011-01-06
Unfortunately, I don't have a Lubuntu install handy but I don't think that the 'alacarte' application for editing the menu entries is installed by default in Lubuntu.  Furthermore, I don't think it actually works if it is installed either!

All menu entries use the xdg standard and are stored as '.desktop' files usually in /usr/share/applications.  It's very different from the 'Windows' way of doing it and can get quite complicated.  It works very well though!  You'll probably find more information about it in the online Help on the menu.

If the applications you installed don't create a menu entry automatically (and some don't) you could probably create (or copy an existing one) a '.desktop' file and add it to /usr/share/applications.

I'd have to download a Lubuntu distro to check this for you.  I'll let you know if I find out more!

Hope this helps.

Graham

---

### Post by ~Maxx on 2011-01-06
Thanks gmjs.  Definately different than Windows, but that's part of the fun.  I'll fiddle around with it later on and see what I can accomplish.

---

### Post by gmjs on 2011-01-07
OK, I've tried Lubuntu 10.10 and it does use the xdg standard for menu entries, but it appears that there is no graphical-interfaced program for editing them.

You can copy an existing file and edit it to create a new one, or make one from scratch (they're just text files with a particular layout and a '.desktop' file extension).

There's a good example on the LXDE forums here: [http://wiki.lxde.org/en/Main_Menu]("http://wiki.lxde.org/en/Main_Menu")

You'll need root access ('sudo -i' in terminal) to add files to /usr/share/applications or, as recommended in the wiki, /usr/local/share/applications.

You'll see from the example that the group that a shortcut appears in is also specified in the text file.  (The 'groups' by the way are also files, but they are known as 'Directory Entry' files instead and have the '.directory' file extension.  They're stored under /usr/share/desktop-directories).

Hope this helps.

Graham

---

### Post by acreech on 2011-01-07
> **~Maxx said:**
> Hello.  I've installed a couple of programs that haven't shown up in the main menu ("start" menu).  Is there any way I can add them in under the proper sub menus?

Much appreciated!

You can just right click on "Applications" then choose "Edit Menus". This will bring up a new gui. This is where you can add things or take things off of the menu.

---

### Post by ~Maxx on 2011-01-07
> **gmjs said:**
> OK, I've tried Lubuntu 10.10 and it does use the xdg standard for menu entries, but it appears that there is no graphical-interfaced program for editing them.

You can copy an existing file and edit it to create a new one, or make one from scratch (they're just text files with a particular layout and a '.desktop' file extension).

There's a good example on the LXDE forums here: [http://wiki.lxde.org/en/Main_Menu]("http://wiki.lxde.org/en/Main_Menu")

You'll need root access ('sudo -i' in terminal) to add files to /usr/share/applications or, as recommended in the wiki, /usr/local/share/applications.

You'll see from the example that the group that a shortcut appears in is also specified in the text file.  (The 'groups' by the way are also files, but they are known as 'Directory Entry' files instead and have the '.directory' file extension.  They're stored under /usr/share/desktop-directories).

Hope this helps.

Graham

Wow...  You really saved me a LOT of searching around Graham.  Thanks so much for your effort and thorough explanation.  I've got everything just the way I want it now, and I have the know-how to change it in the future.  Thanks again Graham.  All the best!

---

