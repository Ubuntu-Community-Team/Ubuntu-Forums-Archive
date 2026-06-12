---
title: "MV command question"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by GodJunker on 2009-05-19
Got a simple(I hope) about the MV command. How do I add spaces in when I move folders? 

mv -t /home/kyle/Anime /home/kyle/Desktop/Gundam 08th MS Team

So how would I represent those spaces in the folder name? Since all it does is give me errors doing it like that. I did the mv --help and found nothing about it.

---

### Post by samden on 2009-05-19
You need to put the title in quotation marks, ie:

mv -t /home/kyle/Anime /home/kyle/Desktop/"Gundam 08th MS Team"

Or you could decide to rename the folder using "_" instead of " "'s

mv -t /home/kyle/Anime /home/kyle/Desktop/Gundam_08th_MS_Team

Whenever you are dealing with spaces with the command line, not just with the mv command, use quotation marks. Incidentally this is why you should avoid using spaces in file and directory names, but I still keep on doing it, though I'm trying to get out of the habit...

---

### Post by GodJunker on 2009-05-19
That was easy. Thanks:D

---

### Post by Cheesemill on 2009-05-19
Or you can escape the spaces with a \
```
mv -t /home/kyle/Anime /home/kyle/Desktop/Gundam\ 08th\ MS\ Team
```

---

