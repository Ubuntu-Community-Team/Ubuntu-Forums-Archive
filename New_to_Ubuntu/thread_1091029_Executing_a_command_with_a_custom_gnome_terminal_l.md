---
title: "Executing a command with a custom gnome terminal launcher"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Vunutus on 2009-03-08
I'm trying to set up a custom launcher for use with TinTin++ (MUD client for those who are unfamiliar). I want the launcher to start gnome-terminal, hide the menubar, set the terminal profile (to make the colors suitable for MUDs), and of course launch tt++.

The command section of my launcher looks like this:

```
gnome-terminal --hide-menubar --window-with-profile=tintin --command=tt++
```

The first two options work correctly, but it fails to launch tt++. When the window comes up, it just hangs there with a blinking cursor and no shell prompt.

What am I doing wrong?

---EDIT---

I did some poking around and I think I found the problem, although I don't know the solution. Whenever I bring up the tintin launcher and let it hang there, if I open up another terminal and run "ps aux | grep tt++" it shows tt++ as running, yet I cannot interact with it. This means that it is indeed being launched but apparently the terminal is not getting control over it. Does anyone know why?

---

### Post by unutbu on 2009-03-09
Try this:
```
gnome-terminal --hide-menubar --window-with-profile=tintin -x bash -c "tt++"
```

---

### Post by Vunutus on 2009-03-09
> **unutbu said:**
> Try this:
```
gnome-terminal --hide-menubar --window-with-profile=tintin -x bash -c "tt++"
```

That ends up doing the same thing mine does. Both of these lines are correct according to the gnome-terminal man page.

It works fine if I omit the part about starting tintin, but then I have to type tt++ every time. This is the 21st century, that isn't acceptable :D

I did some poking around and I think I found the problem, although I don't know the solution. Whenever I bring up the tintin launcher and let it hang there, if I open up another terminal and run "ps aux | grep tt++" it shows tt++ as running, yet I cannot interact with it. This means that it is indeed being launched but apparently the terminal is not getting control over it. Does anyone know why?

---

### Post by Vunutus on 2009-03-10
Bump

---

### Post by RomeReactor on 2009-03-10
Hi. Try it like this:
```
gnome-terminal --hide-menubar --window-with-profile=tintin -e tt++
```

---

