---
title: "Finding files and list their storage usage"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by Linux noob magican on 2011-06-30
Hello!  *First post* ):P


I was using the terminal to check how much hd space my video files was taking but couldn't figure out how to do it.

I understand i need to use this:

find / -iname '*.mpg'

tried this but i didn't work

find /-iname '*.mpg' | ls -sh

Anyone know how? ;)

---

### Post by Ozymandias_117 on 2011-06-30
Are they all in one folder?

---

### Post by Linux noob magican on 2011-06-30
no they are not, they are spread across the computer.

---

### Post by dFlyer on 2011-06-30
Have you looked in the folder you downloaded them to. If so just cd to the folder and enter du and press enter.

---

### Post by Ozymandias_117 on 2011-06-30
This is probably a little overcomplicated, but this should find any instance of a file ending in .mpg on your computer, add up the sizes, and print it as Megabytes and Gigabytes.

```
#!/bin/bash

if [[ ! -e tmp ]]
then
  TOT_SIZE=0
  FILE_TYPE="*.mpg" #Simply change this to the filetype you want to search for.

  #Search in ~ /mnt and /media - Those are the only places that should have user data
  find ~ -iname "$FILE_TYPE" > tmp
  find /mnt -iname "$FILE_TYPE" >> tmp
  find /media -iname "$FILE_TYPE" >> tmp

  while read line
  do

    SIZE=$(du -m "$line" | gawk '{ print $1 }') #I like gawk. :)
    TOT_SIZE=$(($TOT_SIZE + $SIZE))

  done < ./tmp

  printf "%i Megabytes or about %i Gigabytes\n" "$TOT_SIZE" "$(($TOT_SIZE / 1024))"
  rm ./tmp

else

  echo "There is already a file or folder named tmp in the folder you're running this script from."
  echo "It must be moved/removed for this script to work"

fi
```

Save it to a file, then run these commands:```
cd ~/path/to/script
chmod +x script
./script
```

---

### Post by Linux noob magican on 2011-06-30
That was indeed over complicated, but very interesting. 

I shall try to use it when i get home.


Thank you very much.

---

### Post by Linux noob magican on 2011-06-30
It works perfect. Thanks again.

---

