---
title: "script owned by root with setuid bit enabled being denied access to a file"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by jimmybarcelona on 2009-08-14
Okay, so here's the deal. (This is my first ever shell script, and I'm sooo close...)

I want to make a shell script to backup the important files in my home folder and my wife's home folder. So I make a shell script as follows:
#!/bin/bash

```
tar -cvpT fileList.txt 2> "backup report.txt" | gpg -er myself@gmail.com | ssh 192.#.#.# "cat > laptopBackup-8-14-09.tar.gpg"
```

The script works, it just shows errors because I don't have access permission to some of the files in my wife's home folder. Now I know I can just use sudo and chmod to give myself permission to all of her files, but I thought it would be easier to just run the shell script as root and not worry about it. So I use chown and make root the owner of the script and enable the set userid bit with chmod.

```
Desktop/Mp3s I lost/800806_01.wav
Desktop/Mp3s I lost/800908_01.wav
Desktop/Mp3s I lost/800709_01.wav
Desktop/Mp3s I lost/800825_01.wav
Desktop/Mp3s I lost/800906_01.wav
Desktop/Mp3s I lost/800906_03.wav
Desktop/Mp3s I lost/800822_01.wav
Desktop/Mp3s I lost/800803_01.wav
Desktop/Mp3s I lost/800709_02.wav
tar: Desktop/Pictures: Cannot open: Permission denied
Pictures/My Pictures/DSCF0770.JPG
Pictures/My Pictures/DSCF0765.JPG
tar: Pictures/My Pictures/DSCF0753.JPG: Cannot open: Permission denied
Pictures/My Pictures/DSCF0769.JPG
Pictures/My Pictures/DSCF0756.JPG
Desktop/Hubby's Corner.desktop
```

If the script is running as root, why is it being denied access to a directory and a .jpg file? below are the permissions for the script and of the 2 files that are denying root access.....

```
-rwsr-xr-- 1 root     Jim 216 2009-08-14 13:02 personalBackup
drwx---r-x 2 Michelle Jim  4096 2009-06-14 12:02 Pictures
-rwxrwxrwx 1 Michelle Michelle  784245 2003-12-31 23:02 DSCF0754.JPG
```

??? Please advise....

---

### Post by andrewc6l on 2009-08-14
I think Ubuntu is like most modern Unix variants in that it ignores setuid/setgid on shell scripts for security reasons.

If you want to, you can build a C wrapper like this one:
[http://ubuntuforums.org/showthread.php?t=1123639&page=2](http://ubuntuforums.org/showthread.php?t=1123639&page=2)

Not the prettiest, but it means you don't have to sudo to run your script :-)

---

