---
title: "Can't edit File Permissions"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Totooch on 2011-02-22
Hi all,
I'm trying to install a windows application with Wine (I know, I know, blame on me :P ). The first thing I need to do is to set the file as executable. I went to properties>file permission and tried to check the "Allow executing file as program" flag but I cannot edit any of the options there.
I suppose it's because I don't have enough rights, even if I logged as an administrator. How do I get enough rights to edit the file permissions? 
I'd really like to use the graphical options, they put a "permissions" tab there, there should be a reason :P

Thank you!

---

### Post by TeoBigusGeekus on 2011-02-22
> **Totooch said:**
> 
I'd really like to use the graphical options, they put a "permissions" tab there, there should be a reason :P


In case you regret it
```
chmod +x file.ext
```

---

### Post by cariboo on 2011-02-22
You shouldn't have to change any file permissions, just prepend the command with wine eg:

```
wine /path/to/file.exe
```

---

### Post by Totooch on 2011-02-22
Hi all, thank you both! That actually solved my issue on the short term

Silly question: given the point that my next goal is to let my 55yo father install Ubuntu on his pc, why those two simple commands you suggested me can't be done graphically?
I mean, chmod is the command for "right-click>properties>file permissions" and wine is the command for, well just double clicking on the exe you'd like to run.

Don't you know any easy and fast get-the-admin-rights tool? If I'm not wrong in ubuntu 8 there was an option in system>administration that let you have admin rights for the session or in any case until you suspended them again. Is this option anywhere on ubuntu 10.10?

Thanks!

---

### Post by oldos2er on 2011-02-22
> **Totooch said:**
> Don't you know any easy and fast get-the-admin-rights tool? 

CLI: **sudo -i**

GUI: **gksu nautilus**

---

### Post by 3rdalbum on 2011-02-22
> **Totooch said:**
> Hi all, thank you both! That actually solved my issue on the short term

Silly question: given the point that my next goal is to let my 55yo father install Ubuntu on his pc, why those two simple commands you suggested me can't be done graphically?

You can. It's just easier to say "put this one thing into the terminal" rather than "click on x, then y, then right-click and select z" etc.

You can't change permissions on a read-only filesystem such as a CD-ROM. And you can't add the execute permission to a filesystem that doesn't support it, for instance NTFS.

---

### Post by asmoore82 on 2011-02-23
> **3rdalbum said:**
> You can't change permissions on a read-only filesystem such as a CD-ROM. And you can't add the execute permission to a filesystem that doesn't support it, for instance NTFS.
This is the most likely reason for permission troubles in the GUI.

So that takes care of that "why not GUI" situation.

The other situation with wine is a little different.
Wine is, at its heart, predominantly a command line tool. The Windows apps
you run with it will of course be graphical, but Wine itself leans towards
the command line. The reason for this is that Wine pushes beyond just compatibility
and starts to blur the line into more "power user" *pseudo* virtualization.

Especially if you ever get into using multiple Wine config folders to
"bottle" up Windows apps and keep them from stepping on each others toes.

It is highly possible though for you to get wine set up exactly how you want
it for 1 particular app and then create a simple launcher for that app.
Then Wine is fairly command line free until it needs upgrading or tweaking.

For example, my wife and I both have simple launchers for Burger Shop and
Counter-Strike, but in reality, each game is in its own wine bottle.
The two different launcher commands are:
```
#Burger Shop
env WINEDEBUG="-all" WINEPREFIX="/home/asmoore/.wine-subs" wine "C:\\Program Files\\Burger Shop\\BurgerShop.exe"
#CStrike
env WINEPREFIX="/home/asmoore/Games/wine-cstrike" wine "C:\\Program Files\\Valve\\hl.exe" -nomaster -game cstrike +localinfo mm_gamedll dlls/zbotcz.dll
```

---

### Post by Totooch on 2011-02-23
> **3rdalbum said:**
> You can. It's just easier to say "put this one thing into the terminal" rather than "click on x, then y, then right-click and select z" etc. Yeah, I suspected this :P

> **3rdalbum said:**
>  you can't add the execute permission to a filesystem that doesn't support it, for instance NTFS.
Gaaaaawh, this is it, I just copied the file over to my desktop and now I'm able to edit the execute permissions. I just didn't know I cannot use a NTFS filesystem to execute files on linux.

Thanks a lot!

---

### Post by Morbius1 on 2011-02-23
The default permissions have changed on NTFS such that no files are tagged as executable. But Wine doesn't care if it's executable and it has no way of determining if an exe file has a linux executable bit set.

See here for two solutions ( Post #9 and Post #10 ): [http://ubuntuforums.org/showthread.php?t=1690130](http://ubuntuforums.org/showthread.php?t=1690130)

---

