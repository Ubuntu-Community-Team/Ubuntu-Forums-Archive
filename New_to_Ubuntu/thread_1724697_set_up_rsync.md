---
title: "set up rsync"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by philipballew on 2011-04-08
i need to set up rsync to have where my external hd is a clone of my laptop harddrive. how can i do this and not backup the second partition on my external hd?

---

### Post by SeijiSensei on 2011-04-08
Use --exclude or --exclude-from.  Actually in most instances you'll want to exclude /proc as well.  I prefer --exclude-from since I've usually got a bunch of directories like /proc/ and /sys/ and types of files like *~ that I don't want to sync.  I just dump the "globs" in a file, each on a separate line.

There's also --one-file-system which will exclude all mounted devices.

---

### Post by seawolf167 on 2011-04-08
If I'm reading your post correct, you want your external hdd to be a clone of your laptop hard drive, right? 

If you are looking for a clone, you should (IMO) use [Clonezilla]("http://www.clonezilla.org") to image your laptop hard drive and store that image in your external hard drive.

If you are looking to simply mirror the (a) directory tree this is where you'd want to use rsync. An example command would be 

```
rsync -ruv --delete /source /destination
```

as said above, you can use --exclude to exclude locations, for lots more switches read up on the man page

```
man rsync
```

---

