---
title: "[SOLVED] Putting wine apps into AWN"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-26
How can I create a shortcut of a wine app (for example, photoshop.exe) and place it in a dock such as AWN?

Also, I have to run programs such as Photoshop as root, so would placing it in AWN even be possible?

---

### Post by billgoldberg on 2008-12-26
> **adobrakic said:**
> How can I create a shortcut of a wine app (for example, photoshop.exe) and place it in a dock such as AWN?

Also, I have to run programs such as Photoshop as root, so would placing it in AWN even be possible?

First of, don't start programs with root that doesn't require it.

Simply link to the executable.

Go to your home folder and press "ctrl+h".

This will show the hidden folders.

Go to the ".wine" folder, then "drive_c", "program files" and then the folder where photoshop.exe is located.

In AWN, create a new launcher and use

```
gksudo wine /home/username/.wine/drive_c/program\ files/photoshopfolder/photoshop.exe
```

When a folder name contains a special character, like a space, put a "\" in front of it. 

That should do it.

---

### Post by adobrakic on 2008-12-26
I have to start Photoshop as root, otherwise I get an error and it doesn't open. :)

I'll try this and post back here though, thanks!

---

