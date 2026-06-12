---
title: "Some help finding a file"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by lile001 on 2010-02-24
Yesterday I was opening a folder, without paying much attention, and when I looked at the screen it had vanished!  Prolly accidentallty drag and dropped it instead of opening it - but where?  It's not in the trash, can't find it looking in obvious places.  Could be completely gone, in which case I can dig out backups.  Be better to find it if it still exists.  "ls" to the rescue! 

My knowledge of the "ls" command  and terminal is less than adequate. I know what the folder was called, but was it all caps, no caps?  Can't remember.   I know that folder is the only place I would have a *.dwg file on my computer - might be a good search strategy.  How would I form such a command to find any folder with  .dwg files on my computer?

---

### Post by lavinog on 2010-02-24
```

find ~ -iname '*.dwg'

```

If you don't find it there:
```

find / -iname '*.dwg' 2>/dev/null

```
the 2>/dev/null suppresses the permission denied messages

---

### Post by Ozymandias_117 on 2010-02-24
Another option would be "locate -i *.dwg" (If it doesn't come up with any results, use the command "sudo updatedb" then try again) -i means it is case insensitive. locate works off a database instead of real time, which makes it faster, but, if the database isn't new enough, you may not find your file (That's where "sudo updatedb" comes in.)

---

### Post by SoFl W on 2010-02-24
When this happened to me I have found I dragged it into another folder.

---

### Post by lavinog on 2010-02-25
> **Ozymandias_117 said:**
> Another option would be "locate -i *.dwg" (If it doesn't come up with any results, use the command "sudo updatedb" then try again) -i means it is case insensitive. locate works off a database instead of real time, which makes it faster, but, if the database isn't new enough, you may not find your file (That's where "sudo updatedb" comes in.)

The problem with using locate in this case is that the database is likely to be outdated if the user recently moved the files.

---

### Post by gordintoronto on 2010-02-25
> **lavinog said:**
> ```

find ~ -iname '*.dwg'

```



Thanks, Lavinog!  You could have said, "use the find command," but you spelled it out.  It was obvious to me that the format of the find command should be: "find *.dwg" and I was always disappointed with its results.

I still think the author of the program got the format dreadfully wrong, but at least I now know how to use it.

---

### Post by lile001 on 2010-02-26
> **lavinog said:**
> ```

find ~ -iname '*.dwg'

```If you don't find it there:
```

find / -iname '*.dwg' 2>/dev/null

```the 2>/dev/null suppresses the permission denied messages
Sounds good, but this only seems to find stuff in the current directory.  How do you make it search all subdirectories?

---

### Post by lile001 on 2010-02-26
> **Ozymandias_117 said:**
> Another option would be "locate -i *.dwg" (If it doesn't come up with any results, use the command "sudo updatedb" then try again) -i means it is case insensitive. locate works off a database instead of real time, which makes it faster, but, if the database isn't new enough, you may not find your file (That's where "sudo updatedb" comes in.)


This worked.  As I suspected, the folder was drag-and-dropped two levels deep.  Thanks!

---

