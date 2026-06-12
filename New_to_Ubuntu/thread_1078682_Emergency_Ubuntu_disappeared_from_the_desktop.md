---
title: "Emergency: Ubuntu disappeared from the desktop"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Jerriy on 2009-02-23
I think the reason is because earlier I was tinkering at the the default folder status (which was home)

Then a while later I restarted the PC and loaded Ubuntu but instead of landing in my desktop with all the bars and menus and icons, I'm stairing at an empty fuzzy brown abstraction (interpid ibex wallpaper)

I suspect what I need to know is the terminal command for that User-default thing so that I reinstate \home.

Boy this Linux stuff is quite a learning curve. Who knew that just changing a default folder in a user menu would wipe the entire operating system off the map!

---

### Post by Jerriy on 2009-02-23
How does one get into the graphic interface when login fails to lead you there?

---

### Post by Jerriy on 2009-02-23
This is it. This is all I see. Even the mouse cursor has no right-click/left-click drop-down menu.

---

### Post by Temposs on 2009-02-23
> Boy this Linux stuff is quite a learning curve. Who knew that just changing a default folder in a user menu would wipe the entire operating system off the map!

The same thing would happen in Windows if you renamed the C:\Windows folder or something like that. There are lots of system settings kept in your home folder, so you can't just change it without knowing what you're doing. I found this command to change the location of your home folder, so you can try it:

```
sudo usermod -d /path/to/home-dir <your-user>
```

"/path/to/home-dir" would be something like: /home/jerriy

<your-user> would be something like: jerriy

assuming your username on your system is jerriy

---

### Post by Jerriy on 2009-02-23
Yea it worked. Many thanx Temposs!

> **Temposs said:**
> The same thing would happen in Windows if you renamed the C:\Windows folder or something like that. There are lots of system settings kept in your home folder, so you can't just change it without knowing what you're doing.I knew that I was doing something fundamental... just didn't expect to be totally locked out of the whole thing. But it was my fault anyway (since I shoulda had another alternative user pre-installed just for these kind of situations before I started tinkering :redface:

---

### Post by JKyleOKC on 2009-02-23
> **Jerriy said:**
> I shoulda had another alternative user pre-installed just for these kind of situations before I started tinkering :redface:
Tinkering is a good way to learn, but I'd suggest that you create that alternative user, and do most of your tinkering as that user. The reason is that by default, only the first user created at install time has the ability to use sudo and gksudo. Thus the alternative user would not have been able to do this recovery!

To give the second user sudo capability, you need to add the user to the "admin" group. I'm using Xubuntu rather than Ubuntu so the procedure I use wouldn't be the same for you, but the starting point should be the "users and groups" section of the "system" menu...

---

