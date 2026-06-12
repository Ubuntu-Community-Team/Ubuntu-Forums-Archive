---
title: "Changing directory in Terminal"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by SnabelAir on 2009-05-16
Hello guys!
I'm a lifetime Windows user and I've solved  throu a douzen problems the last 24hs in my newly installed Ubuntu! I love Ubuntu already and lots of prejudices about linux has so far not been true. :)

Just wanted to see if anyone of you could help me, the user guides couldnt. :) Not ever the old Google gave any good answer (or at least they were to complicated):
Im trying to install drivers for my G15 keyboard and got very happy when finding "G15 Daemon" for Linux systems! After downloading it I'm in a folder and (as old Windows user) looking for Install.exe. Obviously there were no such file and the readme-file says:
"Ok browse to the directory where you extracted the daemon to. 
As a user or root type 
./configure 
make 

Then as root type
make install"
So far so good, after launching Terminal I cannot change directories! Ive logged in as ROOT but when using "dir" to see which folders I could browse into I only get "No such file or folder" when typing for example "cd /dekstop" even thou the "desktop" folder appears with both the "dir" and the "ls" commands. 

Anyone knows what the error is? Why can't I browse into folders?
Greatful for answer,
Andreas

---

### Post by drs305 on 2009-05-16
In linux everything is case dependent, so your desktop is "Desktop". 

**cd $HOME/Desktop** should get you there.

---

### Post by rohedin on 2009-05-16
What you're trying to do is browse to /directory. In Linux / reffers to the root folder of the computer, the equivalent of C: in Windows. If you wish to browse to a sub-directory of the current folder you should use:
cd ./name-of-folder

This is a common mistake. Also note that the desktop folder is called Desktop and not desktop, be careful as Linux is case-sensitive.

---

### Post by leandromartinez98 on 2009-05-16
The desktop is in /home/yourusername/Desktop

you can change to it by typing

cd ~/Desktop

The "~" is a shortcut to "/home/yourusername"

Be aware that the filenames are case-sensitive, so that "Desktop" is different from "desktop".

Here is a guide of Linux directory structure:

[http://www.debianadmin.com/linux-directory-structure-overview.html](http://www.debianadmin.com/linux-directory-structure-overview.html)

---

### Post by Kimm on 2009-05-16
Also, if the directory you want to navigate to is in the directory that you are in, you can just do:

cd Desktop

no prefixes :)

---

### Post by spikoley on 2009-05-16
> **SnabelAir said:**
> 
Then as root type
make install"
So far so good, after launching Terminal I cannot change directories! Ive logged in as ROOT but when using "dir" to see which folders I could browse into I only get "No such file or folder" when typing for example "cd /dekstop" even thou the "desktop" folder appears with both the "dir" and the "ls" commands. 

Anyone knows what the error is? Why can't I browse into folders?
Greatful for answer,
Andreas

With Ubuntu you do not log in as root.  Instead put [sudo]("https://wiki.ubuntu.com/RootSudo") in front of commands that need root access.  The command line is also case sensitive, so you have to use caps.  The desktop is listed as Desktop and not desktop.  The desktop is under your home folder and not in the root like this /home/user/Desktop.  When the folder you are trying to cd into is in that folder you do not need to type the full path.  Use the following command.

```
cd Desktop
```

---

### Post by SnabelAir on 2009-05-16
Ah, many thanks for the answers guy! Dekstop with a capital D solved it! That would have taken me quite some time to log in. :P 
And thanks for the sudo-info!

---

