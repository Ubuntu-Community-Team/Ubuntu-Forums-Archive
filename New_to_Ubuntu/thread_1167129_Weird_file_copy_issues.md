---
title: "Weird file copy issues"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by PureLoneWolf on 2009-05-22
Hi all

I finally moved away from WUBI and to a full blown Ubuntu install.  Everything is fine, I can access and write to my (filled with data) NTFS drives/partitions as I need to.

I would like to move my old "My Documents" folder across to my spangly new ext3 home partition, and this is where my issue starts.

The files are currently in /dev/sdb1/My Documents - This is an NTFS formatted partition.  I can read/write and do what I want as expected.  When I copy a subfolder (I don't want everything) to my /home/me/Documents I can see it, I can create new folders but, if I try and launch a document (say, a text file), it won't launch.  

I went into properties and noticed that Text Editor was selected but not available with a right click.  All of the file permissions were turned on and my username was the owner.

Would anyone have any ideas?

Thanks

---

### Post by jerrrys on 2009-05-22
if i understand this correct...you are trying to x-fer from NTSF to ext3 and don't think thats possible...may stand corrected on this one...

---

### Post by PureLoneWolf on 2009-05-22
I am not sure what you mean by "not possible" - Certainly I can copy/paste the files over to the ext3 partition.

If this were true, wouldn't that imply that there would be almost no way to move away from NTFS.  Unless copying from FAT32 was possible, for which I would need another drive as I don't have enough spare space for a FAT32 partition.

Thanks

---

### Post by oldos2er on 2009-05-22
Do you get an error when trying to look at the text file? I'm guessing gedit is getting confused on its location because there's a space in the name "My Documents".

 Also you might want to consider mounting the drive somewhere other than /dev.

---

### Post by PureLoneWolf on 2009-05-22
Sorry, I should be a little more clear.  /dev/sdb1 is mounted as /mnt/sdb1 and I moved over a subfolder of My Documents (called Shrooms) to /home/me/Documents/ - I performed the move via Nautilus cut/paste and there were no errors.

If I try and double click a text file (called scripts.txt) nothing happens at all.

After that happened, I cut/pasted the folder back to it's original location and was able to launch the text file as expected through double clicking, I made no changes to the files/permissions etc in either direction.

Thanks

---

### Post by HeirPixel on 2009-05-22
Is it possible that you only pasted a *reference* to the original file? Perhaps try ```
mkdir /home/me/Documents/Shrooms && mv /mnt/sdb1/My\ Documents/Shrooms/* /home/me/Documents/Shrooms/*
``` in terminal and see if that solves the problem.

---

### Post by PureLoneWolf on 2009-05-24
I think it is permissions related.  All of my NTFS drives are mounted under /mnt, so that I can hide the volume icons that appear on the desktop.  When I check permissions on an NTFS stored file, everything is 777 and the owner/group is root.

When I copy to my home partition, everything becomes owned by me (as hoped), but stays as 777 (ie with the execute flag).  Ubuntu treats files with an execute flag differently on ext3 than on NTFS from what I can see.

Is there a (preferably GUI based) tool that will copy a folder (or group of) along with all of their sub-folders and files, and also allow me to set default permissions for the destination?  So I could copy/paste but make sure that they execute flag is removed from files.

Many thanks

---

