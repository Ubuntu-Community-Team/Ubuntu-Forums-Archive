---
title: "What is the linux alternative to Windows Clonecd?"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-06-06
What is the linux alternative to Windows Clonecd?

---

### Post by Gone fishing on 2010-06-06
I like the utility disk Parted Magic [http://partedmagic.com/](http://partedmagic.com/)

I clone Windows partitions with the ntfsprogs that come with most distros (and are in parted magic). I use ntfsclone to make an image (this is remarkably fast) and to deploy the image is remarkably fast too.

---

### Post by aeiah on 2010-06-06
[dd](http://en.wikipedia.org/wiki/Dd_(Unix))

---

### Post by frenchn00b on 2010-06-06
cat /usr/bin/clonecd 
```
#!/bin/sh
if [ "$1" == "--help" ] ; then 
	cat /etc/fstab | grep cdrom 
	exit
	exit 0
fi
readom dev=$1 -clone -nocorr f="$2"
```

---

### Post by mapes12 on 2010-06-06
Check out K3b and K9copy. Their both in Synaptic.

---

### Post by frenchn00b on 2010-06-06
> **mapes12 said:**
> Check out K3b and K9copy. Their both in Synaptic.

what about those format of k3b and k9copy? are they compatible wiht each other, and also the one from readom ? 

For ccd, there is a converter in the repositories

---

### Post by frenchn00b on 2010-08-07
A better version

```

#!/bin/bash
# coded by Frenchn00b

if [ "$1" = "--help" ] ; then 
        echo "type -clone or -image for arg1 to do copy using readom with cloning to bin file or copying regular to iso"
        exit
        exit 0
fi

if [ "$1" = "-help" ] ; then 
        echo "type -clone or -image for arg1 to do copy using readom with cloning to bin file or copying regular to iso"
        exit
        exit 0
fi

if [ "$1" = "" ] ; then
        echo "type -clone or -image for arg1 to do copy using readom with cloning to bin file or copying regular to iso"
        exit
        exit 0
fi



########## detecting the CD-ROM
echo "---"
notify-send  " Detecting the device of the cdrom ..."
echo " Detecting the device of the cdrom ..."
THECDDEV=`cdrecord -scanbus | grep CD-ROM | cut -f2 | head -n 1`
echo "The found result for device is:  $THECDDEV" 
echo "---"
if [ "$THECDDEV" = "" ] ; then
        MSG="No CD-ROM device has been found. Aborted."
	zenity --info  --text="$MSG" &
	echo "$MSG"
	notify-send "$MSG"
	cdrecord -atip
	cdrecord -scanbus
        exit
        exit 0
fi





if [ "$1" = "-clone" ] ; then
        notify-send "Clone mode: CD-ROM to image BIN file"
	notify-send "Press OK, and enter the filename to save the file (without extension)"  ; szSavePath=$(zenity --file-selection --save --confirm-overwrite);echo $szSavePath
	readom dev=$THECDDEV  -clone -nocorr f="${szSavePath}.bin"
        MSG="$(date) CD-ROM has been cloned, $(ls -ltrah ${szSavePath}.bin)"
fi

if [ "$1" = "-image" ] ; then
        notify-send "Image mode: CD-ROM to image ISO file"
	notify-send "Press OK, and enter the filename to save the file (without extension)"  ; szSavePath=$(zenity --file-selection --save --confirm-overwrite);echo $szSavePath
        readom dev=$THECDDEV  f="${szSavePath}.bin"
        MSG="$(date) CD-ROM has been copied, $(ls -ltrah ${szSavePath}.bin)"
fi

if [ "$1" = "-burn" ] ; then
        notify-send "Burn ISO/BIN to CD-ROM"
	FILE=`zenity --file-selection --title="Select a File"` ; echo "$FILE"
        notify-send "$FILE selected"
        echo  "$FILE selected"
	cdrecord -v -eject dev="$THECDDEV" "$FILE"
	MSG="$(date) CD-ROM has been burnt, $(ls -ltrah ${FILE})"
fi


if [ "$1" = "-burnfolder" ] ; then
        notify-send "Burn folder mode to CD-ROM"
	FILE=`zenity --directory --file-selection --title="Select a File"` ; echo "$FILE"
        notify-send "$FILE selected"
        echo  "$FILE selected"
	mkisofs -r -R -J -l -L "$FILE" | cdrecord dev="$THECDDEV" -v --eject  -
        MSG="$(date) CD-ROM has been burnt"
fi

zenity --info  --text="$MSG" &
echo "$MSG"
notify-send "$MSG"

##backup folder to cd: mkisofs -r -R -J -l -L /home/user1 | cdrecord dev=0,4,0 -v --eject speed=4 -


```

---

