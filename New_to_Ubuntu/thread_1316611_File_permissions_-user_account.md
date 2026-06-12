---
title: "File permissions -user account"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by Habaneroman on 2009-11-06
I am trying to replace my hosts file and I am having problems, Extraction not performed     You don't have the right permissions to extract archives in the folder "file:///etc". I am new so be patient, I  think I need to change something to allow me to do this task.

---

### Post by mcduck on 2009-11-06
Aöll you ened to do is to tel the system that you want to use rot permissions.

Even admin users don't run with full administrator permissions all the time in Ubuntu, most of the time they are just like any other user, with write access only in their own home directories. When you need more permissions than that you need to specifically ask for them. In Ubuntu this is done by using the "sudo" (and "gksduo" commands".

First you should probably read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

...and after that, you can just press Alt-F2 and run "gksudo nautilus" to open the file manager with full root permissions. That should allow you to easily extract your files into /etc.

---

### Post by nothingspecial on 2009-11-06
What are you trying to move or extract from where to where?

You will probably have to do it as root but I`d like to be sure you`re not going to mess anything up first.

---

### Post by elliotn on 2009-11-06
alt-f2 then type gksudo nautilus

---

### Post by Habaneroman on 2009-11-06
Still Lost!! I am trying to replace my hosts file with one that will block parasites, in windows it was just a matter of dragging the new file over the other one, I am not experienced with the command line in the ubuntu terminal.

---

### Post by Habaneroman on 2009-11-06
Still Lost!! I am trying to replace my hosts file with one that will block parasites, in windows it was just a matter of dragging the new file over the other one, I am not experienced with the command line in the ubuntu terminal.

---

### Post by Habaneroman on 2009-11-06
Still Lost!! I am trying to replace my hosts file with one that will block parasites, in windows it was just a matter of dragging the new file over the other one, I am not experienced with the command line in the ubuntu terminal. jj

---

### Post by 3rdalbum on 2009-11-06
You're bumping your message quite a lot.

The /etc/hosts file is outside your home directory, so your normal user account cannot modify it. This is for security and stability reasons. You need to open up a file browser as root (administrator) by using the following command:

```
gksudo nautilus
```

Within this window, you can do anything on your computer - so be careful! Any files you open or programs you launch from within this window will be run as root too. Another good way of using root is to install the "nautilus-gksu" package; when you next log in after installing it, you'll be able to right-click any file or folder and choose "Open as Administrator".

Also I'm not sure what you mean by "block parasites". What parasites? If you want to stop incoming connections to your computer, what you need is a firewall, not a hosts file.

---

