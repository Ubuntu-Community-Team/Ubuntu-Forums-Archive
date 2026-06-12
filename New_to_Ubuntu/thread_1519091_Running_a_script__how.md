---
title: "Running a script  how?"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by jfbooth on 2010-06-27
I have a file downloaded to my DOWNLOAD directory.  It is named:

124401-filecleaner.sh

and here are the permissions on it:

-rwxr-xr-x 1 jb jb 2638 2010-06-27 14:26 124401-filecleaner.sh

The author stated it required something called ZENITY and according to my PACKAGE MANAGER, ZENITY is installed on my machine.

I know it is near insane to run scripts downloaded from the Internet .. especially one designed to 'clean up junk files' .. so **I probably won't run it**.  I thought of this after TRYING to run it and it failed.  I will say, it is from a fairly trusted source.  SO, with the idea that I probably will delete the download and forget it, how WOULD I run it, NOOB that I am?

Here are my previous attempts:

jb@jb-desktop:~/Downloads$ ls
124401-filecleaner.sh

jb@jb-desktop:~/Downloads$ chmod +x 124401-filecleaner.sh
jb@jb-desktop:~/Downloads$ ls -l 124401-filecleaner.sh
-rwxr-xr-x 1 jb jb 2638 2010-06-27 14:26 124401-filecleaner.sh

jb@jb-desktop:~/Downloads$ 124401-filecleaner.sh
124401-filecleaner.sh: command not found
jb@jb-desktop:~/Downloads$ 124401-filecleaner
124401-filecleaner: command not found
jb@jb-desktop:~/Downloads$ 

I THINK I made the file executable and tried to execute it by typing its name .. with extension and without extension .. and failed.

Comments, corrections, criticisms, and advice welcome and appreciated in advance.

---

### Post by r_s on 2010-06-27
it's a bash script you can run it using *bash filename* or using *./filename*

---

### Post by jfbooth on 2010-06-27
> **r_s said:**
> it's a bash script you can run it using *bash filename* or using *./filename*

understand:

jb@jb-desktop:~/Downloads$ ./124401-filecleaner.sh

should run it.   THANK YOU.

---

