---
title: "Libre Office exits after splash screen"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by fsodano on 2011-08-22
Hello Everyone, how are you?

I'm don't use Libre office (or any other office suite) too often, so I don't know exactly when it stopped working, but I do know that it was working before.

The problem, as the title says, is that LibreOffice won't start after the splash screen disappears (the progress bar always remains in 0%), it doesn't give an error, warning, nothing.

I have tried the possible solutions given in this forum and the web, but none seem to work.

I have renamed my ~/.libreoffice folder to something else, and the folder gets created again, but it still won't start.

I have tried running it from the terminal, but it won't throw any errors either.

I ran this code: ```
strace -f -o outputfile /usr/bin/libreoffice
``` and this was the output: [http://tinypaste.com/f87b1]("http://tinypaste.com/f87b1") which, from what I can tell has something to do with a timeout problem.

I don't know what else to do :(

Any help is appreciated.

Cheers!

EDIT: This was solved by completely removing all the packages, rebooting and reinstalling, as per 123456789123456789123456's answer.

---

### Post by 123456789123456789123456 on 2011-08-23
I've read through the output.  seems to be in a loop error, the main thing that cought my attention, is that it is trying to access a file, and keeps returning no file or directory, this appears multiple times, and always the same file trying to be accessed.  The only suggestion I can think of, try to go to the synamptic package manager, search for the office program, tell synamptic to completely remove the application, this uninstalls the program, and deletes the install packages, then mark them again for installation, this will cause the system to download the install packages again insuring a fresh copy, and install the program again.  See if that resolves the issue.  you can also have synamptic check for and repair brocken packages before this, to see if that works for you.

---

### Post by fsodano on 2011-08-23
Thanks 123456789123456789123456, I completely removed it (I had done it before, but maybe I missed a package), installed it again, and now it's working again.

Cheers!

---

### Post by yoramdavid on 2011-12-10
Hello all,

Shall I use this threat or start my own?
I have the exact same problem as described by fsodano with one difference:

```
strace -f -o outputfile /usr/bin/libreoffice
```
Does not return anything at all.

I removed the ~/.libreoffice but no luck with that either. (I made a backup, yes).
LibreOffice just remakes a folder with just one file inside a tree of folder about java settings.
I ran <code>openoffice -norestore</code>
with no difference.

I am out at sea with very limited Internet connection and removing the package and reinstalling it is not an option as it is I believe 150 Mb?

Another difference from fsodano: I use libreoffice very often and know exactly when that happened: After restoring a backup with srestore.

can any one help?

---

### Post by yoramdavid on 2011-12-11
There was an LibreOffice update, that repaired the installation and it works now.

---

