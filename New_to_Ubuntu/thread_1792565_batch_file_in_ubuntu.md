---
title: "batch file in ubuntu"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by yuki_sama on 2011-06-28
Hey, i need your help. I have a PHP program for email filtering by checking inbox. The question is how to make a batch file to run that program in certain time (for example every 30 second), so it can detect if there is/are new email. OS : ubuntu 11.04. 
Thanks a lot...:)

---

### Post by sanderd17 on 2011-06-28
Ubuntu doens't have batch files, but we do have bash scripts with about the same functionality.

You just make a file that starts with
```

# /bin/bash

```

after that line, you put your script, something like
```

sleep 30
check_for_mails

```

and you make it executable (with the chmod command or via the file properties in nautilus).

some info about the shell: [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by seawolf167 on 2011-06-28
And more information about writing scripts here - [BashGuide]("http://mywiki.wooledge.org/BashGuide").

---

### Post by yuki_sama on 2011-06-28
Thanks a lot for your answers. yup, have to visit those addresses...:)

---

