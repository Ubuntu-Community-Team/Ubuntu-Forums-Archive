---
title: "Another Scripting issue"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by sreaney89 on 2011-04-12
echo "Replication of file command? Yes or No"
read YESORNO
case "$YESORNO" in
[Yes]*) ls *.c* ;;
[No]*) ls * ;;
*) echo "Sorry, don't understand" ;; 
esac

i have to replicate the file command, i tried doing it via this to find the program files, i have to use a case statement.. 

any advice?

---

### Post by f1tz on 2011-04-12
The major problem with your script is on this line:
[I]
*) echo "Sorry, don't understand" ;; [/I]

in your "don't", you have a quote that isnt escaped. Replace it with \'
This should work:
```
#!/bin/sh
echo "Replication of file command? (yes/no or y/n)"
read YESORNO
case $YESORNO in
yes|y) ls *.c* ;;
no|n) ls * ;;
*) echo "Sorry, don\'t understand" ;;
esac
```Also... I'm not sure why you're using *ls ** that would list the contents of the subdirectories as well as your current working directory. Perhaps use just *ls* instead, if that's not your intent?

---

### Post by sreaney89 on 2011-04-12
the fact that im using virtual box ubuntu, would that mean that there is no c drive?

---

### Post by hakermania on 2011-04-12
there is not C: drive in ubuntu.
If you'd like to ls the up up up up up directory, type ls /

---

