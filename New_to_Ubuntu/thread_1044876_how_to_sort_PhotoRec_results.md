---
title: "how to sort PhotoRec results"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by cartisdm on 2009-01-19
I used PhotoRec(part of TestDisk) in order to recover a picture directory that I had formatted over.  I recovered picture files as well as .txt, .gz, .htm etc.  There are about 600 different directories containing various files inside, most of which are meaningless.

Obviously I have to sort through these (unless there is an easier way to get results after PhotoRec has ran that I don't know about), but how do I search through and find just picture files in Nautilus.  I need a GUI search because I need to see the thumbnail to decipher if it's just a stupid icon or an actual picture for me to recover.  I tried using the Search feature in Nautilus with " *.jpg " but that didn't seem to work.  Am I doing it wrong or is there another way?

---

### Post by spiderbatdad on 2009-01-19
how did search not work? Perhaps update database then search?
```
sudo updatedb
```

---

### Post by cartisdm on 2009-01-20
EDIT:

Here's what I ended up running in a terminal:

```
find . -name "*.jpg"
```

This returns lots of results, more than I want to scroll up and count.  So I have two questions:

- How can I count how many results I just got from running that command (so I can get idea of how much I'll be copying over)

- How can I copy the results of those searched jpeg files over to another folder?

---

### Post by datacorder on 2012-05-14
I just did a script for sorting Photorec results.

It's usefull to help you to find what you are searching in Photorec results and to improve the results for it's delivery to your data recovery customers.

You can check it out in my website: [http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)

Hope it is useful to you.

---

### Post by oldfred on 2012-05-14
Testdisk/photorec has some scripts also:

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

