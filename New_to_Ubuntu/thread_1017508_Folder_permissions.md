---
title: "Folder permissions"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by gzav on 2008-12-21
Hi all,

Using Xubuntu 8.1, i'm plugging an external HDD with all my documents. But, when i save a file from the internet in the main ubuntu folder and then when i try to copy-paste it in a folder in my HDD, i can't do it, ctrl+v or right-click and paste doesn't work...

I'm guessing it's a problem of permissions, what should i do to change them?

Thanks!

---

### Post by ibizatunes on 2008-12-21
go the terminal and enter ```
gksudo nautilus
```   - enter your pword

This will open nautilus as root, and you can copy and paste

You can now go to any folder and change it's permissions so you can open it's files or drag and drop it's contents when you are a user. Just right click on the folder to bring up the options menu. Then select the 'permissions' tab. You can then check of the tabs for 'others' or 'group'. If you are the only one using your computer and you want full access, you can check them all off. If you don't want other people to have access, be selective. Also don't change the permisions on system files like root and usr. They need to be root.

---

### Post by gTinker on 2008-12-21
[QUOTE=gzav]Using Xubuntu 8.1, i'm plugging an external HDD with all my documents. But, when i save a file from the internet in the main ubuntu folder and then when i try to copy-paste it in a folder in my HDD, i can't do it, ctrl+v or right-click and paste doesn't work...

I'm guessing it's a problem of permissions, what should i do to change them?[/QUOTE]

ibizatunes, answered your question correctly but you may not have asked the right question. 

The filesystem has the permissions it has for good reasons, a normal user should by default have the necessary permissions for locations where they should be able to save files. The situation you describe could also be related to how the ext drive is mounted, maybe it's mounted read only. 

It would have been good if you had posted the exact error message you received and more detail (like what you mean by "main ubuntu folder"). 

Just changing permissions on folders without being knowledgeable about what you are doing can introduce security issues. Occasionally, it can cause a system to stop working. 

Just one more piece of advice to consider.

---

