---
title: "Check file type command?"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by SpinningAround on 2010-05-14
I'm working on a script to mount iso or img file, by combining these two 
[http://ubuntuforums.org/showpost.php?p=854720&postcount=2](http://ubuntuforums.org/showpost.php?p=854720&postcount=2)
[http://www.ubuntugeek.com/mount-isos-easely-in-gnome-nautilus.html](http://www.ubuntugeek.com/mount-isos-easely-in-gnome-nautilus.html)

Since it feel slightly unnecessary to create two script, do i wonder how I can determine if the file is img, iso or neither?

---

### Post by -humanaut- on 2010-05-14
ls -F *

*=File location

Will list the file extension not sure if thats what your looking for or not?

---

### Post by mali2297 on 2010-05-14
The easiest would be to use the file extension. A simple script can look like this:
```

#!/bin/sh

if [ -f $1 ]; then
  case $1 in
    *.img) mount -t udf -o loop $1 /media/temp ;;
    *.iso) mount -t iso9660 -o loop $1 /media/temp ;;
    *) echo "Unrecognized file" ;;
  esac
fi

```

It tests that the command line argument is an existing file and then checks if the file name ends with .img or .iso or just anything.

---

### Post by sisco311 on 2010-05-14
Use the *file* command:
```
file -b path/to/file
```

I didn't test it, but something like this should work:
```

FILE=path/to/file
ISO="ISO 9660 CD-ROM filesystem data 'CDROM                          ' (bootable)"
IMG="*output of the file command for an img file*"
TYPE="$(file -b "$FILE")"

if [ "$TYPE"=="$ISO" ]; then 
  ...
elif [ "$TYPE"=="$IMG"]; then 
  ...
else 
  ...
fi
```

---

### Post by SpinningAround on 2010-05-15
I tried using ls -F /path/to/file but it only return the same. file -b works better it return following for a img file. I think it can work if it's possible to remove the 'Title' part.
```
# UDF filesystem data (version 1.5) 'Title'
```

---

### Post by mali2297 on 2010-05-15
> **SpinningAround said:**
> I tried using ls -F /path/to/file but it only return the same. file -b works better it return following for a img file. I think it can work if it's possible to remove the 'Title' part.
```
# UDF filesystem data (version 1.5) 'Title'
```

You can extract the first (say) three characters with *cut*:
```

file -b path/to/file | cut -c1-3

```
This should then give you either 'UDF' or 'ISO'.

---

### Post by SpinningAround on 2010-05-15
Thanks for all the answers, I'm almost got the script working but there is some problem regarding '$*'. It return the absolute path to the file instead of only the file name.

[PHP]
#!/bin/bash
#
# nautilus-mount-iso

gksudo -u root -k /bin/echo "Enter your password for root terminal access"
zenity --info --text "TEST /media/$*/"
TYPE = "$(file "$*" | cut -c 3-6)"
if [-d /media/"$*" ]; then
	if [ zenity --question --title "ISO Mounter" --text "Unmount $*?" ]
		sudo umount "$*" 
		zenity --info --text "Successfully unmounted /media/$*/"
		sudo rmdir "/media/$*/"
		exit 0
	else
		exit 1
	fi
else
	sudo mkdir /media/"$*"
	if [ "$TYPE"==ISO ]; then
		if [ sudo mount -o loop -t iso9660 "$*" /media/"$*" ]; then
			zenity --info --title "ISO Mounter" --text "$* Successfully Mounted."
			exit 0
		else
			sudo rmdir /media/"$*"
			zenity --error --title "ISO Mounter" --text "Cannot mount $*!"
			exit 1
		fi
	elif [ "$TYPE"==UDF ]; then
		if [ sudo mount -t udf -o loop $1 /media/"$*" ]
			zenity --info --title "ISO Mounter" --text "$* Successfully Mounted."
			exit 0
		else
			sudo rmdir /media/"$*"
			zenity --error --title "ISO Mounter" --text "Cannot mount $*!"
			exit 1
		fi
	else
		sudo rmdir /media/"$*"
		zenity --error --title "ISO Mounter" --text "Cannot mount $*!"
		exit 1
	fi
fi
[/PHP]

---

