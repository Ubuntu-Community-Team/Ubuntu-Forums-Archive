---
title: "unable to add/delete files from memory card"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by _King_Q_ on 2008-12-02
i am un able to delete any files or folders from my memory card i tried using nautilus but that was no help i have no damn clue what to do and now when i open my memory card from my desktop it wont even show me the files saying i dont have permission to do so

---

### Post by Michael.Godawski on 2008-12-03
open up Nautilus with 

```
gksudo nautilus
```

Warning: you have root privileges so be cautious and act wisely.

Navigate to the place where your memory card (or usb stick ?) is usually mounted. That can be on the Desktop or in the /media folder. Right click on it, go to Properties and change the owner to your user-name and give you the permission to write and read the files. I don't know if this is a permanent solution though...

---

