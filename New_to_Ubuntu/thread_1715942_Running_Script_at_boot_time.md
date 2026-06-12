---
title: "Running Script at boot time"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by Apoorvbarwa on 2011-03-27
Hi i am trying to run a script at boot time but am not able to .... i have created the script and placed it in the folder **/etc/init.d/** also i created a symbolic link in the folder etc/rcS.d as
**sudo ln -s /etc/init.d/my_script/ S33myscript **
but it did not work .......... i also tried to put the script in **rc.local **file as i added the line 
**sh /etc/init.d/myscript **

also when i did
**sudo update-rc.d defaults myscript** 
the script would run on shutdown ... and since a user input is required the system would not shutdown and i had to shut it down manually....
i searched but these were the only solutions i found ... could anyone help me .... 
I am running ubuntu 10.04

---

### Post by aaaaalex on 2011-03-27
Why not simply put it in /etc/rc.local?

I know there are a gazillion other ways but this is easy and probably just what you are looking for:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/path/to/your/scrip/here.sh

exit 0

```

---

### Post by Apoorvbarwa on 2011-03-28
Already tried this ... did not work .... can it be possible that my script runs at boot up but does not show ... although to exit the screen i have asked for a user inout in it ... if so is there way to check if my script has run during boot up .....

---

### Post by smuthavarapu on 2011-03-28
Did you try put that script in Start-Up applications ?

---

### Post by robsoles on 2011-03-28
If you think your script might be executing but not managing to stop anything long enough for you to see then you could include appending the current response for the 'date' command to a file in your script.```
date >> /home/[COLOR=Red]<your-user-name>[/COLOR]/testing-script.txt
```

---

