---
title: "Want Default Panel Back"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by flutti-tutti on 2008-12-30
My default panel at the top somehow disappeared from the desktop, Ubuntu 8.10.  I tried to recreate it, but could not find an item of a wireless signal indicator among the selections of "Add to Panel".  I wanted it back, because it was so convenient.
Please help.  Thanks.

---

### Post by nothingspecial on 2008-12-30
I think its part of Notification area. Right click on your panel and click add to panel then look for it in there.

---

### Post by -kg- on 2008-12-30
I have one of these applications on my LaunchBar, and when I pulled it up it said it was "Network Manager" [http://www.gnome.org/projects/NetworkManager/]("http://www.gnome.org/projects/NetworkManager/")

I pulled up the "Add To Panel" list and Network Manager wasn't listed, though Network Monitor was (a different icon, though).  This may be because I already have it installed, so look and see if you have a "Network Manager" in your "Add To Panel" list.

In the mean time, I'll look and see what I can find out.

---

### Post by cdtech on 2008-12-30
Here is a method for restoring your panel to default:

Press ALT+F2 and in the run dialog box, type "gnome-terminal" then click on Run.

When the Terminal window opens, enter the command:
```
sudo apt-get install gconf2
```
```
gconftool-2 --recursive-unset /apps/panel
```
Then enter:
```
rm -rf ~/.gconf/apps/panel
```
And enter one more command:
```
pkill gnome-panel
```
This will retore to its original state. Be sure to backup your config files if you modify the panel, the files can be found here:
```
~/.gconf/apps/panel
```
Hope this helps ya.........

---

### Post by -kg- on 2008-12-30
And if that doesn't help, you might be able to find an answer [in this thread,]("http://ubuntuforums.org/showthread.php?t=965821&highlight=network+manager+disappeared") which is basically the same problem you're describing.

---

### Post by flutti-tutti on 2008-12-31
Thank you very much for your responses.

cdtech's codes restored the default panel.
thanks!!

---

