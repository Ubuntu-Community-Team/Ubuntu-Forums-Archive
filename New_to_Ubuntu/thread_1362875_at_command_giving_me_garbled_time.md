---
title: "at command giving me garbled time"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-12-23
im using
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

ubuntu$ at
Garbled time
ubuntu$

how do i reset the at command so i can use it again it is stuck at garbled time.

---

### Post by falconindy on 2009-12-23
Running 'at' with no arguments will fail. That's just how the program works. Read 'man at' for more info on proper invocation.

---

### Post by lance bermudez on 2009-12-23
is their a way to use
zenity --info --text="test" instead of notify-send 'yay'

in the command

at 18:17
warning: commands will be executed using /bin/sh
at> notify-send 'yay'

---

### Post by falconindy on 2009-12-23
Sure. Throw it into a script file and run it as:
```
at -f /path/to/script.sh 18:17
```

---

### Post by lance bermudez on 2009-12-23
Sure. Throw it into a script file and run it as:
at -f /path/to/script.sh 18:17

what would the script look like? the best i can do is

#!/usr/bin/bash
echo 'notify-send'
date
read date
at $date 

I think you had a easery way to do this.

---

### Post by falconindy on 2009-12-23
The script would just contain the execution of the program you want to run via the at command...
```
#!/bin/sh
notify-send "`date`"
```

or using Zenity...
```
#!/bin/sh
zenity --info --text="`date`"
```

This **might** not work because of issues with X authorization. You may have to prepend the command with your display, i.e.:
```
DISPLAY=:0.0 zenity --info --text="`date`"
```

---

### Post by lance bermudez on 2009-12-23
i have a script that works if i dont do at -f for displaying zenity --info --text="test"

i have to put sh or bash before the script to get it to work this errors our the at -f command

#!/usr/bin/bash
zenity --info --text="test" 

to run it 
sh test
bash test

---

### Post by falconindy on 2009-12-23
You need to specify the shell because your shebang points to the wrong location, and you may or may not have made the file executable with 'chmod +x script.sh'. Normally, you shouldn't. And with this fix or fixes in place, it will work with at -f.

---

