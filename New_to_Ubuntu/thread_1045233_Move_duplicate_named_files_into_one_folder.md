---
title: "Move duplicate named files into one folder"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by cartisdm on 2009-01-20
I did a search for all my JPEG files throughout a harddrive.  Many have identical names but are located in different directories.  Via the search I can see them all at the same time, but now I want to copy everything and paste it into one folder.

This can't be done without skipping the identical files or replacing them.  I don't care about what any of the files are named, they could be gibberish for all I'm concerned but I don't want to lose any of the files.  How can I accomplish this?

---

### Post by northern lights on 2009-01-20
Run the following in the specific folder(s) to add a running number (i.e. resolve filename conflicts)```
n=1; for i in *.jpg; do mv "$i" "${i/.JPG}-[$j]".jpg; let "n= $n + 1"; done
```

---

### Post by cartisdm on 2009-01-20
the JPEG are listed in a search results window.  There are results in about 300 different folders, there's not really a way I can navigate to all the folders containing the pictures

---

### Post by Hospadar on 2009-01-20
Well, if you have lots of files, and you really want them all in just one directory, I would write a script (a bash script) to search for those files, rename, and move them.  In fact, I have devised just such a script!

```
#!/bin/bash
FILETYPE=".jpg"
DESTINATION="~/new_PIX
mkdir $DESTINATION
cd $DESTINATION
#find all the jpegs in your home directory
find ~ -name "*$FILETYPE" | grep -v $DESTINATION | while read FILENAME
do
#generate a new random filename
NEWNAME=$RANDOM
#make sure it isn't already in use
while [ -e $DESTINATION/$NEWNAME$FILETYPE ]
do
    NEWNAME=$RANDOM
done
#print out the names of the files we are moving and where they are going
echo "moving $FILENAME to $DESTINATION/$NEWNAME""$FILETYPE"
#move the files
mv $FILENAME $DESTINATION/$NEWNAME$FILETYPE

done

```This will create a folder called new_pix and move all of your newly randomly renamed jpg files into it.

The find line is really the main operator here
The first part 
find ~ -name "*$FILETYPE"
Finds every file with $FILETYPE extension
the grep part filters out images that have already moved (i.e. those in the $DESTINATION folder)
the wile read part loops through each line in the output


Just in case you arn't familiar with bash scripts, the way I'd make this happen, is open a terminal:
```
nano
```paste in the script (right click with the mouse in the terminal, ctrl-v won't do it)
Then save the script with ctrl-o, maybe name it mover.sh
Quit with ctrl-x
then make the script executable```
chmod uog+x mover.sh
```now let's run our new script```
./mover.sh
```

A couple notes:
This will only move  files

---

### Post by northern lights on 2009-01-20
Make it```
n=1; for i in `[COLOR="Red"]locate *.jpg[/COLOR]`; do mv "$i" [COLOR="Navy"]"${i/.JPG}-[$j]".jpg[/COLOR]; let "n= $n + 1"; done
```then.

Alter [COLOR="Red"]*jpg[/COLOR] to your search term.

[COLOR="Navy"]"${i/.JPG}-[$j]".jpg[/COLOR] sets the new filenames to OLDFILENAME-RUNNINGNUMBER.jpg If you just want to make it RUNNINGNUMBER.JPG, alter accordingly to [COLOR="Navy"]"$j".jpg[/COLOR]

---

### Post by cartisdm on 2009-01-20
You guys are awesome, thanks!!!!!!


EDIT:  When did they remove the "Thanks" feature?  Someone mind posting a link to a thread that discussed it?

---

### Post by northern lights on 2009-01-20
[http://ubuntuforums.org/showpost.php?p=6544653&postcount=9]("http://ubuntuforums.org/showpost.php?p=6544653&postcount=9")

---

