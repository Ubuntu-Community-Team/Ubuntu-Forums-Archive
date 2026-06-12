---
title: "change permission file systen"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by elvenour on 2010-12-18
i want to install nvidia driver
but it came must be in root folder
but my file system folder said that im not the owner
how this can be?
im the only one using this ubuntu
please help me

---

### Post by Verbeck on 2010-12-18
you shouldn't mess up with permissions of that
could you post the exact instructions you are following? its uncommon for a file to be placed in the root folder

(normally the drivers are activated through  system>administration>hardware drivers/additional drivers.)

---

### Post by 3rdalbum on 2010-12-18
1. To install the Nvidia driver, go to System > Administration > Additional Drivers and the driver will be offered to you.

2. The reason why your user account doesn't have permission to modify the file system is because in Linux we have "seperation of root and user". Ordinary users can't mess with the internals of the system or disrupt other users on the same computer. The only user that can is called "root".

How do you become root? In Ubuntu, if you are running a command, run it with the word "sudo" typed before, for instance:

```
sudo apt-get install chromium
```

If you are running a graphical program (such as the Nautilus file browser) as root, you can prefix it with 'gksudo' instead:

```
gksudo nautilus
```

Running the file browser as root, like I've shown above, will allow you to modify the file system inside that new window.

---

