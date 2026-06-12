---
title: "Can't empty Trash"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by Elep.Repu on 2009-06-25
I can't empty the trash, I tried 
```
sudo rm -fr /home/USERNAME/.local/share/Trash/
```[http://www.randyjensenonline.com/blog/cant-empty-trash-in-ubuntu-804](http://www.randyjensenonline.com/blog/cant-empty-trash-in-ubuntu-804)
But it doesn't seem to work. The files are still in the trash. 

I'm using 9.04 Ubuntu.

When I browsed to (/home/USERNAME/.local/share/Trash)
 (before and after I did the command) the trash's files are not located there.

---

### Post by Elep.Repu on 2009-06-25
Sorry, I fixed it;

```
sudo gksu nautilus ~/.local/share/Trash/

```

Then I saw the files.

I guess doing ```
sudo gksu nautilus ~/
```
and browsing there took me out of root or something. Thank you.

---

### Post by lovinglinux on 2009-06-25
> **Elep.Repu said:**
> Sorry, I fixed it;

```
sudo gksu nautilus ~/.local/share/Trash/

```

Then I saw the files.

I guess doing ```
sudo gksu nautilus ~/
```
and browsing there took me out of root or something. Thank you.

I never saw anyone using *sudo gksu*. It seems odd to me.

The correct way I know is:

```
gksudo nautilus
```

When opening graphical interfaces with administrative rights you should always use *gksudo*. Use *sudo* only for command-line.

---

### Post by Elep.Repu on 2009-06-25
> **lovinglinux said:**
> I never saw anyone using *sudo gksu*. It seems odd to me.

The correct way I know is:

```
gksudo nautilus
```When opening graphical interfaces with administrative rights you should always use *gksudo*. Use *sudo* only for command-line.


I'm so sorry but I thought it worked and it didn't!
I went into the folder as root and right clicked, but there was no option to delete (at least i never saw one.) There was just Move to Trash

And now I can't even find the files. They still show in the trash can, and the delete command (with -rf) won't do anything. 
When I reload the Trash folder it still shows nothing.

**
I tried running,
**sudo rm -rf /root/.local/share/Trash/***

(Cause they're in that folder now) but it didn't work.

I tried pressing the **Delete** key on the keyboard, but the files just disappeared, then reappeared.

***
I finally just did:

> aji@aij-dtp:/$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
aji@aij-dtp:/$ su
Password: 
Added user root.

root@aij-dtp:/# ls
bin    dev   initrd.img  lib64       mnt   root     srv  usr
boot   etc   lib         lost+found  opt   sbin     sys  var
cdrom  home  lib32       media       proc  selinux  tmp  vmlinuz
root@aij-dtp:/# cd root/
root@aij-dtp:~# ls
Desktop
root@aij-dtp:~# cd .local
[EMAIL="root@aij-dtp:%7E/.local"]root@aij-dtp:~/.local[/EMAIL]# ls
share
[EMAIL="root@aij-dtp:%7E/.local"]root@aij-dtp:~/.local[/EMAIL]# cd share/
[EMAIL="root@aij-dtp:%7E/.local"]root@aij-dtp:~/.local[/EMAIL]/share# ls
Trash
[EMAIL="root@aij-dtp:%7E/.local"]root@aij-dtp:~/.local[/EMAIL]/share# cd Trash/
[EMAIL="root@aij-dtp:%7E/.local"]root@aij-dtp:~/.local[/EMAIL]/share/Trash# ls
files  info
[EMAIL="root@aij-dtp:%7E/.local"]root@aij-dtp:~/.local[/EMAIL]/share/Trash# cd files/
[EMAIL="root@aij-dtp:%7E/.local"]root@aij-dtp:~/.local[/EMAIL]/share/Trash/files# ls
dvdshrink32setup.2.exe  Linux.2
dvdshrink32setup.2.zip  m89ajc06b2uyyjcns4ug.2.jpg
[EMAIL="root@aij-dtp:%7E/.local"]root@aij-dtp:~/.local[/EMAIL]/share/Trash/files# rm -rf *
[EMAIL="root@aij-dtp:%7E/.local"]root@aij-dtp:~/.local[/EMAIL]/share/Trash/files# ls


By the way _Thank you. :)_

---

### Post by lovinglinux on 2009-06-25
You shouldn't use *sudo passwd root*. Take a look on [this thread](http://ubuntuforums.org/showthread.php?t=473916), particularly [this post](http://ubuntuforums.org/showpost.php?p=2844158&postcount=2).

Also read:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Please notice the bright yellow warning

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=118905&stc=1&d=1245919764[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=118906&stc=1&d=1245919843[/IMG]

> If for some reason you have enabled your root account and wish to disable it again, use the following command in terminal... 

```
sudo usermod -p '!' root
```



Ubuntu comes without root password for security reasons.

I strongly recommend that you do not follow tutorials and run commands without knowing what they do and what are the security risks. If you are in doubt, just ask in the forums first. Please read the following announcement:

[ATTENTION ALL USERS: Malicious Commands](http://ubuntuforums.org/announcement.php?f=326)



*UKeywords: 649167 2009 june root sudo*

---

### Post by Elep.Repu on 2009-06-25
> **lovinglinux said:**
> You shouldn't use *sudo passwd root*. Take a look on [this thread]("http://ubuntuforums.org/showthread.php?t=473916"), particularly [this post]("http://ubuntuforums.org/showpost.php?p=2844158&postcount=2").

Also read:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Please notice the bright yellow warning


Oh sorry, I just disabled it, thank you!

---

