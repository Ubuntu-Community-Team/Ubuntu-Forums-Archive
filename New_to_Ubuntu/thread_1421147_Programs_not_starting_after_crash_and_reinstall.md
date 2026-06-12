---
title: "Programs not starting after crash and reinstall"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by asharpham on 2010-03-03
Recently Ubuntu crashed and I reinstalled it. Then I restored from a backup and redownloaded the programs I had previously installed. Some of these just won't run. Two of them are aMSN and VLC. I decided to totally remove them and reinstall again, but it made no difference. Does anyone have an idea why some of my programs are doing this?

Alan.

---

### Post by ImperialXT on 2010-03-03
try starting them from a terminal and see if they print out any errors into the terminal

---

### Post by asharpham on 2010-03-04
I really am new at this. I don't know where the executable file is located or what it's called. For examople, one of the files is vlc. Where will I find it so I can try to start it in Terminal? I tried "locate" but got too many files and have no idea which is the executable file. I know in windows it would have an exe extension, but what does it have in Ubuntu?

Alan.

---

### Post by ImperialXT on 2010-03-04
try just typing "vlc" into the terminal.

---

### Post by isparkes on 2010-03-04
You can see if a file is executable by doing 

```
ls -la
```

This will show you 10 letters and/or dashes on the left of the file name

-rwxr-xr-x  1 ian  ian        288 2009-11-18 10:24 sendmails.sh
-rw-r--r--  1 ian  dip      18342 2010-02-12 11:18 sequencer_ins.sql

Forget the first one for the moment, the others are in three groups:

owner (the person who created the file)
group (people who share a group with the owner)
other (everyone else)

Within the three groups there are three positions
r (can read the file)
w (can write/delete the file)
x (can execute the file)

So taking this example

-rwxr-xr-x  1 ian  ian        288 2009-11-18 10:24 sendmails.sh

ian (who created the file) can read, write (=modify or delete it) and execute the file

anyone in group "ian" can read and execute it

anyone else can read and execute it.

More information is here:

[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

---

### Post by asharpham on 2010-03-04
When I typed "vlc" into terminal I got:
VLC media player 1.0.2 Goldeneye
[0x9a350d0] main demux error: possibly corrupt module cache
[0x9a34c80] main interface error: possibly corrupt module cache
[0x9a34c80] main interface error: no suitable interface module
[0x999c140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x999c140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9a34c58] main interface error: possibly corrupt module cache
[0x9a34c58] main interface error: possibly corrupt module cache
Remote control interface initialized. Type `help' for help.

I'm not sure that uninstalling it and reinstalling it will help as I've already done that and the above is the result. When i uninstalled, i did it through synaptic and selected complete removal.

sbackup is another program that won't work. The items appear in System-->Administration but if I try and run them I just get "Could not launch 'Simple Backup Config'. Failed to execute child process "su-to-root" (No such file or directory)." I completely removed it and reinstalled but it does the same.

I don't know what to do to get these programs working.

By the way, thanks isparkes for your explanation of the attributes.

---

### Post by mikechant on 2010-03-04
You could try deleting the .vlc directory from your home directory. You may need to turn on 'show hidden files' in your file manager (under edit/preferences in Nautilus if I remember correctly) to see this file.
Then try running from the command line again and see if you get the same errors.

---

### Post by asharpham on 2010-03-04
I could not find a .vlc file even with "Show Hidden files" ticked.

---

### Post by asharpham on 2010-03-05
I decided to reinstall Ubuntu so my problem is no longer relevant. Thanks to all who tried to help.

Alan

---

