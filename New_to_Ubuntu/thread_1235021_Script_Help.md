---
title: "Script Help"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by Hygaphunkik on 2009-08-08
Having spent this morning learning how to write my first shell script so that I could put a Java programme to run from a menu link I have tried to repeat this success with a python programme. 
The commands all work when I type them directly into terminal but when I try to run them as a script a a terminal window opens briefly and then shuts.

#! /bin/bash
cd schoolprogs/Phonix/src
python phonix.py

Any help would be appreciated, I have trawled the forums but being a bit of a noober most replies to this kind of thing go straight over my head.

Thanks in advance

---

### Post by mcduck on 2009-08-08
I'd say the problem is with your cd command, you should either use full path or $HOME-variable to point to correct location, now your command only works if it's executed in the same directory where "schoolprogs" is located.

```
#! /bin/sh
cd $HOME/schoolprogs/Phonix/src
python phonix.py
```

or:
```

#! /bin/sh
cd /home/yourusername/schoolprogs/Phonix/src
python phonix.py
```

---

### Post by unutbu on 2009-08-08
Add "read" to the end of your shell script. Then the terminal window will wait for you to press Enter before closing the window.
```
#!/bin/sh
cd $HOME/schoolprogs/Phonix/src
python phonix.py
read
```

---

### Post by Hygaphunkik on 2009-08-08
> **mcduck said:**
> I'd say the problem is with your cd command, you should either use full path or $HOME-variable to point to correct location, now your command only works if it's executed in the same directory where "schoolprogs" is located.

```
#! /bin/sh
cd $HOME/schoolprogs/Phonix/src
python phonix.py
```

or:
```

#! /bin/sh
cd /home/yourusername/schoolprogs/Phonix/src
python phonix.py
```

Fantastic seems to have done the trick. When I write a script in future is it wise to all ways put in the $HOME at the begining of the path?

---

### Post by mcduck on 2009-08-08
Just make sure you use some format that gives the full path and works regardless of what directory you are in at the moment the command is executed.

Using $HOME instead of "/home/username/" of course has the benefit that it works regardless of the username, making the script more portable.

---

### Post by Hygaphunkik on 2009-08-08
> **mcduck said:**
> Just make sure you use some format that gives the full path and works regardless of what directory you are in at the moment the command is executed.

Using $HOME instead of "/home/username/" of course has the benefit that it works regardless of the username, making the script more portable.

That's handy to know as I may become involved in installing some software on other computers to run from menus.

---

