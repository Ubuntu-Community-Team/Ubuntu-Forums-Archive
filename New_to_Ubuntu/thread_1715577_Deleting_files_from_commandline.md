---
title: "Deleting files from commandline"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by UpSignal on 2011-03-27
Hey guys, this might sound very noob. but i'm affraid of messing with my system, so i decided to ask first.

Mission: Delete all ".jpg" on "Music" folder.
 I know this is done using wildcards, but inside my music folder i have several other folders with bands name, then several folders with albuns name...so, i don't even know if this is possible. 
If something goes wrong and ubuntu deletes ALL the jpgs on my system, i think i'm gonna blow my head against the wall. :D
So, you guys know a way to do it?

---

### Post by sisco311 on 2011-03-27
You could use the find command. Check out this howto: [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)


You can list the files with:
```
find ~/Music -iname '*.jpg' -type f -print
```

Then you can use the gvfs-trash command to move them to the trash:
```
find ~/Music -iname '*.jpg' -type f -exec gvfs-trash '{}' +
```

If you are sure that find lists only the files you want to delete, then you can use its -delete option to remove them permanently:
```
find ~/Music -iname '*.jpg' -type f -delete
```

Be careful and if you have any questions, please feel free to ask.

---

### Post by UpSignal on 2011-03-27
> **sisco311 said:**
> You could use the find command. Check out this howto: [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)


You can list the files with:
```
find ~/Music -iname '*.jpg' -type f -print
```

Then you can use the gvfs-trash command to move them to the trash:
```
find ~/Music -iname '*.jpg' -type f -exec gvfs-trash '{}' +
```

If you are sure that find lists only the files you want to delete, then you can use its -delete option to remove them permanently:
```
find ~/Music -iname '*.jpg' -type f -delete
```

Be careful and if you have any questions, please feel free to ask.

Thanks so much man! Worked like a charm! 
cheers :D

---

### Post by sisco311 on 2011-03-27
You're welcome!

Don't forget to mark this thread as [SOLVED].

---

