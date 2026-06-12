---
title: "changing folder permission"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by duceduc on 2011-03-10
I am trying to change permission on some folders I have created. However, each time I input the chmod cmd, the file doesn't change. It stays the same. Here is the cmd I used.

> 
sudo chmod -R 0444 /path/to/my/folder


---

### Post by mcduck on 2011-03-11
First, if the directories are something you ave created as your own user, they already belong to that user and there's absolutely no need to use "sudo" in that command. You already have the right to access and modify files and directories you own.

Anyway, is the directory located on a Windows file system (FAT or NTFS)? Those don't understand ownerships and permissions as they are used in Linux & Unix systems, so you can't set te permissions of individual files or directories on them , instead permissions are applied to the whole file system at the time it's mounted.

Same goes for any optical medias, the file systems used on those can't handle ownerships and permissions, and are also read-only by definition. So no chown/chmod on CDs or DVDs either...

---

### Post by asmoore82 on 2011-03-11
_[COLOR="Red"]**You should never `chmod -R` with number codes!**[/COLOR]_

This is the probably the #1 piece of bad advice
that's littered all over the forums and google searches.

Directories need to be executable but regular files do not.
There is simply no way to express this with number codes.

`chmod` has somewhat lesser known symbolic letter codes that are much
better for use with `-R`. The codes are fairly self explanatory:
'a+r' means "add Read for All"
'go-w' means "remove Write for Group and Others"
'g=u' means "copy User perms. to Group"

The "magic" letter code that's not immediately obvious is the _capital_ "X"
This means "execute only for directories and executables[COLOR="Purple"]*[/COLOR]"

So, the problem with your `chmod -R 0444 ...` is that it will always remove
executable from all directories. Likewise, `chmod -R 555` is no good because
it will always add executable to all files. The proper thing to do is this:
```
chmod -R a+rX,a-w /path/to/folder
```
^Note the capital "X"!!
This means "Recursively allow Read for All and deny Write for All."

[COLOR="Purple"]*[/COLOR]The "Wizard Behind the Curtain" that allows the letter codes
to automagically know when to add execute to programs is that it checks to 
see if the program is already executable by anyone else.

So, say you have 1 directory with 1 file and 1 executable script.
And you want to properly allow read/execute to this location for everyone.
It currently looks like this:
```
drwxr-x--- [COLOR="Blue"]folder[/COLOR]
-rw-r----- folder/readme.txt
-rwxr-x--- [COLOR="Lime"]folder/script.bash[/COLOR]
```

The proper command to run is: ```
chmod -R a+rX folder
```
This knows to add execute to "folder" because it is a directory;
It knows not to add execute to "readme.txt" because it is a plain file;
and It knows to add execute to "script.bash" because it is already
executable for the owner. So you end up with this:
```
drwxr-xr-x [COLOR="Blue"]folder[/COLOR]
-rw-r--r-- folder/readme.txt
-rwxr-xr-x [COLOR="Lime"]folder/script.bash[/COLOR]
```
^Perfect!

:D I'm not all boring &#8212; I use the numeric chmod codes all the time, just not with Recursion!

---

### Post by duceduc on 2011-03-11
Thanks for the replys. The folders are from an external hdd and it was mounted  FAT32.

---

### Post by mapes12 on 2011-03-13
I do this the GUI way. Launch Nautilus like this ```
gksudo nautilus
```Go to the folders where you want to change permissions. Right click then select the Permissions tab. Set the permissions how you want them then close nautilus.

You're good to go.

Mark

---

### Post by duceduc on 2011-03-13
It's a server edition. No gui

---

### Post by rosencrantz on 2011-03-13
> **duceduc said:**
> The folders are from an external hdd and it was mounted  FAT32.
There's the rub: fat32 doesn't support setting linux-style folder permissions. You can only set permissions partition-wide while mounting. Check this article: [http://ubuntu.swerdna.org/ubufat32.html](http://ubuntu.swerdna.org/ubufat32.html)

Cheers,
rosencrantz

---

### Post by Morbius1 on 2011-03-13
If you want the whole partition to have what I think was your intent ( 0444 - read only by everyone and not executable ) you're going to have to deviate from swerdna's example:
> UUID=AD74-85CA /path_to/mount_point vfat umask=0000,utf8 0 0Something like this I think would be more appropriate:
> UUID=AD74-85CA /path_to/mount_point vfat dmask=0222,fmask=0333,utf8     0 0This will make all directories have permissions of 555 - Everyone can open and read the contents of the mount point.

And all files will have permissions of 444 - Everyone can read but not write or execute.

The umask parameter for a Windows filesystem is the equivalent of the "-R" option in chmod'ing a Linux file system with number codes. Unlike Linux filesysems all folders and files start out as 777. There's no way to enable the execute bit on folders ( which you must do ) without enabling them on files ( which you do not want to do ) using umask. The dmask / fmask options separate umask into it's directory ( dmask ) and file ( fmask) components.

Besides we don't want asmoore82 to yell at us again :wink:

---

### Post by rosencrantz on 2011-03-13
right, sorry, I was too lazy to adapt it...

---

