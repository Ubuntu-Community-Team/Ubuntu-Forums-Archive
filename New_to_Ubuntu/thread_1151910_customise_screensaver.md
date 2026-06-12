---
title: "customise screensaver"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by chipppy on 2009-05-07
I want to customise the screen saver.  I want to use my pictures instead of one of the normal screensavers.

unfortunately I am using Mythbuntu 9.04 and therefore i have all my picture stored in the mythtv/...../pictures folder so that they can be used via the mythtv system and not the normal pictures folder that the screensaver has an option for.

Anyone know how to customise screensaver to use my mythtv/..../pictures folder??

cheers
chipppy

---

### Post by cariboo on 2009-05-07
If you have nothing in the Pictures directory, just delete it and create a sym-link in your home directory to your pictures directory eg:

```
sudo ln -s /mythtv/..../pictures Pictures
```

You have to use the full path to the pictures directory

---

### Post by kelbizzle on 2009-05-07
I'm thinking you can replace the folder that the screensaver uses with a symbolic link or symlink to the folder where your pictures are stored. I would read a little more if I were you about symlinks. The command would look somthing like this. 

> sudo ln -s  /mythbuntu/.../screensaverpics/ /mythbuntu/.../yourpictures/



Edit: Yea what he said.

---

