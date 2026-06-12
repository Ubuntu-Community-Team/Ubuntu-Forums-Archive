---
title: "[SOLVED] Editing a read-only file"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by danlembek on 2008-12-28
I'm trying to access xorg.conf (filesystem/etc/X11/xorg.conf) in order to add the option for screen rotation for the nvidia settings. However, I can't save the changes because I'm told that I'm not the "owner" and don't have privileges to edit the file.

---

### Post by OutOfReach on 2008-12-28
You have to open with root privileges, for example from the command line it would be:
```

gksu gedit

```

Or whichever editor you use.

---

### Post by newbee70 on 2008-12-28
Deleted

---

### Post by northern lights on 2008-12-28
Open a Terminal from Applications > Accessories and run```
gksu gedit /etc/X11/xorg.conf
```
for GUI editing
or ```
sudo nano /etc/X11/xorg.conf
```for editing directly in the Terminal.

[EDIT]
> **newbee70 said:**
> right click on the file you want to change, at the bottem click on properties, then click on permissions.
Theoretically a working option and not entirely wrong. However, it is much more advisable to open the file in question as root, rather than permanently altering file permissions.
[/EDIT]

---

### Post by gn2 on 2008-12-28
Press Alt + F2 then type: gksudo gedit /etc/X11/xorg.conf

This will open xorg.conf in Gedit, a graphical (gk) text editor application with super user (sudo) permissions.

Remember to save a back-up copy of your xorg.conf before modifying it.

---

### Post by Bölvaður on 2008-12-28
if you are changing that file you should make backup copy if something goes wrong.

you can either use the gui :

press Alt+F2 and type:
gksudo nautilus

and you can figure out the rest easy....


or do everything from the terminal

cd /etc/X11

and then type sudo in front of all the operations for super user access.


like "sudo cp xorg.conf xorg.conf_backup" for making the backup

gksudo is sudo for gui stuff so  "gksudo gedit xorg.conf" would be pretty good.

---

### Post by scorp123 on 2008-12-28
> **newbee70 said:**
> right click on the file you want to change, at the bottem click on properties, then click on permissions. Nope, that's not the right way to edit a systen-wide config file!

---

### Post by newbee70 on 2008-12-28
Deleted

---

### Post by northern lights on 2008-12-28
> **newbee70 said:**
> It is a Real and viable alternative, always learn All options, then choose the best for use.
I thought I was rather pc and diplomatic about this.

Since you prefer to further promote, how should I put it without being to blunt, "bad ideas", let me put it this way:

It technically works. But that is it. It is _not_ a viable alternative, if you do not want to jeopardize the long-term security and stability of your system.

If it was a viable alternative, you could enable the root account also.

What you promote is entirely counter-productive to the Ubuntu security model.

---

### Post by malathion on 2008-12-28
> **newbee70 said:**
> right click on the file you want to change, at the bottem click on properties, then click on permissions.

DO NOT DO THIS!! System files have those permissions set for important security reasons! To edit protected system files, use sudo as others have suggested.

---

### Post by billgoldberg on 2008-12-28
> **newbee70 said:**
> right click on the file you want to change, at the bottem click on properties, then click on permissions.

Your name says a lot.

Whatever you do, don't start messing with file permissions if you know nothing about them.

You could end up in serious trouble.

---

### Post by scorp123 on 2008-12-28
> **newbee70 said:**
> It is a Real and viable alternative **[COLOR="Red"]No it's not.[/COLOR]**

---

### Post by billgoldberg on 2008-12-28
I hope that newbie and the op got it now.

---

### Post by gsocker on 2008-12-28
> **newbee70 said:**
> right click on the file you want to change, at the bottem click on properties, then click on permissions.
Changing the permissions will fail anyway  since xorg.conf is owned by root. You cannot change permissions files you don't own! Also, follow people's  advice and make a backup before you edit. If this file has an error you will not have a GUI after you restart the X server.

---

### Post by danlembek on 2008-12-28
> **gsocker said:**
> Changing the permissions will fail anyway  since xorg.conf is owned by root. You cannot change permissions files you don't own! Also, follow people's  advice and make a backup before you edit. If this file has an error you will not have a GUI after you restart the X server.
Yeah. I was unable to change via properties>permissions for the same reason that I couldn't simply open the file and change the text. I received a non-owner restriction message. Anyway, I used gn2's method and it works fine now.

---

### Post by northern lights on 2008-12-28
> **danlembek said:**
> Yeah. I was unable to change via properties>permissions for the same reason that I couldn't simply open the file and change the text. I received a non-owner restriction message.
You've really tried to follow this, when everyone else advised against it?
:-k

---

### Post by sirebral on 2008-12-28
> **danlembek said:**
> Yeah. I was unable to change via properties>permissions for the same reason that I couldn't simply open the file and change the text. I received a non-owner restriction message. Anyway, I used gn2's method and it works fine now.

This is part of the security of Linux.

> **northern lights said:**
> You've really tried to follow this, when everyone else advised against it?
:-k

This is one way we learn about computers.  It's forgivable since it's his, he was warned, and it is owned by root.

---

### Post by northern lights on 2008-12-28
> **sirebral said:**
> This is one way we learn about computers.  It's forgivable since it's his, he was warned, and it is owned by root.
Fair enough.

Here's some really good advice:

Unplug your machine, climb the largest building in your town, top floor, open a window and chuck it out.

Trust me, you'll learn something. Namely that it breaks when thrown from decent heights.

Are you going to go try it now?!

---

