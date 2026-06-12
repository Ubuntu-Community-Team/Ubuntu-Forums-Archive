---
title: "Change Folder Permissions for ALL folders Under Folder"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by teh_yodeler on 2009-01-25
I have a folder called "Docs."  Under that are all kinds of other folders such as "Pictures," "Music," etc.

Problem is "root" is the owner.  My name is "compaq"

If I use ```
gksudo nautilus
``` I can right click, >>> Properties, >>>Permissions, and change the owner to "compaq."  However this does NOT change the permissions for folders below!  Only the folder I am currently in!

I have hundreds of stupid little folders that I am painstakingly entering only to change their permissions.

Is there ANY way to change the owner for the entire "Docs" folder, including all folders beneath it?  

I did click "Apply Permissions to Enclosed Files," but that didn't do anything.

If someone can help that would be great.  I've been googling since yesterday and all I can find it advice on the gksudo method and then click on permissions... which will take me years, and wear out my mouse finger.

Linux is about nifty command-line shortcuts, right?  Does anyone have one?

Thanks!!

---

### Post by taurus on 2009-01-25
Open a terminal, Applications -> Accessories -> Terminal, and change to the directory where Docs is located.  Then, change the ownership of Docs and everything under it from root to your login name, compaq.

```
sudo chown -R compaq:compaq Docs
ls -la
```

---

### Post by teh_yodeler on 2009-01-25
Thanks taurus, I'm about to walk out the door, but I'll try this when I get home.

I'd mark this "Solved" if I could! :p

---

