---
title: "Help saving lots of time"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by crazychipmonk on 2011-08-17
I have a bout fifty folders filled with music files, and i was wondering if there was a way to extract all the files without going into all the folders and doing a copy all then paste into a destination folder. if anyone could help it would be wonderful. 
Thanks

---

### Post by Neoncamouflage on 2011-08-17
I wanted to do the same thing with .iso files from my downloads folder.

```
for file in `find ~/Music`
do
if echo $file | grep ".mp3"
then
mv $file DESTINATION
fi
done
```

Replace Music with whatever main directory the folders are in, and if they aren't all mp3s then change that to .* for all files or specify exactly which types. Run it as a script or from the terminal.

Let me know how it goes.

---

### Post by fdrake on 2011-08-17
actually if you have file different from mp3  just skip line 3 & 4 
grep ".*" will look for termination * since is inside double quotes.

also instead of mv i 'd use cp -v just in case you dont loose files.

---

