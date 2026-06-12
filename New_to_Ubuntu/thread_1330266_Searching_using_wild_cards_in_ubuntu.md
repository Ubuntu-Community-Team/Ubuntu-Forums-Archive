---
title: "Searching using wild cards in ubuntu"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by BDNiner on 2009-11-18
I would like to know how to search ubuntu using wild cards and preferably using nautilus as I have to delete the files that the search returns. Also the search needs to be performed on a network drive, I have already figured out that I need to mount the share inorder to search it but nothing comes up when I do.

For example in windows I can search using the criteria
```

*@*.mp3

```

In ubuntu this doesn't work. All the files I am looking for are mp3s that have the "@" in their title. I would like to delete these files.

---

### Post by diesch on 2009-11-18
Unfortunately Nautlius' search function is a bit limited. Use the search function of the "Places" menu instead. Right clicking on the results gives you a context menu with the option to delete files.

---

### Post by akelsall on 2009-11-18
I'd recommend installing beagle. It will do exactly what you want. Once the search runs, just highlight the files you want to delete, right-click, and select "move to trash"

 sudo aptitude install beagle


Andy

---

### Post by mvalviar on 2009-11-18
If you're comfortable with using the terminal. You could try this:

cd to the directory where you want to do your search then type ```

find . -name '*@*.mp3' 
```

That should show all mp3 files with @ in their name. If you're happy with what you found run ```
find . -name '*@*.mp3' -exec rm '{}' \;
``` to delete them.

---

### Post by BDNiner on 2009-11-18
Will the command line option search in folders within folders? I have a main my music folder and a bunch of music arranged by artist and album.

Beagle also seems like a good option I will install that. I was kinda pissed because windows search worked fine without any complaints. I guess there are limitations to Nautilus search.

---

### Post by ukripper on 2009-11-18
> **BDNiner said:**
> Will the command line option search in folders within folders? I have a main my music folder and a bunch of music arranged by artist and album.



find command will search in sub-directories as well.

---

