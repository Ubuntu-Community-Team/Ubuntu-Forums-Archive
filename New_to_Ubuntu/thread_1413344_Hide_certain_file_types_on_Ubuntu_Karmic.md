---
title: "Hide certain file types on Ubuntu Karmic"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by noran on 2010-02-22
Hello,

I would like for nautilus to hide files of a certain type, in particular Windows .ini and .db files. Any way to do this?

Thanks in advance, :)

---

### Post by TenPlus1 on 2010-02-22
As far as I'm aware the only files that are hidden begin with a period... ".hello" the hidden file attributes on Windows dont work on linux...

---

### Post by mikechant on 2010-02-22
It's maybe not exactly what you want, but the method discussed in this thread
[http://ubuntuforums.org/showthread.php?t=789684](http://ubuntuforums.org/showthread.php?t=789684)
allows you to hide files permanantly using a 'right-click,hide file' action - it adds the filename to the special .hidden file.

If you've only got a relatively small number of folders then it probably won't take long, and if you want to hide the same files in every folder you can probably copy the .hidden file around.

Note the .hidden file can also be used to hide entire folders.
I don't know if it supports generics like *.db - I assume not since noone mentions it but it might be worth trying.

---

### Post by theozzlives on 2010-02-22
I just delete them. Windows files have no business on my Linux system.

---

### Post by noran on 2010-02-22
Yes but the problem is, I have a shared partition between Ubuntu and Windows. Even if I delete them from Linux, whenever I start Windows all the desktop.ini and thumbs.db files are created again. I would like to find a way for nautilus to automatically hide them, they're really annoying :(

---

### Post by mikechant on 2010-02-24
If it's really just these two specific files that are annoying you (desktop.ini and thumbs.db) then the .hidden file (as per my previous post) definitely sounds like the way to go. You just need a .hidden file containing these two filenames on seperate lines, and a means of copying this file recursively to all folders on your windows partition.

So if your windows partition was mounted as /mnt/windata in Ubuntu, create the .hidden file as per above in /mnt/windata and run the command
```
find /mnt/windata -type d -exec cp /mnt/windata/.hidden {}/ \;
```

This command was based on the following post
[http://www.unix.com/unix-dummies-questions-answers/45096-copy-single-file-multiple-directories.html#post302144896](http://www.unix.com/unix-dummies-questions-answers/45096-copy-single-file-multiple-directories.html#post302144896)
and I have not been able to test it as I am not at my Ubuntu PC at present.

If you added new windows folders (or add more filenames to .hidden) and wanted to redo the command you would probably want to add the -f flag to the cp command so it would overwrite all the existing .hidden files automatically.

You might need to use 'sudo' for these commands depending on the permissions you've set up for the windows filesystem.

---

### Post by KeLa on 2010-02-24
One thing to try is to disable "Remember each folder's view settings" in windows
This can be found from Explorer menu "Tools" -> "Folder options" -> "View"
I use this method and don't have any desktop.ini or thumbs.db files on my system.
Also you can try to disable "Do not cache thumbnails" setting in same place.

---

### Post by noran on 2010-08-20
> **mikechant said:**
> If it's really just these two specific files  that are annoying you (desktop.ini and thumbs.db) then the .hidden file  (as per my previous post) definitely sounds like the way to go. You just  need a .hidden file containing these two filenames on seperate lines,  and a means of copying this file recursively to all folders on your  windows partition.

So if your windows partition was mounted as /mnt/windata in Ubuntu,  create the .hidden file as per above in /mnt/windata and run the command
```
find /mnt/windata -type d -exec cp /mnt/windata/.hidden {}/ \;
```This command was based on the following post
[http://www.unix.com/unix-dummies-questions-answers/45096-copy-single-file-multiple-directories.html#post302144896](http://www.unix.com/unix-dummies-questions-answers/45096-copy-single-file-multiple-directories.html#post302144896)
and I have not been able to test it as I am not at my Ubuntu PC at present.

If you added new windows folders (or add more filenames to .hidden) and  wanted to redo the command you would probably want to add the -f flag to  the cp command so it would overwrite all the existing .hidden files  automatically.

You might need to use 'sudo' for these commands depending on the permissions you've set up for the windows filesystem.


Sorry for the very late reply. I finally got around to trying this out and it works. The command also executes faster than I expected. I was also able to hide the Windows Recycle Bin folder.

Thanks so much.

---

