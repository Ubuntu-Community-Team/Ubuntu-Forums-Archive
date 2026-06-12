---
title: "Music players trippling up my music?"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-18
Okay, 
this happened in Rhythmbox too.
I use banshee now.
As you can see in the screenshot there seems to be so many copies of each song. Viewing the properties only shows that every listing is the exact same file, so no, I don't have multiple copies in my library.
This also happens for artists.
I don't get why it's doing this?

---

### Post by Gp. on 2009-06-20
Bump, anyone?

---

### Post by FreewheelinFrank on 2009-06-20
Do you have the same files in different locations? Have you changed the location of your music library?

---

### Post by Gp. on 2009-06-20
Nope and Nope.
That's why I don't get it.
When I view the properties of every file that's the same, it shows the same location and file.

---

### Post by doug1212 on 2009-06-20
Hi,
I had a similar issue after altering tags and if I remember I had to delete the Rhythmbox database and rebuild.

I think the database is here:

```
~/.gnome2/rhythmbox/rhythmdb.xml
```

Doug.

---

### Post by Gp. on 2009-06-20
This is Banshee...:P

---

### Post by Gp. on 2009-06-20
How do I rebuild for banshee?

---

### Post by FreewheelinFrank on 2009-06-20
Find the database and delete it, or do a complete uninstall then reinstall.

I had the same problem with Rhythmbox, and did a reinstall- that *was* because I had the same files in different locations.

---

