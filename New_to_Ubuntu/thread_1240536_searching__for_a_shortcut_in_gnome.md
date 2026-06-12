---
title: "searching  for a shortcut in gnome"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by A_M_S on 2009-08-14
Hi
 After installing a application, sometimes its hard to find the launcher in the gnome menus.
 Is there any way to know where the application appears in the gnome menus?

tnx

---

### Post by Buuntu on 2009-08-20
This HOWTO contains several ways of how to search for applications, whether by installing a program or using commands like 'locate' and 'which'.
[http://ubuntuforums.org/showthread.php?t=182201](http://ubuntuforums.org/showthread.php?t=182201)

I'm not sure if there's anyway of knowing where it will be in the GNOME menus however.


***P.S.  You might want to put Ubuntu as your version if you are asking questions about GNOME, since Kubuntu uses the KDE environment instead.

[URL="http://ubuntuforums.org/showthread.php?t=182201"]
[/URL]

---

### Post by Cheezespread on 2009-08-20
Hi A_M_S ,

Some of the applications may not have an entry directly in the menus even when you install it .In that case you can search for the name of the command used to launch the application and add a menu item in the required space.

For eg : When i installed gtkorphan( an application to find broken packages), i didn't find the same in the application menu .

You can add them manually for your further use :
1.Cick on System and Navigate to Main Menu
System > Preferences > Main Menu
2.You will have a screen where you can add a new launcher for the application with the " New Item " option on the right hand side.
3. When you click the same , you will have the following options and drop downs mentioned.

Type :Application 
Name : gtkorphan ( give the name you want it to be seen as )
Command : This is the only thing you have to figure out. The command part as i figured out is the command in terminal required to launch the app .
In this case being "gtkorphan"
4.You can submit the ok button and Voila you have the item added in the menus.


If there was any mistakes in what i mentioned here , please correct me . A newbie too ;)

---

### Post by LewRockwell on 2009-08-20
System > Preference > Main Menu

.

---

### Post by Copernicus1234 on 2009-08-20
If it doesnt appear in the menus, the locate command is great for finding stuff. It will list every file name containing the word you type.

---

