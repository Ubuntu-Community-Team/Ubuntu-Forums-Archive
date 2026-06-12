---
title: "Files on windows box open with no content"
date: 2014-07-03
forum: Networking &amp; Wireless
---

### Post by open4junk on 2014-07-03
I am using xubuntu 14.04 on a laptop that is wirelessly networked with a window 7 machine where shared folders have been created. Problem: when I open a document file from the shared folder, there is no content. However, if I copy that file to xubuntu, say the documents folder, and open it, voila content is there. This seems to defeat the purpose of having the shared folder. I have searched numerous places and have found no satisfactory solution. I have even done a clean re-install of xubuntu thinking maybe there was a glitch but that was not the answer.  If you can suggest a course of action, I would appreciate it.

thx

---

### Post by bashiergui on 2014-07-14
The issue is likely permissions. In Xubuntu right click on the shared folder, choose "properties", click on the "permissions" tab. Under "owner", "group", and "others", change the folder access to "create and delete files". Change "file access" to "read and write" in all three areas. Click close. 

Here are some screenshots
[http://askubuntu.com/questions/373292/change-directory-subdirectory-folder-and-file-permissions-in-ubuntu-gui](http://askubuntu.com/questions/373292/change-directory-subdirectory-folder-and-file-permissions-in-ubuntu-gui)

Or you can use the terminal by typing ```
chmod -R 777 path/to/shared/folder
```

---

### Post by open4junk on 2014-07-15
> **open4junk said:**
> I am using xubuntu 14.04 on a laptop that is wirelessly networked with a window 7 machine where shared folders have been created. Problem: when I open a document file from the shared folder, there is no content. However, if I copy that file to xubuntu, say the documents folder, and open it, voila content is there. This seems to defeat the purpose of having the shared folder. I have searched numerous places and have found no satisfactory solution. I have even done a clean re-install of xubuntu thinking maybe there was a glitch but that was not the answer.  If you can suggest a course of action, I would appreciate it.

thx

Thx but I cannot change the shared folder permission settings.

---

### Post by bashiergui on 2014-07-16
> **open4junk said:**
> Thx but I cannot change the shared folder permission settings.
Why? What's preventing you from changing permissions?

---

