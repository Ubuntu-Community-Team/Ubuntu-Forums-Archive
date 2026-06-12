---
title: "Where are my new apps, and how do I invoke them?"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by macruadhi on 2009-02-28
I have added several new apps that didn't put shortcuts in the menus. Where can I find them? I used synaptic and deb files.

---

### Post by adult swim on 2009-02-28
the executables are normally in /usr/bin
try hitting alt+f2 and typing in the name of the program and hitting enter to run them

---

### Post by lindsay7 on 2009-02-28
I was having the same problem and you suggestion of alt + f2 worked. Now, how do I make a short cut to the desktop of application menu so that I do not have to do the alt + f2 and type program name?

---

### Post by Michael.Godawski on 2009-02-28
hi,

perhaps this guide will help you a bit:


[LIST]
[*][http://ubunturesources.ub.ohost.de/launchers.html](http://ubunturesources.ub.ohost.de/launchers.html)
[/LIST]

---

### Post by adult swim on 2009-02-28
right click on top of applications and select edit menus
on the right side of the window that opens up, select new item and fill in the form.
you can name it whatever you want, and the comment can be whatever you want it to be.  the only thing that needs to be exact is the command.  just enter in here whatever it was that you were entering in when you pressed alt+f2 to run the program.  then click ok and make sure that the new item you added is checked and it should appear in the menu.

---

### Post by ScarySquirrel on 2009-02-28
"Launchers" are the Ubuntu version of "Shortcuts".
Right click you desktop, then click "Create launcher", then type the name of the program you want to launch, or browse for it.

---

### Post by lindsay7 on 2009-02-28
Thanks to you all.  That makes life easier it all makes sense now.  I have been spending a lot of time reading posts and all of these little tips are really great.

This is a super forum and everyone is very helpful.

Thanks again.

---

### Post by 3rdalbum on 2009-02-28
Sometimes you won't know the exact name of the program. To find the exact name of the program you can look in Synaptic; right-click the package, choose Properties, and then go to Installed Files. Any installed files in /bin, /usr/bin, /usr/games or /opt are likely to be executables and can be added to the menu.

My signature has a screencast of it, if you need more help.

---

