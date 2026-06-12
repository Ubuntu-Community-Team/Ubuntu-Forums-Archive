---
title: "syntax error"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by Spartukus on 2009-12-08
Hey guys keep having problems with the below script syntax error near unpexpected token '0' exit 0
 
I have two directorys backups and Usr in the usr i have sub dir's wp,ss,pic which i would like to back up (copy those directorys to the backups directory) with user acknowledgement from command line. I would then want the ability to restore those files back to the Usr from Backups so the code is below if any one could be so kind to help me out, would be much appreciated.
 
Thanks 
-----------------------------------------------------------------------------------------
echo "please choose backup or restore"
read bor
 
case "$bor" in
 
backup )
ls -d Usr/*
echo "please choose directory to backup (example wp,ss,pic)"
read dir
 
case "$dir" in
 
wp )
echo "word processor directory backedup"
cp -r Usr/wp Backups/wp;;
 
ss )
echo "word processor directory backedup"
cp -r Usr/ss Backups/ss;;
 
pic )
echo "word processor directory backedup"
cp -r Usr/pic Backups/pic;;
 
restore )
ls -d Backups/*
echo "please choose directory to restore (wp,ss,pic)"
read bdir
 
case "$bdir" in
 
wp )
echo "word processor directory restored"
cp -r Backups/wp Usr/wp;;
 
ss )
echo "word processor directory restored"
cp -r Backups/ss Usr/ss;;
 
pic )
echo "word processor directory restored"
cp -r Backups/pic Usr/pic;;
 
exit 0

---

### Post by lloyd_b on 2009-12-08
You aren't terminating any of the cases.  For every "case x in" line, you need a corresponding "esac" to mark where the end of that particular case structure is.  In the case of nested case statements, the esac needs the ";;" to mark where the end of that particular sub-case is.

Here's a short example of nested case statements:
```
echo "Enter first value (one, two)"
read val1

case $val1 in
    one)   echo "Enter value (hello, goodbye)"
           read oneval

           case $oneval in
               hello)    echo "one -> hello";;
               goodbye)  echo "one -> goodbye";;
           esac;;

    two)   echo "Enter value (day, night)"
           read twoval

           case $twoval in
               day)    echo "two->day";;
               night)  echo "two->night";;
           esac;;
esac

exit 0
```
Lloyd B.

---

### Post by Spartukus on 2009-12-08
echo "please choose backup or restore"
read bor

case "$bor" in

backup) ls -d Usr/* 
           echo "please choose directory to backup (example wp,ss,pic)"
           read dir

           case "$dir" in

wp )
echo "word processor directory backedup"
cp -r Usr/wp Backups/wp;;
esac;;

ss )
echo "word processor directory backedup"
cp -r Usr/ss Backups/ss;;
esac;;
 
now I get an error near unpexcted token ';;' line 25 esac;; which the last esac under ss??
 
anythoughts?

---

### Post by lloyd_b on 2009-12-08
I guess I didn't explain it clearly.

The "esac" occurs after the *last* case for a given case structure, not at the end of each individual case within the case structure.

The ";;" marks the end of an individual case within a case structure.  'esac' only needs this when it happens to be the last statement within such a case.

May I suggest you take my example, and modify it?  It *does* work, so you can make changes one at a time and test them, which makes it easier to identify problems.

Finally, when doing case structures, it is a lot easier to read if you indent one step (I use 4 spaces, but that's personal preference) for the individual cases.  You can preserve indentation on this forum by highlighting the text, and clicking the "#" icon towards the top of the message entry window (or manually wrapping it in CODE tags, if you're familiar with PHPcode).

Lloyd B.

---

### Post by Spartukus on 2009-12-08
YOU ARE A GOD AMONG MEN! 
 
Thanks alot.
 
There is one slight problem well not a problem with the syntax but my silly attempt at this, and thats when I try to copy something over thats already there it places it further into the directory?
 
Is there a way to add a delete if already there statement to this syntax:
 
cp -r Usr/Pic Backups/;; 
 
i need it to delete if already there and then copy as this is just copying atm?

---

### Post by Locke_99GS on 2009-12-08
if [ -e /Usr/Pic\ Backups/ ]; then rm -rf /Usr/Pic\ Backups/; fi;

edit: proper indents makes the script so much easier to read and understand at a glance.

---

### Post by Spartukus on 2009-12-08
```
all) echo "all files backed up"
         if [ -e /Usr\ Backups/ ]; 
         then rm -rf /Usr\ Backups/;  (this line is the error)
         fi;;
```
 
I seem to be getting a token error with this sorry :o

---

### Post by Locke_99GS on 2009-12-08
That could be because I didn't actually look much at your script to see what it was doing. Sorry. :)

*cp -ur Usr/Pic Backups/*

Will copy (overwrite) if the source file is newer than the destination file, or if the destination does not exist. I am not sure if this is what you wanted.

Otherwise, If you want the "Backups" folder to be deleted if it is there already, then do this:

*if [ -e Backups/ ]; then rm -rf Backups/; fi;*

I'm unsure of exactly what you're wanting done. Hopefully one of those is what you're looking for.

---

### Post by Spartukus on 2009-12-08
nah it isnt quite what im looking for, im confusing my self now.
 
two directorys Backups and Usr. By default Usr has wp, ss, pic sub directorys. 
 
If i choose backup from my script I would like to copy all of the sub directorys of Usr i.e wp, ss, pic into Backups directory so it then contains the sub directorys wp, ss, pic.
 
but now i am chasing my own tail trying to work it out lol

---

### Post by Spartukus on 2009-12-08
wait I figured it out woohoo thanks for all the help guys

---

