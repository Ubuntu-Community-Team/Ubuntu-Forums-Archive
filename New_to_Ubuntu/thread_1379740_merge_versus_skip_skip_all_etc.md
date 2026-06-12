---
title: "merge versus skip skip all etc"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by completeidiot on 2010-01-12
I think i'm becoming a legend in the dumb questions field but, it's better safe than sorry. 
I'm copying some mp3 files from one drive to another....planning to format my external change it to fat32 from mac and transfer back. unfortunately there is some duplication in files and in folder names. whenever the transfer finds a duplicate folder it gives me the merge, skip, skip all and some other option. 
what exactly does merge do? will it overwrite files with the same name? will it only copy over the files that are not duplicate? ideally it would just combine the folders and not skip over anything...at least in this case. 
so how sophisticated is merge? it's a truly massive transfer and very important data so i want to be sure

---

### Post by falconindy on 2010-01-12
I would hope that merge would be smart enough to behave similarly to the 'update' functionality in some command line utils such as cp and rsync. That is, a file is only written to the destination if it is newer than the pre-existing file. However, this may not actually reflect reality.

That said, why not copy via the command line so you can specify exactly what you want to happen?

```
cp -ru <source> <destination>
```

This will copy recursively (include directories) and follow the update behavior I described above.

---

### Post by completeidiot on 2010-01-12
honestly i'm doing the transfer very slowly and deliberately because i would pretty much die if i lost any of the data. plus it's almost a terabyte and i have never been able to do a transfer anywhere near that size without some sort of interrruption...thus i'm doing it in blocks.
the merge option that pops up is in reference to folders not files. within the merge i may even get prompted about merging or skipping files individually. 
i really don't think the definition of merge in this instance is obvious. merging files is somewhat, but folders is a different story. especially when i am afraid it won't prompt again at the file level.

---

### Post by falconindy on 2010-01-12
> **completeidiot said:**
> honestly i'm doing the transfer very slowly and deliberately because i would pretty much die if i lost any of the data. plus it's almost a terabyte and i have never been able to do a transfer anywhere near that size without some sort of interrruption...thus i'm doing it in blocks.
the merge option that pops up is in reference to folders not files. within the merge i may even get prompted about merging or skipping files individually. 
i really don't think the definition of merge in this instance is obvious. merging files is somewhat, but folders is a different story. especially when i am afraid it won't prompt again at the file level.
You're right. It's not obvious, but thinking back to my Gnome days I'm fairly certain that it does re-prompt after prompting about a directory. It'd be fairly easy to test with some bogus files, but it sounds like you're most comfortable in just taking your time to make sure it goes as planned (which is understandable).

---

### Post by completeidiot on 2010-01-13
especially since i'm not in a rush, the work around isn't that big of a deal, but i'm still curious about what happens

---

### Post by completeidiot on 2010-01-16
Merging will still prompt you again at the individual file level.

---

