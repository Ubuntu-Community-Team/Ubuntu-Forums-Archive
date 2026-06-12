---
title: "bash export question"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by fredshevek on 2010-03-22
Hello,

I try to export 2 env variables by placing a sh file under /eth/profile.d

The weird think is that only one of those is exported.

Here is /etc/profile.d/jmagick.sh file:
```
#!/bin/bash -l
JMAGICK_PATH="/usr/lib:/usr/local/lib"

if [ $LD_LIBRARY_PATH ]
then
	LD_LIBRARY_PATH="$LD_LIBRARY_PATH:$JMAGICK_PATH"
else
	LD_LIBRARY_PATH="$JMAGICK_PATH"
fi

if [ $LDPATH ]
then
	LDPATH="$LDPATH:$JMAGICK_PATH"
else
	LDPATH="$JMAGICK_PATH"
fi

export LD_LIBRARY_PATH 
export LDPATH
```
after a system restart:
```
~$ echo $LDPATH 
/usr/lib:/usr/local/lib
~$ echo $LD_LIBRARY_PATH

~$ 

```
There is nothing on $LD_LIBRARY_PATH

I'm sure that $LDPATH is not set anywhere else because if I refome jmagick.sh file then $LDPATH is unset.

Thanks

---

### Post by r-senior on 2010-03-22
I think I'd add some lines to the end of the script to echo the values and redirect to a file. If they are both set OK at that point, something is overriding what you are setting.

---

