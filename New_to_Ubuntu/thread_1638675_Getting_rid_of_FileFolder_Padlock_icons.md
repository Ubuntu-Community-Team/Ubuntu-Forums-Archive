---
title: "Getting rid of File/Folder Padlock icons  ????"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2010-12-05
OK I am making some progress in transferring files from my Jaunty Jack install to my Lucid install. After copying the Desktop folder I now have padlock icons on each file/folder. I assume this a permissions issue.

I altered the permissions on the parent Lucid Desktop folder and selected the change permissions on subordinate files option. The folder changed ownership from root to me, user Ed but the slave files/folders did not.   ????

Do I dare attempt this under terminal with a chown command?

What is the proper syntax?

Tks,   Ed

P.S. Besides the /home folder do I need to copy /etc or any other data from Jaunty to Lucid to have what I need?

---

### Post by Zzl1xndd on 2010-12-05
I would open a terminal and enter ```
gksudo nautilus
``` .

This should open a Nautilus Window with Root privileges, then use it to alter the file permissions.

---

### Post by ozark_hillbilly on 2010-12-05
I was under Nautilus when i made the file/folder permission changes....

the folder changed but not the files & folders under it....

????

Ed

P.S.

Under nautilus I did change an individual file permission on the Desktop and the padlock icon went away. It's just not changing all the files at once. It won't be practical to change these one at a time....    :^ (

---

### Post by Zzl1xndd on 2010-12-05
Using ```
gksudo nautilus
``` Via the Terminal will give you full access to all files on the system.

Basically whats happening is the files you moved don't belong to your account on the current install, so it wont let you change them.

---

### Post by beew on 2010-12-06
Just type in the terminal 

```
sudo chown -R usrname path_to_folder
```

This will transfer ownership of folder to "username". With the -R option it will change ownership of all the files in the folder as well

---

### Post by asmoore82 on 2010-12-06
For folders only, the last button under the "Permissions" tab
should be "Apply Permissions to Enclosed Files"

To get at this for the whole Desktop, you need to open "Places -> Home"
and then right-click the Desktop folder and "Properties -> Permissions"

---

