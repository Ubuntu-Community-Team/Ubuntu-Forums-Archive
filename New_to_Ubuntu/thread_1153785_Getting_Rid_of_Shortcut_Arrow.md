---
title: "Getting Rid of Shortcut Arrow"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by tommo12 on 2009-05-09
Hey, using Ubuntu for a couple of days now... what a breath of fresh air it is. Never going back to Windows...

ANYWAY my question is the Shortcut arrow on a shortcut icon, how do you get rid ot it? 

I searched google and came up with the directory of the file

/usr/share/icons/Tangerine/16x16/emblems
and 22x, 24x, 32x

and they said to make it transparent. 

The only problem is I do not have access to these files because I do not have root permissions. 
I tried to log in as root, didn't work. I can't copy the files and edit them else where etc.

Is there an easy way around this other than typing in code into the terminal I am pretty new to Linux and would rather find a graphical way around this.

Cheers

Your New Linux BUddy :)

---

### Post by Peter09 on 2009-05-09
Do you not have root permission because you are not an admin user or is it because you do not know how to. If you are the only user on the PC then you should have admin permissions.

---

### Post by 3rdalbum on 2009-05-09
When you log in, you are logging in as a normal user. For security and stability reasons, normal users are not allowed to change anything outside their home directory and /tmp. The only user who can alter the system is the "superuser", also known as "root".

You can't log in as root on Ubuntu, but you can run a program as root. In this case, you will want to run Nautilus (the file browser) as root, and you can do it thus:

```
gksudo nautilus
```

The "gksudo" bit tells Ubuntu that you want to run Nautilus as the superuser.

A new file browser window will open, with full root permissions. Use it wisely. Note that if you right-click those files and select "Open with The Gimp", then The Gimp will open as root.

When you're done, quit The Gimp and close the instance of Nautilus that is running as root.

---

### Post by tommo12 on 2009-05-09
I have root password, which i use to install whatver usually.. but I cant edit these files because they have the permission only for Root. as I said I can't log in and if i try to do anything to these files they say no permission or nothing happens.... no password box or anything :(

---

### Post by Bölvaður on 2009-05-09
to be allowed to change the files you need super user rights, most often given to you by the command sudo in ubuntu

but we have special graphical sudo command for noncommand line commands (like programs that got graphical user interface), gksudo or gksu

the file manager is named nautilus

and the place you want to go to is  /usr/share/icons/Tangerine/16x16/emblems


Press Alt+F2 and copy and paste this into that window
> gksu nautilus  /usr/share/icons/Tangerine/16x16/emblems


note that only the window that opened by this command has super user rights, no other.

Also note that if you are using some else icon theme than Tangerine you will have to change that theme but not the Tangerine icon theme... the default one for ubuntu is Human, but I do belief they borrow the icon you wish to change from either the gnome icon set or tangerine.

---

### Post by tommo12 on 2009-05-09
thanks everyone, I got in there and deleted the files, then it came back with default shortcut graphics so i deleted them too hehe and now I have none which looks great! cheers all

---

