---
title: "Convert a BIN Image from linux clonecd to ISO 9660 file ?"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-08-17
Hello, 

I usually clone the cdrom with this command for bit to bit exact copy:
```
 readom dev=$THECDDEV  -clone -nocorr f="${szSavePath}.bin"
```

How can we convert those to ISO 9660 general standard ?

Regards

---

### Post by frenchn00b on 2010-08-17
I found this for but to convert *.toc to cue no easy :-(

 [http://wiki.linuxquestions.org/wiki/CD_Image_Conversion](http://wiki.linuxquestions.org/wiki/CD_Image_Conversion)

```
       149 Aug 17 14:16 file.bin.toc
 355750704 Aug 17 14:18 file.bin

```


my *.TOC content of file gives:
> 
&#65533;&#65533;&#65533;
&#65533; 0     )29(
            "'7


---

### Post by Hospadar on 2010-08-17
[http://www.ubuntugeek.com/how-to-convert-bincue-files-to-iso-in-ubuntu.html](http://www.ubuntugeek.com/how-to-convert-bincue-files-to-iso-in-ubuntu.html) - second result on google

Also you can just dump them straight to iso, no need for bin/convert.  I forget exactly how to do this, but I'm pretty sure you can ```
#it might not be exactly /dev/cdrom0 for you, could be just cdrom, or cdrom1, take a look and see what you have
#'if' is "infile", 'of' is "outfile
dd if=/dev/cdrom0 of=/home/$USER/filename.iso
# you might need to sudo:
sudo dd if=/dev/cdrom0 of=/home/$USER/filename.iso
```If this command doesn't work, I just got some of the syntax wrong, dd is the command line tool to dump block devices (**d**ump **d**isk) (cd drive, hard drives, etc) to files, so do some googling for "dd dump cd to iso ubuntu" and you'll certainly come across pertinent informtion

---

