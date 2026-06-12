---
title: "Fixing the duplication"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by TironN on 2009-11-22
Hey guys,
I have about 600 music songs including some identical doubles. Now I simply want to remove one of these to fix all these doubles. Is there a program to help?
Thanks

---

### Post by BenAshton24 on 2009-11-22
fdupes should do the trick... just install fdupes and run the following:

```
fdupes -r ./music_folder | xargs rm -f
```

I would recomend just running the following first, just to make sure everything is working

```
fdupes -r ./music_folder > dupes.txt && gedit dupes.txt
```

home of fdupes: [http://netdial.caribe.net/~adrian2/fdupes.html](http://netdial.caribe.net/~adrian2/fdupes.html)

good luck :)
Ben.

---

### Post by TironN on 2009-11-22
the gedit gave me all I need but I got this in terminal when running it:

```
fergus@fergus-desktop:/media/bigd$ fdupes -r ./Music | xargs rm -f
xargs: unmatched single quote; by default quotes are special to xargs unless you use the -0 option
rm: cannot remove `./Music/Dropkick': Is a directory
rm: cannot remove `./Music/Dropkick': Is a directory
rm: cannot remove `./Music/Dropkick': Is a directory
rm: cannot remove `./Music/Dropkick': Is a directory
rm: cannot remove `./Music/Dropkick': Is a directory
rm: cannot remove `./Music/Dropkick': Is a directory
rm: cannot remove `./Music/Dropkick': Is a directory
rm: cannot remove `./Music/Dropkick': Is a directory
rm: cannot remove `./Music/Dropkick': Is a directory
rm: cannot remove `./Music/Dropkick': Is a directory
rm: cannot remove `./Music/Dropkick': Is a directory
rm: cannot remove `./Music/Dropkick': Is a directory
rm: cannot remove `./Music/Dropkick': Is a directory

```

What should i do?

---

### Post by BenAshton24 on 2009-11-22
You don't really need to do anything... It didn't remove the directory ./Music/dropkick because the rm command didn't specify that directories should be removed for obvious reasons. Your music should now be duplicate free at any rate :D

---

### Post by TironN on 2009-11-22
Excellent! It all worked. Lovely!

---

