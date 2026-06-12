---
title: "[SOLVED] Just installed Kdenlive but can't find it"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by thadacto on 2008-12-27
I have just installed Kdenlive video editor using the Synaptic manager. But it doesn't appear in any of my >Application menus.
I have used >Places> search for files but it can't find Kdenlive. In the synaptic Manager there are two files relative to Kdenlive marked as installed. 
Where is the program application??

---

### Post by nhasian on 2008-12-27
in a terminal type:

```
whereis kdenlive
```

if its not in the path then do:

```
sudo updatedb
```

then

```
locate kdenlive
```

---

### Post by thadacto on 2008-12-27
Thanks, nhasian, found it with whereis and it is working. Now I just have to work out how to get the name (shortcut) onto the menu.

Incidently, what is the difference between "whereis" and "locate"?

---

### Post by jerome1232 on 2008-12-27
> **thadacto said:**
> Thanks, nhasian, found it with whereis and it is working. Now I just have to work out how to get the name (shortcut) onto the menu.

Incidently, what is the difference between "whereis" and "locate"?

Just right click you menu, click edit menus, Figure out where you would like it to appear, then select New Item.

You can also get this editor via System->Prefrences->Main Menu

or

alt+f2; then type alacarte.

---

### Post by thadacto on 2008-12-27
Cheers jerome1232, did it - eventually!! Finally got it where I want it.

---

### Post by nhasian on 2008-12-27
> **thadacto said:**
> Incidently, what is the difference between "whereis" and "locate"?

*whereis* locates the binary, source, and manual page files for a command.

*locate* will find any files by name from the database.  the database is updated every morning at 5am so if you made any changes since then they wont show up in the search unless you manually update the database with the command *updatedb*

---

