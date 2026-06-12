---
title: "missing desktop"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by degarb on 2010-03-01
Every now and then in gnome, my desktop disappears.   

In windows, I would kill explorer.exe and restart it.  How do I get it back without logging out and in again?

---

### Post by Hospadar on 2010-03-01
It might be nautilus, there is a process killer somewhere, I always just use the terminal, you can alt-f2 'gnome-terminal' (or just run the command in the alt-f2 window, this is assuming you can't see menus).

If alt-f2 doesn't work, go over to a tty, ctrl-alt-f1 (you can also ctrl-alt-f2, f3, etc.  ctrl-alt-f7 will go back to the gui).

There are a few possibilities as I see it.  Nautilus, which provides the backgrounds and file manager might die.  gnome-panel (your top and bottom menu bars might die).  Or perhaps your whole X session (X is the program that runs the entire GUI at a low level) might have died.

If the problem was nautilus, try 'killall nautilus', if gnome-panel 'killall gnome-panel', if it's your X session, 'sudo /etc/init.d/gdm restart'.  the 'killall' commands are preferable since they won't kill your whole session, but if the session is crashed as a whole, you'll need to restart it.  As I implied, the gdm restart command will totally restart your GUI session, killing anything that may be running inside it.

---

### Post by switch10 on 2010-03-01
do a;
```
 gconf-editor 
```

then apps>nautilus>prefs>check "show_desktop"

that is, if you can still use the GUI.

---

### Post by degarb on 2010-03-02
> **Hospadar said:**
> It might be nautilus, there is a process killer somewhere, I always just use the terminal, you can alt-f2 'gnome-terminal' (or just run the command in the alt-f2 window, this is assuming you can't see menus).

If alt-f2 doesn't work, go over to a tty, ctrl-alt-f1 (you can also ctrl-alt-f2, f3, etc.  ctrl-alt-f7 will go back to the gui).

There are a few possibilities as I see it.  Nautilus, which provides the backgrounds and file manager might die.  gnome-panel (your top and bottom menu bars might die).  Or perhaps your whole X session (X is the program that runs the entire GUI at a low level) might have died.

If the problem was nautilus, try 'killall nautilus', if gnome-panel 'killall gnome-panel', if it's your X session, 'sudo /etc/init.d/gdm restart'.  the 'killall' commands are preferable since they won't kill your whole session, but if the session is crashed as a whole, you'll need to restart it.  As I implied, the gdm restart command will totally restart your GUI session, killing anything that may be running inside it.

ctrl atl f2  and return didn't work. sudo...restart  had problems getting back into gui.  also looked as involved as logging out and relogging in. gnome-panel kill didn't help.  

then apps>nautilus>prefs>check "show_desktop"
   I dont think this is the proper location.  I don't see this option.

Killall nautilus, said no nautilus process.  If i type nautilus, it opens, eventually nautilus, and DESKTOp reappears!   But on close, it disappears again. 

I obviously don't want to keep nautilus open forever every session.

---

### Post by degarb on 2010-03-02
I see if i open nautilus by terminal then killing the terminal kills the desktop.  but If I start by alt f2, then If I kill the nautilus, the desktop remains.

I really don't want a panel with nautilus.  So will create a app menus item, which I don't see.

---

### Post by lyall on 2010-03-02
Recover a Damaged Desktop

when you log on at the Option button on the Login screen and click on Sessions.
select Failsafe Gnome
you should be able to repair your desktop or possibly even use the Users and Groups program to create a new account for the future 

this info is from the **Ubuntu Kung Fu** book
it is **109 Recover a Damage Desktop** from the book

also the the following link it might help
[https://help.ubuntu.com/community/LiveCD]("https://help.ubuntu.com/community/LiveCD")

hope this helps

good luck and have fun learning

---

