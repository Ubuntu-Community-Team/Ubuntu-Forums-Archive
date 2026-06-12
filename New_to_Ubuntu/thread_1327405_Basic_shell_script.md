---
title: "Basic shell script"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by jualin on 2009-11-15
I have some video files all ending in .wmv .mov .mpg. I have music files ending in .mp3 .wma. And finally I have some text files all end in the extension .txt

I would like to write a shell script that will generate subfolders, one for the music files, one for the video files, and one for the text files, and then organize all of the files into the correct subfolders.
I would like the script to be interactive so it can prompt the user to make sure that he/she wants to continue with the reorganization.
And finally I would like the script to write a log file that contains, for each file, the original file name, as well as the new file path/name it was moved to. 
 I would like to run this script from the same folder as all of the unorganized files.

Any ideas of how to do that? :guitar:

Thank you in advance!

---

### Post by nikhilbhardwaj on 2009-11-15
i'll get you started but you'll have to do it yourself
if you get stuck will be glad to help

```

find . -iname \*.zip

```

will list all the files in the current directory which have a .zip extension

and 
you can use the redirection operator to get a list of movies txt etc
like
```

find . -iname "*.wmv" >>movielist

``` 

and then simply read a line at a time from the file
and move it to the required files
```

!/bin/bash

for i in `grep -v '^#' movielist`
do
  mv $i ./movies/
done
# that should move all the files from movielist to movies

```

as for interactive
look up the case statements in bash syntax
pretty similar to c++/java switch case

---

### Post by Liolikas on 2009-11-15
```


#!/bin/bash
#just ideas not tested for sure with mistakes :P


echo "Do you want run script? (Y/N)"
read yn
if (yn eq Y); then
mkdir video
mkdir audio
mkdir text
mv *.wmv video
mv *.mov video
mv *.mpg video
mv *.mp3 audio
mv *.txt text
ls video >> log.txt
ls autio >> log.txt
ls text >> log.txt
else
echo "aborted"
fi

```

---

### Post by jualin on 2009-11-15
Thank you both for the ideas, I will try them when I get into the Ubuntu machine.
:popcorn:

---

