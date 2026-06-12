---
title: "Backlight From Terminal"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by hackerseraph on 2010-07-21
I'm looking for a bash script that will let me control the backlight. Anyone know how?

---

### Post by hackerseraph on 2010-07-21
Ok, I've been looking around all day and I've come up with a way to do it :] yay me.

So I went to my /proc/acpi/video/ folder and since my laptop's built in screen is vga, i clicked on the vga folder and since im trying to control brightness the file im looking to control and edit the path i need to type is 

```
/proc/acpi/video/VGA/LCDD/brightness

```
continuing on, i opened the brightness folder (read only) and saw that it lists the brightness settings in numbers (the lowest being the dimmest, the highest number being the brightest) and i noticed below that my brightness is listed. (I double checked this number by changing my brightness and reopening the file)

So, I figured there must be a way to change that number. So I did some further research and learned that echo -n [VALUE] will change that number to your select brightness

Therefore,

```
echo -n 1 > /proc/acpi/video/VGA/LCDD/brightness
```

inside my script will adjust the brightness BUT theres that small problem of that file being read only because its an acpi system file. So, i have to append chmod 777 to my script. (chmod 777 stands for change mode 777 relating to binary 111 standing for read write execute allow me to change the file and use those changes)

Conclusively,

if one wants to change their brighness through the terminal they will have to first

```
sudo chmod 777 /proc/acpi/video/VGA/LCDD/brightness

```
then

```
echo -n [VALUE] > /proc/acpi/video/VGA/LCDD/brightness

```
and then it works

---

### Post by jthechemist on 2010-08-01
Here's a couple of bash scripts I wrote to increment/decrement  the backlight brightness. If you set up a pair of hotkeys to invoke  them, you can replace any screen brightness controls that were set up  during install. They should work regardless of what the actual brightness levels defined for your system are...

Here is backlight_up.sh:
```

#!/bin/bash

# Edit BRIGHT_FILE to point to the right location
BRIGHT_FILE="/proc/acpi/video/VGA/LCD/brightness"

# Grab the info from BRIGHT_FILE
LEVELS=`awk '$1=="levels:"{print $0}' $BRIGHT_FILE`
MAX_LEVEL=`awk '$1=="levels:"{print $NF}' $BRIGHT_FILE`
CURRENT_LEVEL=`awk '$1=="current:"{print $2}' $BRIGHT_FILE`

# Running this loop will update the backlight to one level higher than the current one
UPDATE="not_yet"
for i in $LEVELS; do
  if [ $UPDATE = "now" ]; then
    echo -n $i > $BRIGHT_FILE
    break
  fi  
  if [ $i = $CURRENT_LEVEL ]; then UPDATE="now"; fi
done

```And here is backlight_dn.sh:
```

#!/bin/bash

# Edit BRIGHT_FILE to point to the right location
BRIGHT_FILE="/proc/acpi/video/VGA/LCD/brightness"

# Grab the info from BRIGHT_FILE
LEVELS=`awk '$1=="levels:"{print $0}' $BRIGHT_FILE`
MIN_LEVEL=`awk '$1=="levels:"{print $2}' $BRIGHT_FILE`
CURRENT_LEVEL=`awk '$1=="current:"{print $2}' $BRIGHT_FILE`

# Running this loop will update the backlight to one level lower than the current one
LAST_LEVEL=`awk '$1=="levels:"{print $2}' $BRIGHT_FILE`
for i in $LEVELS; do
  if [ $i = $CURRENT_LEVEL ]; then
    if [ $CURRENT_LEVEL -gt $MIN_LEVEL ]; then echo -n $LAST_LEVEL > $BRIGHT_FILE; fi
    break;
  fi
  LAST_LEVEL=$i
done

```Notes:
1. Make sure to change BRIGHT_FILE to point to the appropriate  file.  For me that is /proc/acpi/video/VGA/LCD/brightness, but yours may  be  different.
2. Make sure to change the write permissions on the file pointed to by BRIGHT_FILE as noted above.

Maybe this can be of use to someone. And to all the posters above who found the original solution: Thank You! :D

---

