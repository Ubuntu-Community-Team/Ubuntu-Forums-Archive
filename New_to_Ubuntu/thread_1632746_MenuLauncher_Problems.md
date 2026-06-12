---
title: "Menu/Launcher Problems"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by John_in_Tally on 2010-11-28
Hello All!
 
I'm using Ubuntu 10.10 Netbook Edition and what I'm trying to change is a couple of things concerning menus & launchers.
 
I've downloaded a .deb program (not from the Ubuntu repositories) which I've been able to install and run successfully. However, I can only run the program from the Terminal (as the root user) as it does not appear in the Applications Menu. I've tried right clicking the icon launcher (which just has an "?" icon) to install it there while the program is running, but I'm unable to do that. I've been able to do this for other programs I've used so I'm confused as to why I now cannot do this. I've also tried creating a menu item for the program using the Main Menu program, but I can't get it to appear in the Applications Menu.
 
So what am I doing wrong? Has it something to do with having to run the program as the root user, or is it something else?
 
I was also wondering if there is a way to delete the Files & Folder icon from the launcher (again if I right click on it it doesn't give me the option to remove it)? I like using the File Manager more than Files & Folder so to me it's just taking up space.
 
Thanks to anyone who can help me with these issues.

---

### Post by cariboo on 2010-11-29
The folders and files icon is hard coded into the panel, but if you just click and drag one of the other for example cheese, to the right, you should have the extra space for another icon.

If your application doesn't have a launcher in /usr/share/applications, you can use one of them as a template to create a launcher.

```
[Desktop Entry]
Version=1.0
Name=Empathy
GenericName=IM Client
X-GNOME-FullName=Empathy Internet Messaging
Comment=Chat on Google Talk, Facebook, MSN and many other chat services
Exec=empathy
Icon=empathy
StartupNotify=false
Terminal=false
Type=Application

```

---

