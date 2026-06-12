---
title: "How to get administrative tools installed ?"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by ESDEEM on 2011-04-21
I installed [Ubuntu [SIZE=2][COLOR=Red]mini[/COLOR][/SIZE] 10.04 (64 bit )]("https://help.ubuntu.com/community/Installation/MinimalCD") and I'm missing some administrative tools under "System" like "Users and Groups"....How to get all the administrative tools for Lucid Lynxs?

I have ...
*Log file viewer
*Login Screen
*Software Sources
*Synaptic Package Manager
*System Monitor
                  in the System => Administration......
Want to get the rest....!
thanks !

---

### Post by Tamlynmac on 2011-04-21
First you should probably check the "edit menu" function to assure the  apps. you want - just aren't turned on. Right click on the panel menu and  select "Edit Menus". A new window will open called Main Menu. On the left  side under "Menus", select "system/administration". An items listing  will show up on the right side window. Search for items that your  missing and if there, make sure there's a check mark in the box to the  left of the item. Odds are the apps are listed in the edit menu, but  just aren't checked to turn them on in your panel menu.

If the items your looking for don't show up on the right side of the  window left click on "Add Item" in the upper right hand corner. Another  smaller "Create Launcher" window will open.

Type: Application
Name:  As you defined
Command: For User and Groups;  (click the browse button) and find  "filesystem/usr/bin/users-admin" double click on this file and it will  add it to the create launcher command. Or just type "users-admin" into the command box. On the left side of the create  launcher window an icon should appear. If you don't like the icon left  click on it and choose an alternative. When done select "OK" at the  bottom of the create launcher window and your new launcher should appear  in the items listing. If so make sure that there's a check mark in the  box next to it and close the "Main Menu" edit window and your new  launcher should appear in the system/administration list of your panel  menu.

It's unnecessary to type anything in the "Comments" box of the create launcher window. 

If you need help locating the commands for any additional items in the system/administration menu, just post your request list here and I'll provide said locations/commands. Generally, they are listed in the "filesystem/usr/bin".

Good Luck & hope this helps.

---

### Post by ESDEEM on 2011-04-21
I browsed for....
> filesystem/usr/bin/users-adminbut could only find "users" instead of "users-admin"
[see this]("http://oi53.tinypic.com/2jb1udv.jpg")
I chose users but nothing happens when I click the launcher...
Need some help pls....

---

### Post by Tamlynmac on 2011-04-22
It appears (for what ever reason) that the "adduser" item was not installed or was removed from your system.

You can install the "adduser" from the Synaptic Package Manager or I  believe it's listed in the Ubuntu Software Center under System as "add  and remove users and groups". It's interesting that it wasn't  installed with the original installation, as I believe it's a default.

In Synaptic: Open it and select "ALL" on the left side of the window  then click on the Binoculars (toolbar) and type "adduser". Check the box  next to "adduser" when it shows up in the right side and click on apply  in the toolbar. If another box opens and ask to install other files,  just say ok. After the install I think you will either find it in your  menu or check the launcher you made and see if the "users-admin" file is  there and just change it in your launcher command box.

You can find other missing admin items in the Synaptic Package Manager. For example, Network tools are listed as net-tools.

Should you need any help finding additional menu items or what to search for in the Synaptic Package Manager, just ask.

Was this a custom installation?

---

### Post by ESDEEM on 2011-04-23
"users-admin" still not appearing...just only "users" file is there...   :(

> Was this a custom installation?Yup....I installed Ubuntu minimun (15mb) to get only basics....

While installing,on the partitioning step,I chose
> /instead of 
> /rootas the mount point..
Is it a reason not for having the admin-user thing...?
I think so as the following appears in terminal when I try to add an user as I have no other application to do so
> esdeem@esdeem:~$ adduser test
adduser: Only root may add a user or group to the system.
If it is the reason tell me how to correct it....
thanks in advance !

---

### Post by ESDEEM on 2011-04-24
great puzzle solved...   :)
just installed
> Gnome system-tools
through Synaptic and got the Users and Groups app.....
Thanks so much for the help......:P:P:P:P:P

---

