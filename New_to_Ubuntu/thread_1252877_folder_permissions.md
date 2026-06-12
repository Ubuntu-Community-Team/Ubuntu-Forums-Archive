---
title: "folder permissions"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by fitgene on 2009-08-29
how do you assign permission to folders
i want to deny access read write and execute permission for group and others for a particular folder. how do i do it?
also mention command line

---

### Post by s.fox on 2009-08-29
Hi,

Hope [this]("http://ubuntuforums.org/showthread.php?t=445213") helps.

-Silver Fox

---

### Post by Penguin Guy on 2009-08-29
> **fitgene said:**
> i want to deny access read write and execute permission for group and others for a particular folder. how do i do it?
You will want to use the command chmod: [COLOR="Green"]chmod 700 <folder>[/COLOR].

---

### Post by bodhi.zazen on 2009-08-29
> **Penguin Guy said:**
> You will want to use the command chmod: [COLOR=Green]chmod 700 <folder>[/COLOR].

That will not work on FAT or NTFS partitions.

See also : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by ayenack on 2009-08-29
Also if you own the folder you can right click on it and select **Properties>Permissions** and change your setting from the drop down menus. This is assuming that the folders were created by you in Ubuntu.

Be careful which folders you change permissions on as it's possible to mess up your system if you change permissions on system folders and alike. If it's a folder you've created then you should be fine.

---

### Post by fitgene on 2009-08-29
thanx for the link silver. enjoying ubuntu

---

### Post by fitgene on 2009-08-29
i have previously tried the command chmod go-rwx filename and chmod go= filename. bothe never worked. is it bcoz i do in the $ prompt. shud i switch to root and try

---

### Post by ayenack on 2009-08-29
You may need to use sudo in front of it depending on what folders you are changing. Be careful what folders you change the permissions on.

---

### Post by PukingPenguin on 2009-08-29
If you can post the absolute path to the file, we will have a better idea if it is a file that you can safely change permissions on, as well as whether or not sudo is required.

Assuming that the file is in /home and you don't need to use sudo to alter it, the advice previously given to use ```
chmod 700 <filename>
``` is correct.That will give the owner (presumably you) the right to read, write or execute and deny all access to all others.

---

### Post by fitgene on 2009-08-30
its a folder thats not in the root directory. i have made the folder. when tried to change the permission with graphic interphase it says the root as the owner. hence unable to change. looking for a command line process. could u help?

---

### Post by bodhi.zazen on 2009-08-30
It would help if you gave us more information.

1. What file system ? ext3 ? ntfs ? what ?

2. What directory you are changing ? /home/your/foo ? /usr/local/bin ?

3. what are the current permissions of the directory , show us the output of :

```
ls -l /full/path/to/directory_in_question
```

4. If you get an error message, please post the exact error message.

If you are on a linux system, 

sudo chown you:you /direcoty
sudo chmod 777 /dirctory

will work

See man chown and man chmod

If you are on a FAT or ntfs file system you set ownership and permissions for the entire partition when you mount it, sub directories can not be changed.

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by ayenack on 2009-08-31
Even though the folder is not in root it can still be owned by root if you used sudo to create it. For instance.

**mkdir /home/ayenack/images** (Would be owned by ayenack and not root.)

**sudo mkdir /home/ayenack/images** (Would be owned by root because I have used sudo to create it.)

Not sure this is the case for you.

What I would do if I were you is just create a new folder in your home directory. You can do this by navigating to your home directory and right clicking in it then select Create Folder and name it whatever you want. Once the folder is created you can right click on it and change the permission by selecting properties then permissions.

Here's a pretty in-depth guide to changing permissions. With examples on what each command will do it's well worth a look just to get a general feel of the concept folder/file permissions.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

