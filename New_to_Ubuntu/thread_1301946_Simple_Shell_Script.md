---
title: "Simple Shell Script"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by pantherattack on 2009-10-26
Hi,

I don't know any of the syntax, but I pieced together a shell script from different sources. It's to toggle the output to the headphone jack on the front of my computer.

```
#/bin/bash

state=$(amixer sget 'Headphone',0 | grep '\[on\]' -c)

if [ "$state" == "2" ]
then
        amixer sset 'Headphone',0 off
else
        amixer sset 'Headphone',0 on
fi

exit 0

```

It works from command line (ie. running ./toggle_headphones.sh), but when I try to associate the script to a keyboard shortcut (tried a few including Alt-2, Alt-H, and my special email button) in System->Preferences->Keyboard Shortcuts, but it doesn't work. But I have gotten other shell scripts to run from  a keyboard short cut. 

Any ideas?

Ian

---

### Post by ctc26 on 2009-10-26
Hi Ian,

Please right click your shell script and select properties. Under properties, go to the permissions tab and ensure that the file is executable.

Alternatively, navigate to the folder where your script is placed in a Terminal (cd /home/username/script) and run:
```

chmod +x yourscriptname.sh

```

---

### Post by ajgreeny on 2009-10-26
I think you also forgot the "!" in the script. ie 
```
#/bin/bash
```should be ```
#!/bin/bash
```

---

### Post by pantherattack on 2009-10-26
Thanks ajgreeny, that did the trick.

---

