---
title: "why won't this script do what its supposed to"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by czerdrill on 2010-07-22
I'm trying to create a script to delete the contents of a subfolder which I can just double click and have it do its thing...here are my steps, someone please correct them lol

1] New file, named it cleanup.sh
2] Opened file and type ```
rm -rf .local/share/Empathy/logs/*
```3] Saved file
4] Terminal: ```
chmod +x cleanup.sh
``` (in the respective directory)
5] Double click file, select Run in Terminal, does something but folder contents still remain

If I run that same command directly in terminal it deletes the folder contents, so what step am I missing here?

---

### Post by matchett808 on 2010-07-22
Try:
rm -f ./.local/share/Empathy/logs/*

(if you have not got subfolders in that folder (ie. ./logs/mon/ etc))

---

### Post by marshmallow1304 on 2010-07-22
Where is the script?  It'll only work if it's in your home directory.

Try

```
rm -rf ~/.local/share/Empathy/logs/*
```

and you should be able to run that from any directory.

---

### Post by czerdrill on 2010-07-22
nope that didn't work...but there are subfolders in there.  if i run the original command directly from the terminal it deletes it subfolders or not...

this was intended for matchett...

trying your way now marshmallow

---

### Post by czerdrill on 2010-07-22
> **marshmallow1304 said:**
> Where is the script?  It'll only work if it's in your home directory.

Try

```
rm -rf ~/.local/share/Empathy/logs/*
```and you should be able to run that from any directory.

You are a gentleman and a scholar :D...that worked thanks!

---

### Post by czerdrill on 2010-07-22
Nevermind...

---

### Post by DaithiF on 2010-07-22
Hi,
at the risk of adding some confusion, when you have different behaviour between a script when its run from the command line versus when its run from the GUI, one thing to watch out for is the shell that it is being executed with.

when you run cleanup.sh in the terminal, it is being run by the bash shell.  When you run it from the GUI its being run by the dash shell.  There are some subtle differences between the two shells that can trip people up, so its good practice to add a shebang line at the top of the script to tell the system explicitly what shell to execute it with.  So #!/bin/bash at the top will mean it gets run by bash rather than dash when launched from the GUI.

(In the case of this script theres no difference in behaviour between the two shells)

---

### Post by bodhi.zazen on 2010-07-22
IMO it is best to use the full path in scripts. both to binaries and files.

If you are using the same binary more then once, set a variable.

> #!/bin/bash

IPTABLES='/sbin/iptables'

$IPTABLES -F
$IPTABLES -P DROP

....


etc

---

### Post by DaithiF on 2010-07-23
though you need to prefix the variables with $ before using them of course

```
IPTABLES='/sbin/iptables'

[COLOR=Red]$[/COLOR]IPTABLES -F
[COLOR=Red]$[/COLOR]IPTABLES -P DROP

```

---

### Post by bodhi.zazen on 2010-07-23
> **DaithiF said:**
> though you need to prefix the variables with $ before using them of course

```
IPTABLES='/sbin/iptables'

[COLOR=Red]$[/COLOR]IPTABLES -F
[COLOR=Red]$[/COLOR]IPTABLES -P DROP

```

oops, thank you for pointing that out, I updated my post.

---

