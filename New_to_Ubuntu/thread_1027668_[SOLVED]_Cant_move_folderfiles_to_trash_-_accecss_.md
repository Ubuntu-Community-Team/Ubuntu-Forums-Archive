---
title: "[SOLVED] Cant move folder/files to trash - accecss denied."
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Firestem4 on 2009-01-01
Hi. I am trying to delete the folder /home/icarus/trunk. I was dowloading a svn in bash, and I downloaded the wrong thing> the Shell wont let me download the other subversion, because it says the trunk is already being used for another URL. When I try to move it to trash, i get:

Error-Plasma Workspace
access denied to /home/.local/share/Trash/files/trunk.

Permissions say Root but I shouldn't have to use it. I could delete stuff from my home files before except this.

---

### Post by shafi on 2009-01-01
> **Firestem4 said:**
> Hi. I am trying to delete the folder /home/icarus/trunk. I was dowloading a svn in bash, and I downloaded the wrong thing> the Shell wont let me download the other subversion, because it says the trunk is already being used for another URL. When I try to move it to trash, i get:

Error-Plasma Workspace
access denied to /home/.local/share/Trash/files/trunk.

Permissions say Root but I shouldn't have to use it. I could delete stuff from my home files before except this.

You should check, may be you have open this folder some where in use, if not try the following commands:
[HTML]
sudo chmod 777 /home/icarus/trunk
sudo rm -r /home/icarus/trunk
[/HTML]

---

### Post by snova on 2009-01-01
Perhaps some permissions got messed up. Try this, to make sure you own these files:

```
sudo chown icarus:icarus ~/.local/share/Trash -R
sudo chown icarus:icarus~/trunk -R
```

---

### Post by Firestem4 on 2009-01-01
Thanks shafi, Your fix worked perfectly.

Snova, Shell reports
```
icarus@icarus-Linux:~$ sudo chown icarus:icarus~/trunk -R
chown: missing operand after `icarus:icarus~/trunk'

```
Whats that mean?

And Shafi, would you mind explaining what I just did? is -R remove?

Edit: I just realized why it said that. I deleted the file already. Lol! thanks though.

---

### Post by Firestem4 on 2009-01-01
Oh and thanks for such a quick response =) Its much appreciated.

---

### Post by Copernicus1234 on 2009-01-01
Remove please.

---

### Post by Copernicus1234 on 2009-01-01
chown changes the owner of the folder and -R stands for Recursive (the changes are done to all the subfiles and subfolders).

So the command changed the owner of these files to be you so you have access to them.

Do a "man chown" for more info.

---

### Post by Firestem4 on 2009-01-01
Oh ok. Thanks. I'm going to copy that down for future reference.

---

### Post by gn2 on 2009-01-01
Or: press Alt + F2 and type gksudo nautilus

This gives sudo access to the GUI file browser.
Browse to the directory you want to modify and right-click on it, select Properties and  in the Permissions tab you can change the user.
You can apply the change to all enclosed files.

Remember to close nautilus when you're finished.

---

