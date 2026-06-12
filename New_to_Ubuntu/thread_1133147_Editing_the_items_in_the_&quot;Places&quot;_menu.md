---
title: "Editing the items in the &quot;Places&quot; menu"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by Thurgood Stubbs on 2009-04-22
In the "Places" menu there is by default links to Documents, Music, etc.  However, I still have my files on the Windows section of my drive and don't want to move them so that when I need to go into Windows, I can get to them.  Is there a way to edit these links to folders so instead of pointing to the system default, I can set them to the folders I am using?

---

### Post by steve101101 on 2009-04-22
i dont know but you can always make a shortcut on the desktop to the host folder.

---

### Post by Seq on 2009-04-22
Yes, the file is called ".config/user-dirs.dirs".

Ubuntu will automatically update those directories if you move them in nautilus (I created a Media folder and moved several within). You will probably just want to edit the file directly, though.

You may need to log out and back in for it to take effect (I'm not sure if the stuff responsible watches the file, or what to poke to tell it to update).

---

### Post by Thurgood Stubbs on 2009-04-22
> **steve101101 said:**
> i dont know but you can always make a shortcut on the desktop to the host folder.

I have that already.  I was hoping to get something in the Places menu  because it is always there on my screen as opposed to having to go to the desktop to get at a link to my "actual" home folder.

---

### Post by Thurgood Stubbs on 2009-04-22
> **Seq said:**
> Yes, the file is called ".config/user-dirs.dirs".

Ubuntu will automatically update those directories if you move them in nautilus (I created a Media folder and moved several within). You will probably just want to edit the file directly, though.

You may need to log out and back in for it to take effect (I'm not sure if the stuff responsible watches the file, or what to poke to tell it to update).

This seems like what I am looking for.  How do I get to/edit this file?

---

### Post by steve101101 on 2009-04-22
```

sudo gedit /.config/user-dirs.dirs

```

---

### Post by Thurgood Stubbs on 2009-04-22
Thanks.  When I get there I just have a blank file.  What would I need to do to change where the Places links link to?

---

### Post by Thurgood Stubbs on 2009-04-22
This is still unresolved.  Could someone pickup where steve left off?

---

### Post by Ms_Angel_D on 2009-04-22
All you have to do is open nautilus (file manager) To say your home folder then select bookmarks -> Edit Bookmarks, You can make these links point to where ever you like. You can even add more bookmarks or remove the ones you don't want.

Just go to a folder you want to add and select Bookmarks -> Add Bookmark


I hope this helps.

Angel

---

### Post by Thurgood Stubbs on 2009-04-22
> **MetalHellsAngel said:**
> All you have to do is open nautilus (file manager) To say your home folder then select bookmarks -> Edit Bookmarks, You can make these links point to where ever you like. You can even add more bookmarks or remove the ones you don't want.

Just go to a folder you want to add and select Bookmarks -> Add Bookmark


I hope this helps.

Angel

Worked perfect.  Thanks.

---

### Post by Ticketoride on 2009-04-22
From ---> [https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")
> The third - simple- method is to install the pysdm package (in Gutsy) and then use System-Administration-Storage Device Manager without any manual editing of the fstab file ...
Use the Third Method, as its the easiest to mount your Drives.

Then go into your /media Folder and Drag the "Drive Folder" to the left Pane in Nautilus, or as mentioned above, "Add as Bookmark".

Then you'll have our Drive/Folders available as an Item in your "Places" Menu at Boot up Time too.

---

### Post by Paqman on 2009-04-22
> **steve101101 said:**
> ```

sudo gedit /.config/user-dirs.dirs

```

Please use gksudo for graphical apps. That command would be:

```

gksu gedit /.config/user-dirs.dirs

```

---

### Post by Seq on 2009-04-22
> **Paqman said:**
> Please use gksudo for graphical apps. That command would be:

```

gksu gedit /.config/user-dirs.dirs

```

In this case, use neither. The file is owned by the user. Also, the file is within the user's homedir. I should have been a bit more verbose.

Press alt+F2 and run this command:

```
gedit .config/user-dirs.dirs
```

---

