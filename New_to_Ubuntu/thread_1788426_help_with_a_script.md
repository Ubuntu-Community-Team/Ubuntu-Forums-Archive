---
title: "help with a script"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by Avidanborisov on 2011-06-22
I need to implement in a larger script of mine, bash code that will check if some packages are installed, if yes, do something, if not do something else.
can someone give me an example code of how should I do it?

---

### Post by gmargo on 2011-06-22
You can use **dpkg(1)** to test for installed packages:
```

#!/bin/sh
pkglist="dpkg foobar"
for PKG in $pkglist
do
    dpkg -l $PKG >/dev/null 2>/dev/null
    if [ $? -eq 0 ]; then
        echo "Package $PKG is installed"
    else
        echo "Package $PKG is NOT installed"
    fi
done

``````

$ ./pkgtest.sh 
Package dpkg is installed
Package foobar is NOT installed

```

---

### Post by Avidanborisov on 2011-06-23
Thank you! this is just what I needed!

---

### Post by Avidanborisov on 2011-06-25
hey, just another quick question.
In the script I have a variable that contains a string with 4 letters.
How can I split it into to two variables, one that contains the first three letters and another that contains only the last letter?
edit: nevermind, I used offsets.

---

### Post by nothingspecial on 2011-06-25
```
$ f="abcd"
$ g="${f:0:3}"
$ h="${f:3:1}"
$ echo "$g"
abc
$ echo "$h"
d
```

****Edit Oh you got it. cool*

---

### Post by gmargo on 2011-06-25
My mind automatically thought of using **sed(1)**.  Offsets are bash-specific and not part of the standard shell, so make sure you use the proper she-bang (#!/bin/bash).

---

### Post by Avidanborisov on 2011-06-26
For the end - My script is done. Can anyone suggest me a good place to host it with option to edit it and to be accessible via wget?

---

### Post by Avidanborisov on 2011-06-27
BTW, how do I upload files to launchpadlibrarian?

---

