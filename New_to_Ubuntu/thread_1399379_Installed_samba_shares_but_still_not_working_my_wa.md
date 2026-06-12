---
title: "Installed samba shares but still not working my way"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by degarb on 2010-02-05
I haven't yet figured out how automatically mount an xp share folder. In o office, if you want to use a xp share, you must first browse that folder.

I installed samba shares.  What do I need to do to get these xp folders to work on ubuntu without having to browse first?

---

### Post by degarb on 2010-02-05
Maybe I am missing some configuration, somewhere.

---

### Post by Morbius1 on 2010-02-05
There are three methods ( that I know about ):

(1) The Classic Method: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

(2) The GVFS Method : [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

(3) The Poor Man's Method:

Browse to your share as you always do then Bookmark it.

In Nautilus > Bookmarks > Add Bookmark

It will show up under Places on the left side panel of Nautilus. The next time you need it just click on the bookmark as if it was just another Place.

---

### Post by degarb on 2010-02-05
The classic method is too hard,  no way I am doing that.

method 2 makes alot of sense.  basically make a bat file and add to startup.  

Method 3 is reason I am complaining.

  However, method 2 will only mount 1 of the three shares I need.  It mounted two once, but not again.   The two I am having trouble with are the ones I can write to and read from.

---

### Post by degarb on 2010-02-05
gvfs-mount smb://intellig-wbv5h2/SharedDocs2   a read and write share.

this works in terminal, but not in sh file, even though executeable.

while gvfs-mount smb://intellig-wbv5h2/videos  works.  This folder is read only.

---

### Post by Morbius1 on 2010-02-06
> However, method 2 will only mount 1 of the three shares I need.There is one quirk about the gvfs method that I failed to mention and may or may not be responsible.

If you want to automount multiple remote shares you would think that putting the gvfs-mount commands in one script would be more efficient than multiple scripts. Problem is it doesn't work under all circumstances.

For example, let's say I create a script that mounts two directories:
```
#!/bin/sh
gvfs-mount smb://192.16X.X.XX/shared1/directory
gvfs-mount smb://192.16X.X.XX/shared2/directory
```If the mount to "shared1" fails for whatever reason both mounts will fail. If the mount to "shared2" fails "shared1" still mounts. The script is halted when it encounters an error. A more elaborate script is probably the right answer but what I do is simply create multiple scripts. If one fails it won't impact the other.

The only other thing that I can think of concerning the read/write share is authentication. Does access to that WinXP share require a password? If so, did you do the "remember forever" part of the HowTo concerning username and password? It's just that it sounds like a WinXP authentication or permissions problem, not a gvfs problem.

---

### Post by degarb on 2010-02-06
No password.   

I am baffled I can not mount a folder in a sh file (executable).  But can by pasting same code into the terminal.

Furthermore, I have seen the second of the three mount in bat file twice, but not on other runs.

I did try making separate sh files.  I have not tried mounting by ip, rather than computer name. I will when I get access to the computer later.

---

