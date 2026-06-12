---
title: "I have files that I can't see on terminal, and files I can see on terminal but..."
date: 2011-04-29
forum: New to Ubuntu
---

### Post by BTXNick on 2011-04-29
So when I'm in terminal I see some files listed that I remember having on my computer, but when I'm not in terminal and view the folders they're in using the files and folders application I can't see them. I also can see a files in my folders I want to delete that I can't find using terminal.

Kind of confusing, why is this?


Thanks.


Edit: Also, when I try to delete the non-existent files that I can only see through terminal it won't let me, and when I delete the entire directory they're in, they move to another directory. Wtf?

Edit #2: It let me delete the files that I could only see through terminal, but they all have really long names, any way to copy/paste the names or something?

---

### Post by fabricator4 on 2011-04-29
> **BTXNick said:**
> Kind of confusing, why is this?

No idea, it sounds like you might not be on a Linux partition.

On a Linux partition the hidden files start with '.'

You can see them in Nautilus (file manager) by clicking <view><show hidden files> or pressing <ctrl><h>.

To see the hidden files in terminal use 
```

ls -a

```


> 
Edit: Also, when I try to delete the non-existent files that I can only see through terminal it won't let me, and when I delete the entire directory they're in, they move to another directory. Wtf?

When you delete files in Nautilus they will normally get moved to the trash folder.  To delete them without moving to trash select them then use <shift><delete>.  This works in Windows also.

To remove a directory in terminal use:
```

rm -R /pathname/dirname/

```

You will NOT be asked for confirmation so be careful.

Apart from that, if the files and directories are not in /home/username you may not have permission to delete them, or even view them under some circumstances.  We'd need to know more about what you are trying to do.

Chris

---

