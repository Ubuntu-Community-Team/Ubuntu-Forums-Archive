---
title: "backup script"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by jrev on 2011-01-24
Hi, I am using this script to backup my Documents :
```
#!/bin/bash
SOURCE_DIRS=/home/jean/Documents/
TARGET_DIR=/media/Documents/
point=/media/Documents


rsync -av --del --stats $SOURCE_DIRS "$TARGET_DIR"

#démonter /media/Documents/
umount /media/Documents/
umount /media/Documents/

cat /media/Documents
if mountpoint -q "$point"; then echo "$point monté"; else echo "$point démonté"; fi

echo "Backup Terminé"
``` 

When I start a new backup immediately after the first backup 
_the incremental file list should be void _
in fact 24 files are still copied from my Documents.

How can I fix this problem ?

Thanks :p

Here is copy of the execution : 


<jean@jean:~$ '/home/jean/Bureau/backup/Documents.sh' 
[B][COLOR="Blue"]sending incremental file list
./[/COLOR][/B]
Courrier/Danae4.odt
Sante/DPA/
Sante/DPA/Janvier/
Sante/DPA/Janvier/DPA1.odt
Sante/DPA/Janvier/DPA3.odt
Sante/DPA/Janvier/DPA4.odt
Sante/DPA/février/
Sante/DPA/février/DPA1.odt
Sante/DPA/février/DPA3.odt
Sante/DPA/mars/
banque/
banque/2010/
banque/2010/BPostale/
banque/2010/BPostale/aout.pdf
banque/2010/BPostale/avril.pdf
banque/2010/BPostale/decembre.pdf
banque/2010/BPostale/janvier.pdf
banque/2010/BPostale/mars.pdf
banque/2010/BPostale/octobre.pdf
banque/2010/Occitane/
banque/2010/Occitane/decembre.pdf
banque/2010/Occitane/mai.pdf
banque/2010/Occitane/novembre.pdf
banque/2011/
banque/2011/Occitane/
banque/2011/Poste/
choix de vie/signatures.odt
informatic/AROC09/
informatic/AROC09/emails.adh
informatic/SC/
informatic/SC/emails
informatic/debutant/ABC/
informatic/debutant/ABC/A_fichier.doc
informatic/debutant/ABC/Sauvegarde.doc
informatic/debutant/ABC/Sauvegarde.odt
informatic/debutant/Windows/
informatic/pedago/analyseT.odt
informatic/pedago/Fascicule_B2I/
informatic/scripts/
informatic/scripts/backup.sh
informatic/scripts/backup2.sh
photos2011/
photos2011/janvier/
photos2011/janvier/annivLily/

Number of files: 6923
Number of files transferred: 24
Total file size: 483152985 bytes
Total transferred file size: 1700504 bytes
Literal data: 1700504 bytes
Matched data: 0 bytes
File list size: 144575
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 1846930
Total bytes received: 1110

sent 1846930 bytes  received 1110 bytes  410675.56 bytes/sec
total size is 483152985  speedup is 261.44
umount: /media/Documents/ n'est pas monté (selon mtab)
cat: /media/Documents: Aucun fichier ou dossier de ce type
/media/Documents démonté
Backup Terminé  >

---

### Post by vanadium on 2011-01-24
What is the file system of the receiving drive? Using the -a option supposes both file systems fully support linux file system attributes and permissions.

---

### Post by asmoore82 on 2011-01-24
The answer to your primary question is that DOS filesystems cannot properly store
UNIX ownership and permissions or file modification times.
More specifically, NTFS's mod times are only accurate to even seconds.

The `--modify-window` option to `rsync` will reduce its accuracy to work in your situation.

But several other things in your script are puzzling...
1. why call unmount twice back to back?
    perhaps a typo?
2. why call `cat` on a directory - it only works on files;
    perhaps you meant to call `ls` on the directory? 
3. the `mountpoint` command only checks if a directory is a valid mountpoint -
    not whether or not it is currently mounted - maybe you need a `mount | grep` combo


Another note worth mentioning is that it's good practice to use lots of quotations in shell scripting -
whenever you assign or reference a variable -
as your scripts get more complex it will help eliminate sneaky bugs.

I think this does what you were after ...

```
#!/bin/bash
SOURCE="/home/jean/Documents"
TARGET="/media/Documents"

rsync -av --modify-window=2 --del --stats "$SOURCE/" "$TARGET/"

if mount | grep "$TARGET" &>/dev/null
then
    #démonter /media/Documents/
    umount "$TARGET"

    #cat /media/Documents
    #^??? ls /media/Documents

    echo "$TARGET démonté"
fi

echo "Backup Terminé"
```

---

### Post by jrev on 2011-01-24
> **vanadium said:**
> What is the file system of the receiving drive? Using the -a option supposes both file systems fully support linux file system attributes and permissions.

FAT32 is the best system to transfer data files from one PC to another.
Have you ever tried to transfer a folder "Documents" from one Linux system to another with a USB key in ext3 ?
Then try it and you will understand.

As far as my documents are concerned the permissions should not restrict the transfer or alter the content of the files 
:D

---

### Post by jrev on 2011-01-24
> **asmoore82 said:**
> The answer to your primary question is that DOS filesystems cannot properly store
UNIX ownership and permissions or file modification times.
More specifically, NTFS's mod times are only accurate to even seconds.

The `--modify-window` option to `rsync` will reduce its accuracy to work in your situation.

But several other things in your script are puzzling...
1. why call unmount twice back to back?
    perhaps a typo?
2. why call `cat` on a directory - it only works on files;
    perhaps you meant to call `ls` on the directory? 
3. the `mountpoint` command only checks if a directory is a valid mountpoint -
    not whether or not it is currently mounted - maybe you need a `mount | grep` combo


Another note worth mentioning is that it's good practice to use lots of quotations in shell scripting -
whenever you assign or reference a variable -
as your scripts get more complex it will help eliminate sneaky bugs.

I think this does what you were after ...

```
#!/bin/bash
SOURCE="/home/jean/Documents"
TARGET="/media/Documents"

rsync -av --modify-window=2 --del --stats "$SOURCE/" "$TARGET/"

if mount | grep "$TARGET" &>/dev/null
then
    #démonter /media/Documents/
    umount "$TARGET"

    #cat /media/Documents
    #^??? ls /media/Documents

    echo "$TARGET démonté"
fi

echo "Backup Terminé"
```

[B][I][COLOR="Blue"]My only question is why this script copy again the same 24 files that have just been copied in the preceding copy ?
[/COLOR]
[/I][/B] ;)

**[COLOR="Blue"]I will try your copy Thanks[/COLOR]**

---

### Post by CharlesA on 2011-01-24
> **jrev said:**
> FAT32 is the best system to tranfer from one PC to another.
Have you ever tried to transfer a folder "Documents" from one Linux system to another with a USB key in ext3 ?
Then try it and you will understand.
As far as my documents are concerned the permissions should not restrict the transfer 
:D

You can do that, but you may have to change the owner and group on the files/directories.

If the UID of the user is the same on both machines, then you don't need to do anything.

---

### Post by vanadium on 2011-01-25
> **jrev said:**
> [B][I][COLOR="Blue"]My only question is why this script copy again the same 24 files that have just been copied in the preceding copy ?
[/COLOR]
[/I][/B] ;)

**[COLOR="Blue"]I will try your copy Thanks[/COLOR]**
The question was answered indeed. Look up "man rsync" for --modify-window.

fat is definitely not the best file system to transfer files. You can use ext. If you want the files to be copied onto another system, permissions must be set obviously for the user wanting to copy the files.

---

### Post by jrev on 2011-01-26
Thanks Vanadium,
I must say I adopted your script and everything is OK up to now

Many thanks to everybody !:p

How do I mark this thread solved ?

---

### Post by vanadium on 2011-01-26
> **jrev said:**
> Thanks Vanadium,
I must say I adopted your script 
All credit goes to asmoore82, who took the opportunity to give all of us a little crash course in elegant scripting.

---

