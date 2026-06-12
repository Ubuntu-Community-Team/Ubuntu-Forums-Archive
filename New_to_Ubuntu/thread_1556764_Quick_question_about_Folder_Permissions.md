---
title: "Quick question about Folder Permissions"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by Zeptinune on 2010-08-19
Just need to know how to take control of folders on my computer so I don't have to elevate myself all the time just to write to them. I'm talking about home folders such as, Music, My Documents etc. That appear in the left-hand bar. I have permissions to open and read and execute but not to write.

Right click went permissions cant apply permissions for some reason. Thanks for any quick help.

---

### Post by skatinjj on 2010-08-19
> **Zeptinune said:**
> Just need to know how to take control of folders on my computer so I don't have to elevate myself all the time just to write to them. I'm talking about home folders such as, Music, My Documents etc. That appear in the left-hand bar. I have permissions to open and read and execute but not to write.

Right click went permissions cant apply permissions for some reason. Thanks for any quick help.

If i want control over folders, I simply make myself the owner:

```
sudo chown -R "user" "path to directory/file"
```

Replace "user" with the user you want to have access and "path to directory/file" with whatever directory/file you want to change ownership of.

---

### Post by mrbiggbrain on 2010-08-19
You need to own or be an admin to change any permissions. 

sudo chown -r username file_folder_1 file_folder_2

It will prompt for a password for a user with sudo credentials and then change you to be the owner.

to change the permissions of the file you would use

sudo chmod o+rwx file_Name

to give others wo are not the owner access rights.

---

### Post by Zeptinune on 2010-08-19
Thanks a ton!

---

### Post by Zeptinune on 2010-08-19
EDIT: Sorry guys, nothing is happening. Not being asked for a password. Terminal is just going to another line.

When doing[FONT=monospace]:[/FONT]
```
sudo chown -R "user" "path to directory/file" 
```Nothing happens.

When doing:
```
sudo chown -r "username" "file_folder_1" "file_folder_2"
```I get 'chown invalid option -r try chown help for more information'

I'm of course replacing the quoted stuff with my relevant paths :)

---

### Post by skatinjj on 2010-08-19
> **Zeptinune said:**
> EDIT: Sorry guys, nothing is happening. Not being asked for a password. Terminal is just going to another line.

When doing[FONT=monospace]:[/FONT]
```
sudo chown -R "user" "path to directory/file" 
```Nothing happens.

When doing:
```
sudo chown -r "username" "file_folder_1" "file_folder_2"
```I get 'chown invalid option -r try chown help for more information'

I'm of course replacing the quoted stuff with my relevant paths :)

never mind read too fast sorry let me ponder this another second

---

### Post by skatinjj on 2010-08-19
> **Zeptinune said:**
> EDIT: Sorry guys, nothing is happening. Not being asked for a password. Terminal is just going to another line.

When doing[FONT=monospace]:[/FONT]
```
sudo chown -R "user" "path to directory/file" 
```Nothing happens.

When doing:
```
sudo chown -r "username" "file_folder_1" "file_folder_2"
```I get 'chown invalid option -r try chown help for more information'

I'm of course replacing the quoted stuff with my relevant paths :)

If the command worked, it will not return anything, just drop to a blank prompt line.

To check if it worked run:

```
ls -l
```

That will spit out file information like ownership and permissions.

---

### Post by Zeptinune on 2010-08-19
It did indeed work thanks :) I just needed a restart for some reason.

/Solved

---

