---
title: "pointing to different volumes.. for documents / music / pictures etc...."
date: 2009-11-15
forum: New to Ubuntu
---

### Post by vikman on 2009-11-15
I have this setup - 4 partitions
c:  with windows vista   40GB
/windows fat32 with 100GB
/             ext4 with 15GB
/swap 3GB

my /home is within / 
I want to have my /music /documents /pictures  reside in /windows and have /home point to them... does this make sense? is it possible?

---

### Post by coffeecat on 2009-11-15
Yes it does. Yes it is. :) You need to have /windows mounted at bootup with an entry in /etc/fstab for this work, otherwise you'll get a load of broken symlinks in your home folder - at least until you mount the partition through the Places menu.

OK. Open a Nautilus file browser for the /windows partition. Create a folder - let's use "Music" as an example. Right-click on the new folder and choose 'Make Link'. That will create a symlink folder called "Link to Music", which is just a symlink in the same location as its destination. Now simply drag and drop "Link to Music" to your home folder and another symlink folder will be created there which links to the original /windows/Music. When you double-click on it you will be able to access anything in /windows/Music.

Now delete the original "Link to Music" in /windows - it is superfluous now. And you can rename "Link to Music" in your home folder if you want.

The quicker way of doing this is in the terminal. So long as you have already created the /windows/Music folder, open terminal and while you are "in" your home folder...

```
ln -s /windows/Music Music
```Now repeat for 'Videos', 'Pictures', whatever you want.

By the way, I suggest you rethink using FAT32 for your /windows partition. NTFS is much more robust and allows files greater than 4GB. You've got Vista to repair it if the journal ever gets corrupted. If FAT32 gets corrupted, you could very well lose your data. And NTFS read/write is reliable in Ubuntu.

---

### Post by vikman on 2009-11-15
It worked!!!. thank you.. also changed to NTFS. However.. now my desktop folder is missing and even when I create a desktop icon in my main user directory nothing happens. From the filebrowser window- clicking on the desktop symbol takes me to my main user directory.... how do I fix that?

---

### Post by coffeecat on 2009-11-15
A quick google showed that you are not alone. Other people have had the desktop folder disappear, but I didn't have time to see why or whether there was a fix there. I'll have a proper look later and post back if I can.

Very odd. Creating a few symlinks wouldn't do this, but I don't understand why it has happened.

In the meantime check Trash/Deleted Items. Make sure it hasn't got moved there somehow.

---

### Post by coffeecat on 2009-11-15
Two more things to look for if your desktop folder is not in the trash. These are both in your personal settings so they should not have changed spontaneously, but it's worth checking.

1 - Press alt-F2, type and run 'gconf-editor' (no quotes). Go to apps > nautilus > preferences. Make sure the line 'desktop_is_home_dir' is not selected.

2 - Open your home folder and ctrl-H to show hidden files. Open the '.config' folder and then open the user-dirs.dirs file. Be careful not to change anything. Check that the first uncommented line says:

> XDG_DESKTOP_DIR="$HOME/Desktop"

---

