---
title: "How to change User name"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by chethankrish on 2009-01-21
hi.. can we change our user name in ubuntu.. if so please help me on how to go about doing the same... the screen shot below shows my Ubuntu version and other information..thank you

---

### Post by theozzlives on 2009-01-21
> **chethankrish said:**
> hi.. can we change our user name in ubuntu.. if so please help me on how to go about doing the same... the screen shot below shows my Ubuntu version and other information..thank you

If you have admin rights, go to system>administration>users/groups. Unlock. highlight your name and click on properties.

---

### Post by chethankrish on 2009-01-21
but i cant change user name there.. i can change my real name and other things... but the question is how do i change my user name...?

---

### Post by cariboo on 2009-01-21
The easiest way to change your user name is to create a new user with the name you want, then copy all your files to the new user, then delete your old user. You will have have to copy the files from your old user to the new user as root, press Alt-F2 and type:

```
gksu nautilus
```

This will start nautilus as root. Once you have copied all the files you will have to change onwership and permissions. To do this open a Applications-->Accessories-->Termianl and type the following to change ownership:

```
sudo chown -R <newuser:newuser> /home/<newuser>
```

and to make sure you have permissions to read/write to your files and directories in the same terminal type:

```
sudo chmod -R 755 /home/<newuser>
```

You will get an error saying that you can't  change permissions to .gvfs, just ignore the error, as that is normal.

There is one other file that you will need to change the permissions on. In the same terminal type:

```
sudo chmod 600 /home/<newuser>/.dmrc
```

<newuser> = your new user name. 

Jim

---

### Post by chethankrish on 2009-01-21
thanx a lot for your help.....thank you

---

### Post by Elfy on 2009-01-21
Add the new user to the admin group before you reboot with the new name - Sys Admin - Users and Groups

(didn't see ozzlives post either)

---

### Post by Leon Fai on 2009-01-21
> **chethankrish said:**
> hi.. can we change our user name in ubuntu.. if so please help me on how to go about doing the same... the screen shot below shows my Ubuntu version and other information..thank you


so easy lah!hahahaha u can find in the UBUNTU HELP...:D

---

### Post by theozzlives on 2009-01-21
Sorry for the mis-information, just noticed the username is greyed out.

---

### Post by Elfy on 2009-01-21
> **Leon Fai said:**
> so easy lah!hahahaha u can find in the UBUNTU HELP...:D

Excellent first post on the forum

---

### Post by uid0 on 2009-01-21
Pretty easy actually.  Ubuntu (as well as most all *nix OSes) do everything by UID not username.  As long as you don't change the UID you can change the username to just about anything you like.  You will have to manually edit the following files:

/etc/passwd
/etc/shadow
/etc/group

Use the text editor of your choice and do a simple find/replace.

WARNING:  You need to be root to do this, and make sure you type carefully!  You stand the chance of locking yourself out if you do it badly.

---

