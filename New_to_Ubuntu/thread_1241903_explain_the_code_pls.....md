---
title: "explain the code pls...."
date: 2009-08-16
forum: New to Ubuntu
---

### Post by kishoreavi on 2009-08-16
[B]#!/bin/sh
cd ~/utorrent/
if [ "$1" != "" ]; then
var="`echo $1 | sed 's////g'`"
var="Z:${var}"
wine utorrent.exe "$var"
else
wine utorrent.exe
fi[/B]:guitar:

---

### Post by mcduck on 2009-08-16
First the shebang, this simply tells that this is a shell script and should be executed with /bin/sh:
**#!/bin/sh**

Move to directory called "utorrent" inside the current user's home directory:
**cd ~/utorrent/**

Check if you added any parameterss when running the script:
**if [ "$1" != "" ]; then**

take the first parameter, do some parsing and store it in variable called "var":
[B]var="`echo $1 | sed 's////g'`"
var="Z:${var}"[/B]

run utorrent.exe with wine, passing the "var" as parameter for the utorrent:
**wine utorrent.exe "$var"**

If there wasn't any parameters, simply execute utorrent with wine:
[B]else
wine utorrent.exe
fi
[/B]

Somebody with a better grasp of sed will have to explain the details of the parsing done to the parameter. :)

---

