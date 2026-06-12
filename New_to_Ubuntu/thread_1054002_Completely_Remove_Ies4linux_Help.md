---
title: "Completely Remove Ies4linux Help"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by NorthWesterUK on 2009-01-29
Hi, I installed IE6 yesterday through ies4linux so i could install an activeX plugin to watch a football match, i didnt succeed with installing the activeX plugin!

My question is how do i remove all the files and folders that i installed!

I ticked the install flash player 9 box when installing IE6!.

Then i got prompted to install flash player 10 when i visited a site and without thinking checked the box and installed.

I have already followed the instructions on the ies4linux site...removed  .ies4linux folder  i have looked in the ~/bin for the executables but could not find any!.

Then when i browse C:\ drive trough WINE there are all sorts of files i think that ies4linux has installed...but dont know which ones to remove!.

Any help would be appreciated

Thanks

---

### Post by jgoguen on 2009-01-31
```
rm -r ~/.ies4linux/
```
That command will remove the folder IEs4Linux was installed to (and all the files it downloaded, and all the files it installed, and all the files it created while using it).  Menu/Desktop entries (if you created them) aren't removed by this, you have to remove them separately, but the command above will take care of your IEs4Linux installation.

---

### Post by NorthWesterUK on 2009-02-01
Ok thank you for your help jgoguen

---

