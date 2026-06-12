---
title: "Can't get rid of wine!"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by arashiko28 on 2009-11-29
I want to completely delete wine and reinstall but I can't get rid of it on the applications menu

I already tried sudo apt-get remove --purge wine 
and deleted the wine folder, but still remains, I also went for the software sources but no success...

Any ideas?

---

### Post by Virtual Liberty on 2009-11-29
```
find / -name wine -exec rm -r {} \;
```

---

### Post by Norm24 on 2009-11-29
System>Preferences>Main Menu

Scroll down under items till you see Wine.Highlight it and choose delete.

---

### Post by brij on 2009-11-30
Do you mean you have already removed wine but the wine  menu still appears in the applications list if yes then all you need to do is delete the folder
$USER/home/.local/share/applications/wine.

What happens is when you install a program under wine it installs the program into wine directory under your home directory now when you uninstall that program or say wine it removes the wine directory from your home drive but it doesn't delete the desktop files which appears in the menu.

---

### Post by arashiko28 on 2009-11-30
Now I have reinstalled it and it doesn't show on the main menu. How do I restore that? I have done all I can.

PD: I'm installing 1.1.24+ version because of the need to have MSO2007 for work purposes...

---

### Post by arashiko28 on 2009-11-30
I found the solution, here's how I solved it:

>  Originally Posted by mc4man
when you manually delete a menu item like wine it writes an entry to /home/<user name>/.config/menus/applications.menu
Code:
[QUOTE]<Name>wine-wine</Name>
		<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
		<Deleted/>


remove the <Deleted/>
[/QUOTE]

---

