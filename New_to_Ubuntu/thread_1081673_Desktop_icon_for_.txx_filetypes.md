---
title: "Desktop icon for .txx filetypes"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by goldgin on 2009-02-26
Hello,

Short: 
I would like gnome/nautilus to display my own icon for .txx files

Long:
I have made an application that makes .txx (my own kind of) files. I have managed to associate these files with my application (double-clicking opens them with MY app). So I know a lot about mimetypes, xxx.desktop files etc...

The problem is that these files have the default plain-text icon associated with them. I have been struggling to find a way to change the icon of these files to be my own icon. I know I can right-click on every file and set it manually but it's not the correct solution.

Last thing I've tried was make another .desktop file under /usr/share/mimelnk but no joy. I think I have to rebuild something there in order to work... some command similar to update-mime-database perhaps?

I think people that make .deb packages might also know...

Help :cry:

---

### Post by Ripose on 2009-02-27
I don't know the whole process but, all icons are stored as .svg type, look in /usr/share/icons/gnome/scalable/mimetypes for examples.

---

