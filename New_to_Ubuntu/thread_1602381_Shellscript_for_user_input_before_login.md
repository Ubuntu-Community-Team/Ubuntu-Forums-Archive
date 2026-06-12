---
title: "Shellscript for user input before login"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by helferr on 2010-10-21
I've been working in a project that uses ubuntu server. I'm trying to receive input from the user before the login prompt appears by running a shellscript that was added to the init.d through the proper means (update-rc.d).

During boot this script is invoked (I can see the input message I defined..) and the system freezes.

The shellscript runs fine, if invoked it from the bash prompt. Even tried adding this same script to rc.local with the exact same results (system freeze).

Does anyone have an idea if this is even possible? or what could be the problem?

Thanks!

---

### Post by LowSky on 2010-10-21
Can you show us the script you are trying to run, and what point in the boot process are you trying to run the script. It could be that the process is causing an unrecoverable error due to a unloaded process

---

### Post by helferr on 2010-10-21
Hello, thanks for the feedback :)

This is a very simplified version of the script (and also freezes when added to the boot sequence).

The problem seem to happen in the 'read S' because the following echo never shows...
Funny thing that this seems to work when I do a shutdown ( I'm using the defaults on the update-rc.d) and I can do some input, but as soon has I restart I get a system freeze. This allways happens in the boot.


```
#!/bin/bash
#########################################################################
# Script configuration
CONFIG_DIR=/tmp/cfgs
SERIALID=$CONFIG_DIR/serialid
#########################################################################
if test -d $CONFIG_DIR; then 
    echo Config directory exist
    CURRENT_SERIALID=`cat $SERIALID`
    if test $CURRENT_SERIALID = "0"; then    
        echo -n "Input serial id :"
        read S
        echo "Serial is $S"
    fi
fi
```
The script is being defined in S20test but if we place it in the rc.local (S99rc.local) the result is the same faillure.
I'm assuming that rc.local is the last thing to run before the login prompt shows...

Ideas? 

Thanks

---

### Post by helferr on 2010-10-21
Another simple test is to just add to the /etc/rc.local the following lines before the 'exit 0':

```

(...)
read S
echo "Input was $S"
(...)

```

The result is the same. After this, one has to go to the recovery console and remove these lines as the root user :(

---

### Post by helferr on 2010-10-26
Ok, we arrived at a solution and I'm sharing it :) 

Edit the tty configuration (/etc/init/tty*.conf) and add a line that invokes getty with a shellscript as a parameter just like:

```
(...)
exec /sbin/getty -n -l  theInputScript.sh -8 38400 tty1
(...)
```

Assuming that, we are editing tty1 and the script that reads input is theInputScript.sh.
This should work as it did for me. A word of warning this script is run as root, so when you are inputing stuff to it you have root priviliges. Also append a path to the location of the script.

Important: the script when it finishes, has to invoke the /sbin/login otherwise you wont be able to login in the terminal.

And.. thats all.

Thanks! :)

---

### Post by samo_nz on 2011-03-29
Thank you so much! that worked a treat

---

