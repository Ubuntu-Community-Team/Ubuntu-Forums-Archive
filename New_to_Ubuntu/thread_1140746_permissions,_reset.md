---
title: "permissions, reset"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by rivkinnator on 2009-04-27
i have my friends mac that im trying to get the files off of because it wont boot into mac because a noob thought he knew what he was doign when he partitioned the drive to put windows on then tried to delete it. i now have to remove the permissions off his files to be able to copy them off the drive so i can reinstall MAC OSX. i now the command chmod exists but i dont now how to use it. or are their other commands that can do this. i have tried chmod 777 -R /media/ as a friend told me earlier today on forms. i need help please.

---

### Post by kk0sse54 on 2009-04-27
Type "man chmod" and "man chown" into the terminal, two commands that should greatly help you if you're looking just to move specific files off the drive instead of imaging the entire drive. Chown will change ownership of a file while chmod will change it's permissions. For example if you wanted to change the ownership of ~/example/ directory you would just ```
sudo chown -R <user> ~/example
```
if we analyze the code a bit, "sudo" gives us temporary root permissions, the -R means recursive which means it changes the ownership of all files in the directory and <user> is just the the user who will be given the new ownersip. Of course there'sa bunch more options which it why you should familiarize yourself with the "man" command to acquire documentation from the terminal regarding any command.

---

### Post by rivkinnator on 2009-04-27
i tried chown and chmod with the drive under the /media directory and it says
chown?: changing ownership of '/media/disk/...': operation not permitted

---

### Post by rivkinnator on 2009-04-27
oh another error it says is that its a read only file system

---

