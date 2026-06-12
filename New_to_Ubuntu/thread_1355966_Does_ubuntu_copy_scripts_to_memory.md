---
title: "Does ubuntu copy scripts to memory?"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by outleradam on 2009-12-15
I'm making a script where if the script fails, it will make a separate script that will call the original script with all the input parameters again..
 
ie, you type in /path/script.sh $1 $2 $3, and it fails, it will output the parameters to a file that contains all the commands which have failed since the last time the script-created-script was run.
 
would it be possible to do this?
 
file: /path/thisfile.sh
```
 
rm /path/thisfile.sh
/path/script.sh $1 $2 $3  
/path/script.sh $1 $2 $3
/path/script.sh $1 $2 $3

```
 
or would the rm /path/thisfile.sh delete thisfile.sh before it was executed?

---

### Post by KIAaze on 2009-12-15
Have you tried it?
I don't know exactly where a script gets stored in memory and how it is run, but the following seems to suggest it's safe to remove a script while it is running:
```
$ cat /tmp/tmp.sh
#! /bin/bash
echo HELLO1 $1 $2 $3
rm /tmp/tmp.sh
echo HELLO2 $1 $2 $3
$ /tmp/tmp.sh a b c
HELLO1 a b c
HELLO2 a b c
$ ls /tmp/tmp.sh
ls: cannot access /tmp/tmp.sh: No such file or directory

```

> I'm making a script where if the script fails, it will make a separate script that will call the original script with all the input parameters again..

ie, you type in /path/script.sh $1 $2 $3, and it fails, it will output the parameters to a file that contains all the commands which have failed since the last time the script-created-script was run.

would it be possible to do this?
I'm not sure I understood what you are trying to do. :confused:
Could you give a more precise example? Or explain the problem you are trying to solve?

Do you mean something like this?:

script1.sh
```

good cmd #runs
good cmd #runs
bad cmd #runs and fails. script1.sh writes it to script2.sh and exits
good cmd #does not run

```

script2.sh
```

bad cmd

```

---

### Post by outleradam on 2009-12-19
k, cool. i'm working on this script. 
 
[FONT=Courier New]***http***://mythicallibrarian.googlecode.com/svn/trunk/[/FONT]
 
any kind of change to the script requires the show to complete for testing.

---

