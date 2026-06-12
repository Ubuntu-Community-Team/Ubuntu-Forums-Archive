---
title: "Ubuntu 8.10 - Cannot transfer files from laptop to external hard drive"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by wangsuda on 2009-02-09
I just did a clean install of Ubuntu 8.10 on my laptop. This is not a dual boot system. Now I wish to back up certain files for my external hard drive. Since Ubuntu reformatted my computer to ext3, I reformatted my external drive to ext3. However, when I try to transfer files, I get an error message that says I am not allowed to transfer. When I reformatted my external drive to FAT32, I could transfer with no problems. So what should I do? Is there a way to have my external drive in ext3 format and transfer files?

---

### Post by konqueror7 on 2009-02-09
does your external harddrive support ext3 filesystem?

---

### Post by billgoldberg on 2009-02-09
> **wangsuda said:**
> I just did a clean install of Ubuntu 8.10 on my laptop. This is not a dual boot system. Now I wish to back up certain files for my external hard drive. Since Ubuntu reformatted my computer to ext3, I reformatted my external drive to ext3. However, when I try to transfer files, I get an error message that says I am not allowed to transfer. When I reformatted my external drive to FAT32, I could transfer with no problems. So what should I do? Is there a way to have my external drive in ext3 format and transfer files?

The easy thing to do would be to open Nautilus (or whatever file manager you are using) as root and then copy the files to the external hdd.

That will fix any permission problems, but it's a bad workaround. 

*(open nautilus as root by doing "gksudo nautilus")*

---

### Post by cjv8888 on 2009-02-09
or try change owner to yourself assuming now the external drive is owned by root.

```
sudo chown -R username: /path/to/externaldrive 
```

---

### Post by wangsuda on 2009-02-09
> **billgoldberg said:**
> The easy thing to do would be to open Nautilus (or whatever file manager you are using) as root and then copy the files to the external hdd.

That will fix any permission problems, but it's a bad workaround. 

*(open nautilus as root by doing "gksudo nautilus")*

Tried that but got ```
XXX@XXX-laptop:~$ gksudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initializedNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:14824): WARNING **: Unable to add monitor: Operation not supported

```

---

### Post by vanadium on 2009-02-09
The solution indeed is to change the ownership of the mount point of the drive. Another solution, suited if more users use the drive, is to create directories (as root) on the drive, then change the ownership of the directories to the respective users.

The graphical way to do that is to load nautilus with root permissions. Are you telling that after typing "gksudo nautilus" you do not get nautilus to open?

---

### Post by wangsuda on 2009-02-09
> **vanadium said:**
> The solution indeed is to change the ownership of the mount point of the drive. Another solution, suited if more users use the drive, is to create directories (as root) on the drive, then change the ownership of the directories to the respective users.

The graphical way to do that is to load nautilus with root permissions. Are you telling that after typing "gksudo nautilus" you do not get nautilus to open?

I am sorry, but you are talking way over my head. I don't understand why, when I format a drive in NTFS or FAT32, I can write to it, but I cannot when I format the drive in ext2 or ext3. Sorry, but I am a very new user in this.

---

### Post by rolnics on 2009-02-09
I don't have anything to offer in technical help, but I was just reading the last reply and thought I'd try and help you out wangsuda, it can get complicated when things don't work. Here goes, this is what I think vanadium is meaning.

> **vanadium said:**
> The solution indeed is to change the ownership of the mount point of the drive.
What vanadium is saying is the owner of the ext drive needs to be changed to a user account, the account you normally use, rather than the root user, allowing you to move files.
> **vanadium said:**
> 
 Another solution, suited if more users use the drive, is to create directories (as root) on the drive, then change the ownership of the directories to the respective users.
This might be a better / easier solution, and something I'll keep in mind when I get an ext harddrive. Again what vanadium is saying you create a folder for a "joe smith" named "joe" and change the permissions so that joe and only joe can use this folder, and the whole drive is still owned by the root user, so can ultimately do anything to the drive.


> **vanadium said:**
> 
The graphical way to do that is to load nautilus with root permissions. Are you telling that after typing "gksudo nautilus" you do not get nautilus to open?

I think what vanadium is meaning after typing "gksudo nautilus" does nautilus the file manager open, or are you just getting error text in the terminal and nothing more?

---

### Post by vanadium on 2009-02-09
Linux is a multi user operating system that is designed with security in mind. By default, no-one gets to write to a drive unless he is granted permissions by the system administrator (super user or root user).

Nor non-linux file systems that do not support the permission system, the system is as such: a fat formatted drive is mounted automatically with permissions for the current user. Another user logged on to the system will not be able to use it unless it is removed and plugged in while the session of the other user is in the foreground.

ntfs systems are auto-mounted by default with root ownership and all permissions open. You can regulate permissions through mount options either in the graphical user interface or when you mount using the mount command or using /etc/fstab.

This for the "why".

For the "how", you need to use the command line or load nautilus with root permissions. You did not tell what the problem for you is, running "gksudo nautilus". Normally, a nautilus window should appear with which you can do anything, even delete all files on your system.

---

### Post by HyRax on 2009-02-09
> **wangsuda said:**
> I am sorry, but you are talking way over my head. I don't understand why, when I format a drive in NTFS or FAT32, I can write to it, but I cannot when I format the drive in ext2 or ext3. Sorry, but I am a very new user in this.

NTFS and FAT32 do not enforce permissions like Linux filesystems do. By default, your Ext2/3-formatted drive is only allowed to be written to by root, so you need to fix this.

Let's assume your drive was mounted as /media/mybigdrive - if your login name were jbloggs, to allow access, simply jump into a terminal and type in:

```

$ sudo chown -R jbloggs:jbloggs /media/mybigdrive

```
...and you will be able to access the drive properly after that because the drive now "belongs" to jbloggs instead of root.

You can do this via Nautilus, but the terminal is just soooo much faster.

---

### Post by wangsuda on 2009-02-09
> **HyRax said:**
> NTFS and FAT32 do not enforce permissions like Linux filesystems do. By default, your Ext2/3-formatted drive is only allowed to be written to by root, so you need to fix this.

Let's assume your drive was mounted as /media/mybigdrive - if your login name were jbloggs, to allow access, simply jump into a terminal and type in:

```

$ sudo chown -R jbloggs:jbloggs /media/mybigdrive

```
...and you will be able to access the drive properly after that because the drive now "belongs" to jbloggs instead of root.

You can do this via Nautilus, but the terminal is just soooo much faster.
Thanks for your suggestion. I tried it, and here's my result:
```
douglas@douglas-laptop:~$ $ sudo chown -R douglas:douglas /media/1.0 GB Media
bash: $: command not found
douglas@douglas-laptop:~$ $ sudo chown -R douglas:douglas /media/disk
bash: $: command not found

```I'm lost.

---

### Post by vanadium on 2009-02-09
You should not include the "$" before.

In order for us to be able to give the specific command, execute following command and post the output here:

```

sudo blkid
ls -l /media

```

After the first command, you will need to provide your login password. while providing your password, you won't see anything on the screen: this is normal.

After running the commands, highlight the output in the console by dragging with the mouse, select "edit - copy", and paste that output here in your reply.

---

### Post by HyRax on 2009-02-09
Yes, don't use the $ sign - sorry about that. I always put that there to illustrate that it's a terminal command.

Additionally, your "1.0 GB Media" would need to be written as "/media/1.0\ GB\ Media" because of the spaces - they need to be written "literally" otherwise the system will take "1.0", "GB" and "Media" to be three separate parameters. The backslash tells the system that "the next character is a literal".

---

### Post by egalvan on 2009-02-09
> **HyRax said:**
> ....
Additionally, your "1.0 GB Media" would need to be written as "/media/1.0\ GB\ Media" **because of the spaces **- they need to be written "literally" otherwise the system will take "1.0", "GB" and "Media" to be three separate parameters. The backslash tells the system that "the next character is a literal".

Even better, since he is *not* using Microsoft, 
start labeling the *nix way....

no spaces...use _ for spaces,
example,
this_is_linix_
this is microsoft

lower case only, unless you have a specific need.
*nix sees upper and lower as different.


These ideas have saved me un-told grief... :)

ErnesrG

---

### Post by wangsuda on 2009-02-09
> **HyRax said:**
> Yes, don't use the $ sign - sorry about that. I always put that there to illustrate that it's a terminal command.

Additionally, your "1.0 GB Media" would need to be written as "/media/1.0\ GB\ Media" because of the spaces - they need to be written "literally" otherwise the system will take "1.0", "GB" and "Media" to be three separate parameters. The backslash tells the system that "the next character is a literal".

[QUOTE=egalvan]Even better, since he is not using Microsoft,
start labeling the *nix way....

no spaces...use _ for spaces,
example,
this_is_linix_
this is microsoft

lower case only, unless you have a specific need.
*nix sees upper and lower as different.


These ideas have saved me un-told grief...

ErnesrG [/quote]You two are geniuses! It now works perfect! Thank you!

---

