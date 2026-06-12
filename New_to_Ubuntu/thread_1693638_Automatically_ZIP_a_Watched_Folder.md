---
title: "Automatically ZIP a Watched Folder"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by GaelicAU on 2011-02-23
Hi Guys.

I am new to Ubuntu (2 days) and having a lot of fun using SSH, Squid, Apache etc.

I've setup Dropbox to ferry documents to and from my office and am wondering if anyone can advise on the best way of doing this idea below via a script.

I want to watch a folder (/home/dropbox) and when a new folder gets copied into there, I want it to ZIP that folder (eg. MyFiles to MyFiles.ZIP) and then delete the original MyFiles folder leaving only the ZIP file.

Any help would be greatly appreciated.

---

### Post by aeiah on 2011-02-23
if you did it that way, you'd have to make sure the files had finished copying into dropbox first. it might be best to use nautilus-actions to create a right-click option for folders called (send to dropbox). this could call a command that just zips it and saves the zip to ~/dropbox.


command would be something like:
```
zip -r ~/path/to/dropbox/%f %M
```

that should work. %M means path of folder, %f is foldername. if those parameters dont work you'd have to put it in a script i guess

---

