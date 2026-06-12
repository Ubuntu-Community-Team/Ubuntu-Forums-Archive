---
title: "unrar in subdirectoris"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by mafi127 on 2011-08-31
How can I unrar many folder if the folder are in subdiretoris ? I have 22 simpsons episode witch are like this

videos/simpsons/sesson 1/episode1/simpsons.s01e01.r00
videos/simpsons/sesson 2/episode2/simpsons.s01e02.r00
videos/simpsons/sesson 3/episode3/simpsons.s01e03.r00

how  can I run a shell script in videos/simpsons/ to unrar all rar files in the subdir?

---

### Post by snip3r8 on 2011-08-31
first in the directory that contains the files :

```
ls | grep -i .rar > unrar.sh
```

this will write the names of all the files to a file called unrar.sh

then copy the appropriate unrar code infront of the file names
and save and run the script

```

sh unrar.sh

```

---

### Post by nothingspecial on 2011-09-01
unrar */*/*.r00

---

### Post by snip3r8 on 2011-09-01
> **nothingspecial said:**
> unrar */*/*.r00

Guess that is a shorter route.

---

### Post by mafi127 on 2011-09-01
> **nothingspecial said:**
> unrar */*/*.r00

This wold be the easyest way, but this command dont work for me.

Rightnow I'm using this script

[PHP]#!/bin/bash

BASE=.

for file in `find $BASE -name "*.r00"`; do
    cd `dirname $file`
    unrar e `basename $file` &&  rm *.r??
done[/PHP]

but this dont work very well, because when I run this script it wil unrar only one folder and then it says error. Then I need to manualy aigan run the script to extract another folder

the error msg is 

[PHP]UNRAR 4.00 beta 3 freeware      Copyright (c) 1993-2010 Alexander Roshal

Cannot open the.simpsons.s18e20.pdtv.xvid-2hd.r00
No such file or directory
No files to extract
unrar.sh: line 6: cd: ./The.Simpsons.S18E21.PDTV.XviD-LOL: No such file or directory

UNRAR 4.00 beta 3 freeware      Copyright (c) 1993-2010 Alexander Roshal

Cannot open the.simpsons.1821.pdtv-lol.r00
No such file or directory
No files to extract
unrar.sh: line 6: cd: ./The.Simpsons.S18E22.PDTV.XviD-LOL: No such file or directory
[/PHP]

---

