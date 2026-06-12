---
title: "File System - Application data - Need some very basic information"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by KarenAK on 2009-04-30
I have installed the program Rainlendar. No sweat. Now I want to add a skin. Uhoh.

The installation instruction tells me to copy the files to the Rainlendar skin folder. Aha. 

Sounds easy enough. 

Except I can't find it.

Searched the internal hard drive for Rainlendar. It doesn't seem to exist. (Does the Search function search the subfolders too ? It doesn't say and there seems to be no option for it)

And while looking for it, the question pops up: Where is the Ubuntu equivalent to the Windows "application data" ? Some of it seems to be in my home folder. But not all of it.

Where are the program files ?  I looked through Places | File System but it really doesn't make much sense to me.

Can somebody either point me to a place where this is explained, in detail, in newbie-speak, in ex-windows-user-speak and/or just tell me where to copy those skin files ?

Thanks in advance for any help.

---

### Post by esodin on 2009-04-30
The application data does in fact reside in the home folder. It is however in hidden directories. A file or directory name that starts with a dot "." is hidden. You can unhide the files by hitting the "Ctrl" + "h" key or by selecting Show hidden Files" from the "View" menu.

Look oft the directory ".rainlendar"

---

### Post by Zeedok on 2009-04-30
> Where are the program files ?

Most of the configuration files for programs _are_ in your home directory - they are hidden though.  a directory that startd with "." like:
 
> .home

will be hidden in nautilus.  You can make them visible with CTRL+H

Good luck

---

### Post by KarenAK on 2009-04-30
ok, that is good to know !

Now I only need to find that introduction to the linux file system...but 'll find it...


thank you :-)

---

### Post by muteXe on 2009-04-30
[http://www.google.co.uk/search?hl=en&q=linux+file+system&meta=&aq=f&oq=](http://www.google.co.uk/search?hl=en&q=linux+file+system&meta=&aq=f&oq=)

Take your pick :)

---

