---
title: "Lost apps"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by mgranath on 2009-08-29
Hello

I have installed apps that I can't see. Is there any place where I can see all instaled apps and start them (Ubuntu 9.04)?

---

### Post by mapes12 on 2009-08-29
If you go to a Terminal prompt and type the name of the app that sometimes starts it. What apps are you having a problem with?

---

### Post by d_yat on 2009-08-29
You could always use your file manager (or terminal) and look in the folder here: "/usr/share/applications" (File System -> Usr -> Share -> Applications)

Most of the programs should be there.

If you can't find them in your start menu, it might be worth looking to see if they can be shown by using the Main Menu editor, found here:
System Menu -> Preferences -> Main Menu.
It may just be that it isn't selected. However, you can now add menu  items as you know where to find them now =)

Hope that helps.

(p.s. it is odd how there are some missing programs though)

---

### Post by Paqman on 2009-08-29
> **mgranath said:**
> 
I have installed apps that I can't see.

You might have accidentally installed a command-line only app. It's easily done if you miss the description in Synaptic.

If you want to make sure you getgraphical apps instead of CLI stuff, stick to using Add/Remove for now. All the stuff in there is GUI, and will install a menu item.

---

### Post by 3rdalbum on 2009-08-29
Take a look at the link in my signature. If it's a GUI program, it should have a launcher in your menu; if it doesn't, then you should file a bug report about it.

---

### Post by mgranath on 2009-08-29
Thank You all! I think it was a command line application, qbrew. I manage to start i via the command line.

---

