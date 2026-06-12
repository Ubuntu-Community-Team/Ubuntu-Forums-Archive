---
title: "help with script file"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by matrixman92 on 2010-11-01
i need to create a script file that can do the following.. make adirectory calledetcbackup, copy the /etc directory and all subdirectories to this directory, make a directory listing of etcbackup and make a file containing the listing, echo to the screen the steps being completed. How do i do this please?

---

### Post by matrixman92 on 2010-11-01
anyone?

---

### Post by papibe on 2010-11-01
This is a very simple attempt:
```

#!/bin/bash

if [ -d etcbackup ]
then
	echo "Ditectory etcbackup exists."
	exit 1
fi

mkdir etcbackup
cp -rp /etc etcbackup

ls -R etcbackup >> etcbackup/list_of_files.txt

```

You'll have to "sudo" it, so it could backup protected files.
Enjoy!

---

### Post by SaintDanBert on 2010-11-01
Consider using **rsync** to make the copy target.
Once you complete that, you can then create your list.

**rsync** has options that will write a log of what is happening
while it works. That log might already work as your list of details.
Or it might be easy to filter to create the list that you want.

Bonne chance,
~~~ 0;-Dan

---

### Post by Hippytaff on 2010-11-01
something like 
```

#!/bin/bash
#backup /etc
if [[ -d backup-etc ]]; then
echo 'backup-etc already exists'
else
mkdir /backup-etc
fi
cp /etc /backup-etc
echo '/etc backed up'
ls -a /backup-etc >> backed-up-list.txt
echo 'back-up-list updated'
#end

```

Actually this is a bit rubbish the first one looks better

---

### Post by SaintDanBert on 2010-11-04
**Hippytaff** presented a script that uses 'cp' to move files.
I recommend that you use the following:
```

prompt$  cp --archive $FromHere  $ToThere

```

According to the **cp** manual page the option **--archive** activates the options
[list]
[*]**--recursive** == process the $FromHere files and all sub-folders
[*]**--no-dereference** == files that are *links* at $FromHere remain links in $ToThere
[*]**--preserve=all** == set attributes on $ToThere files to match ownership, permissions, timestamps, etc on the $FromHere files
[/list]

---

### Post by Hippytaff on 2010-11-04
> **SaintDanBert said:**
> **Hippytaff** presented a script that uses 'cp' to move files.
I recommend that you use the following:
```

prompt$  cp --archive $FromHere  $ToThere

```
 

According to the **cp** manual page the option **--archive** activates the options
[LIST]
[*]**--recursive** == process the $FromHere files and all sub-folders
[*]**--no-dereference** == files that are *links* at $FromHere remain links in $ToThere
[*]**--preserve=all** == set attributes on $ToThere files to match ownership, permissions, timestamps, etc on the $FromHere files
[/LIST]
 
I've since decided I prefer the rsync option :-)

---

### Post by SaintDanBert on 2010-11-05
1.  If your situation is handled to your satisfaction, please mark the thread SOLVED.

2. re: "stupid questions"
A wise teacher once taught me that the only "stupid questions" are those that we do not ask.

Cheers,
~~~ 0;-Dan

---

