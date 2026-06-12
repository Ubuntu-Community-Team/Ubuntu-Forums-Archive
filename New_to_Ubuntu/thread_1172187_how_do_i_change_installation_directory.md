---
title: "how do i change installation directory"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by rohan4b on 2009-05-28
ok so i am new to this whole linux thing. i have decided to switch from windows. how do i select where to install my apps. any help would be greatly appreciated.

---

### Post by kpkeerthi on 2009-05-28
Most the stuff will go to /usr/bin and /usr/lib. Unlike the other OS, the file system hierarchy is pretty standard in UNIX/LINUX. For more info, see [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/")

When you install a package (a deb file in Ubuntu), the package contents go to a set of pre-determined locations in the filesystem. This information is sort of hardwired in the package and cannot and is not adviceable to change.

For beginners, I suggest you spend some time reading 
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)
[https://help.ubuntu.com](https://help.ubuntu.com)
and save yourself some frustration.

---

### Post by Andre Murphy on 2009-05-28
Ah I understand now I wondered that as well !! So a follow up question. If you install an app and it doesn't create an icon in the menu is it possibe to go to the bin or lib directory and create a link in the menu?
 Ta
 
Andre

---

### Post by kpkeerthi on 2009-05-28
Yes. Right-click on "Applications" on the top-panel and select "Edit Menus". 

Select the menu category and drill down to where you want a new menu item created. Now, select Create New Item, and specify the Name, Command, Description and a menu icon. You will be all set.

If your application is /usr/bin/my-fav-app, you would specify that under "Command"

---

### Post by rohan4b on 2009-05-28
i only want to change the location as os is installed on an ssd only 4gb big.

---

### Post by LowSky on 2009-05-28
what is great about Linux is that you can create partitions during the installation so lets say an application puts its files in your /home directory, creating a separate home on another drive will save space for root better known as /. you can do the same for  /usr as well, heck any folder location.

---

### Post by Andre Murphy on 2009-05-28
> **kpkeerthi said:**
> Yes. Right-click on "Applications" on the top-panel and select "Edit Menus". 
 
Select the menu category and drill down to where you want a new menu item created. Now, select Create New Item, and specify the Name, Command, Description and a menu icon. You will be all set.
 
If your application is /usr/bin/my-fav-app, you would specify that under "Command"
 
Ta will have a go with that 
 
Cheers
 
Andre

---

