---
title: "renaming mp3s from a ipod"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by spiral the dog on 2010-06-01
hi
i my friend has just droped loads of music on to the computer from his ipod but all the names are just codes, when i look at the tag id the information is all there, how can i get the names to change automatically without having to do it all manually. is there a comand that can be put into the termal or a programme


Thanks

---

### Post by Buuntu on 2010-06-01
Here's a script that will do just that.  It uses a program called id3tool.  Before this script will run, you have to do
```
sudo apt-get install id3tool
```The script itself will change all files with an ID3 tag to the format 'TITLE-ARTIST.extension' in the directory specified.  It also renames files in the directory so that they don't have spaces (which is bad practice anyways).  It's a little extensive and poorly written but it's what I could do with what I know :P.

The script:
```

#!/bin/bash
if [ "$1" = "" ];then
echo "Please enter a directory"
exit
fi
rename 's/ /_/g' *
ls $1 > /tmp/lsout
while read LINE; do
if [ "`id3tool $LINE | grep "No ID3 Tag"`" = "" ]; then
EXT=`echo "$LINE" | cut -d\. -f2`
TITLE=`id3tool $LINE | grep Title | cut -d\: -f2 | sed 's/^[ \t]*//;s/[ \t]*$//'` 
ARTIST=`id3tool $LINE | grep Artist | cut -d\: -f2 | sed 's/^[ \t]*//;s/[ \t]*$//'`
mv "$LINE" "$TITLE-$ARTIST.$EXT"
fi
done < /tmp/lsout
rename 's/ /_/g' *
rm /tmp/lsout

```Save this to a text file (just copy+paste) called namemp3s in your home directory.  Next, open up a terminal and run
```
chmod +x namemp3s
```Now you're ready to run the script.  The syntax for running it is simply namemp3s [directory] - all files with an ID3 tag in the specified directory will be renamed.  So if all the music is in your Music folder, just run:
```
./namemp3s Music/
```
This script isn't recursive, so if you have more directories inside Music, none of the music in those directories will be changed.  To do that you have to run the script for each individual directory.  


Hopefully that does it for you.  Let me know if there are problems with the code or other questions you might have.

---

### Post by Buuntu on 2010-06-01
This is an upgraded version of the same script:
```

#!/bin/bash
# This script will bulk rename music files with ID3 tags to format:
# '[song title]-[artist name].extension'
# The script will take one argument which is the directory in which to rename.
# WARNING: All files in directory with spaces will be renamed, substituting
# the spaces for the '_' character.
if [ "$1" = "" ];then
echo "Error: Please enter a directory."
echo "Format is 'namemp3s [directory]'."
sleep 1
exit
fi
rename 's/ /_/g' *
ls $1 > /tmp/lsout
while read LINE; do
if [ -d $LINE ];then
    echo "$LINE is a directory. It will not be renamed."
elif [ "`id3tool $LINE | grep "No ID3 Tag"`" != "" ]; then
    echo "$LINE has no ID3 Tag. It will not be renamed."
else
    EXT=`echo "$LINE" | cut -d\. -f2`
    TITLE=`id3tool $LINE | grep Title | cut -d\: -f2 | sed 's/^[ \t]*//;s/[ \t]*$//'` 
    ARTIST=`id3tool $LINE | grep Artist | cut -d\: -f2 | sed 's/^[ \t]*//;s/[ \t]*$//'`
    NEWNAME="$TITLE-$ARTIST.$EXT"
    NEWNAME=`echo "$NEWNAME" | sed 's/ /_/g'`
    mv "$LINE" "$NEWNAME"
    echo "$LINE ---> $NEWNAME"
fi
done < /tmp/lsout
rm /tmp/lsout
```

---

