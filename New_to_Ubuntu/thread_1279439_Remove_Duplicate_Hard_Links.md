---
title: "Remove Duplicate Hard Links"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by Commander_Bob on 2009-09-30
I am trying to remove all the duplicate MP3's in my library. If my quest to do so I came across FSlint, which seems to work pretty well. However, I clicked Merge, which turned all the duplicate files into hard links. Now it won't detect the duplicates, but they are still there.

Is there a way to detect and remove duplicate hard links?

Thanks,
Justin

---

### Post by Commander_Bob on 2009-09-30
Figured it out.
```
fdupes -r -H -d .
```

---

### Post by blackest_knight on 2012-07-29
fdupes -r -H -N -d 

slightly quicker version the -N tells fdupes to preserve the first entry and delete the others the equivilent is to press 1 then newline repeatedly for me that would be upwards of 9000 times.

fslint-gui seems to be the best way to locate duplicates but merging while recovering space doesnt deal with the duplicate files appearing in playlists and such like.

Processing is quite slow but this should work eventually.

anyway thats how i did it fslint-gui to find dupes and merge and fdupes to delete the extra file names.

---

