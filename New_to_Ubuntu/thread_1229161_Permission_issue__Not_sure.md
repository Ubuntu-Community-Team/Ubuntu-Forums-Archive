---
title: "Permission issue?  Not sure"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by mrrross on 2009-08-01
I have 9.04 64 bit installed and it's working fine.   I have an application from work which is received as a .tar.gz file.  On my 8.04 box I made a folder for the program in /usr/local and unzip/untar and simply set the path in the /etc/.environment file.  it has several executables in the bin folder I use without an issue.

Fast forward to today.  I'm not sure what I'm doing wrong, but if I log in as root and create a folder in /usr/local, then unzip/untar the file I'm unable to launch any of the files.  I can navigate into the bin window (using the visual windows explorer type file thingy from places) and see the file and double click it all day long, it wont do anything.  I have right clicked on it and see the permissions tab is set with me as the owner, with read and write access.   The allow executing file box has a check mark in it.  

Does this make sense to anyone?  

Thanks in advance for your help.  -Ryan

---

### Post by mrrross on 2009-08-01
bump for any help pls!

---

### Post by adamitj on 2009-08-01
We need more information to assist you, like what's the application and what executable file are you trying to run.

Check out if the executable file is really set as an executable. If not, try:```
$ sudo chmod +x <path_and_executable_filename>
```

---

