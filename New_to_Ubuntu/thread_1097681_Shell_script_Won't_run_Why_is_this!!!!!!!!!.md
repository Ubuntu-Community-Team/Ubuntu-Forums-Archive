---
title: "Shell script? Won't run? Why is this?!!!!!!!!!"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by 133794m3r on 2009-03-16
ok in ubuntu i just clicked "allow executing" and it ran in xubuntu it's not doing anything. I can't get it to run. So this is yet another thing that's slowing me down in xubuntu.

---

### Post by taurus on 2009-03-16
Did you change the permissions to executable first?  Have you tried to run it from a terminal to see if it works?

---

### Post by 133794m3r on 2009-03-16
no option from the properties window. :/ i click on the permissions tab and no option to allow it to execute and i've tried going sudo sh /path to it and it'll just open the file like a text file

---

### Post by taurus on 2009-03-16
What is the name of that file and where does it locate?

```
cd *directory_where_that_file_is*
ls -la
```

---

### Post by 133794m3r on 2009-03-16
it's the wine requirements shell script and it's on my desktop. Is this normal for all xubuntu there's no way to allow it to execute from the desktop? w/o doing some command line options?

output is this :/
```
macarthur@insanity:~/Desktop$ ls -la
total 14868
drwx------  2 macarthur macarthur     4096 2009-03-16 06:01 .
drwxr-xr-x 19 macarthur macarthur     4096 2009-03-16 06:07 ..
-rw-r--r--  1 macarthur macarthur     4582 2009-03-16 06:01 install-wine-deps.sh
-rw-r--r--  1 macarthur macarthur 15187387 2009-03-16 05:58 wine-1.1.17.tar.bz2
```

---

### Post by damis648 on 2009-03-16
While still in that directory, try running:
```
./install-wine-deps.sh

```

---

### Post by taurus on 2009-03-16
```
chmod +x install-wine-deps.sh
./install-wine-deps.sh
-or-
sudo ./install-wine-deps.sh
```

---

### Post by 133794m3r on 2009-03-16
```
macarthur@insanity:~/Desktop$ ./install-wine-deps.sh
bash: ./install-wine-deps.sh: Permission denied
macarthur@insanity:~/Desktop$ sudo ./install-wine-deps.sh
sudo: ./install-wine-deps.sh: command not found
```
i thought xubuntu wouldn't be that much of a difference from ubuntu except some system resources never imagined it'd be this kinda hell :/

edit: as asked why is there no option to enable executing shells and such from the desktop? why must xubuntu be like this?

---

### Post by taurus on 2009-03-16
> **133794m3r said:**
> ```
macarthur@insanity:~/Desktop$ ./install-wine-deps.sh
bash: ./install-wine-deps.sh: Permission denied
macarthur@insanity:~/Desktop$ sudo ./install-wine-deps.sh
sudo: ./install-wine-deps.sh: command not found
```
i thought xubuntu wouldn't be that much of a difference from ubuntu except some system resources never imagined it'd be this kinda hell :/

edit: as asked why is there no option to enable executing shells and such from the desktop? why must xubuntu be like this?

I think you are a little confuse about Xubuntu & Ubuntu.  You are just using a difference window manager/desktop environment (XFce4 instead of Gnome).  Everything else underneath is still the same.

---

### Post by 133794m3r on 2009-03-16
i know everything is the same underneath but why then as i asked is the edit permissions and such soooo much different i used ubuntu for awhile new my way around go to xubuntu b/c it's apparently tailored for weaker systems my backup laptop is one. Then i find out first off i can't enable or edit the permissions of my files from the permissions tab in teh properties window. And also the touchpad won't get disabled i've tried installing that package the suggested and to no avail it wouldn't work.

edit: the reason they're the same underneath is why i chose xubuntu besides the other reason.

---

### Post by damis648 on 2009-03-16
This is all you need to do:
```
chmod + x install-wine-deps.sh
./install-wine-deps.sh
```

---

### Post by 133794m3r on 2009-03-16
yeah that mod worked but this stupid touchepad won't get disabled and the universe doesn't have that qsynatpics package.

ok i installed this file but now it's being weird with me :/ and i can't find it.

---

