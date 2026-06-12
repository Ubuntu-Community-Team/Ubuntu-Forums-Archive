---
title: "Whats crappening in Nautilus?"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by macabro22 on 2007-06-25
Can someone help me with this?

I am trying to access a network folder at my lab and I get the following message:

```
The filename "smb-workgroup-Publico" indicates that this file is of type "x-directory/smb-share". The contents of the file indicate that the file is of type "desktop configuration file". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "desktop configuration file", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 
```

Thats in Nautilus. After clicking ok, I can't open my files there.

I can access this folder without any issues using Konqueror.

Thanks

---

### Post by p_quarles on 2007-06-25
I don't know, but perhaps Nautilus is trying to add its own configuration file to a KDE-configured folder? 

One possible solution might be to get a Samba network browser. There are at least two in the repositories.

---

