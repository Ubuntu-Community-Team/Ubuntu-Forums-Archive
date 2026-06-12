---
title: "Xampp Help"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by ineedhelpman on 2009-02-06
Sorry if this is in the wrong place, i have just downloaded xampp and everything seems to work fine but i read in another forum that to view my php pages i would have to put them in my htdocs folder well when i go to that folder i can not create a folder or copy my php files into the htdocs folder, does anyone have any ideas what could be wrong? Thanks!!

---

### Post by cariboo on 2009-02-06
When creating directories or copying files into a directory you don't own, you need to use sudo eg:

```
sudo mkdir <dirname>
```

and

```
sudo cp filename /path/to/dir
```

or to do it graphically press Alt-F2 and type:

```
gksu nautilus
```

the above command will open nuatilus (file manager) as root. This will allow you to do the same as the above to commands.

Jim

---

