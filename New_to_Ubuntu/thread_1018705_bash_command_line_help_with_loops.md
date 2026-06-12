---
title: "bash command line help with loops"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by ace007 on 2008-12-22
So I have a script which is more complex than below, so I dumbed it down, it gets across the idea.  I have two variables which are the "source" and "dest" directories and have equal elements.  How do I run a loop so that the 1st source is mounted in the 1st dest, 2nd source to 2nd dest, 3rd source to 3rd dest, etc.  

Here is what I have so far, will it work or do I need to select the individual components of $SOURCEDIR?

```

#!/bin/bash

SOURCEDIR=/media/Movies,/media/TV,/media/Videos
DESTDIR=Movies,TV,Videos

for i in $DESTDIR; do
    [[ -d "/home/ace/$DESTDIR" ]] || mkdir /home/ace/$DESTDIR 
    mount $SOURCEDIR /home/ace/$DESTDIR
fi

```

In reality the script is mounting a sshfs folder, so I am not using the above mount command but a more complex sshfs command and a number of more complex commands in the script, but this is the idea.

---

### Post by bluefrog on 2008-12-22
cd media; for i in *.iso; do mkdir -p ~/$i; sudo mount -o loop $i ~/$i; cd; done

---

### Post by Hospadar on 2008-12-22
You could pass sourcedir into the "cut" command to parse out the individual source directories.

If you do a "man cut" you can find out all about it.  I think it'll be something like ```
$RESULT=`cut -d, -f$SOME_COUNTING_VARIABLE $SOURCEDIR`
```Those arn't single quotes, they are the tick in the upper left hand corser

---

### Post by ace007 on 2008-12-22
bluefrog: thanks for your suggestion, but the destination folders aren't all named the exact same as they are named on the source.  I just placed some examples above.  And the folders are on my server, so I cant just cd /media.

 Hospadar: thanks for your suggestion, I'll investigate the cut and awk commands

---

