---
title: "Permission problem with waste bin"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by dan1973 on 2009-04-21
Hello, I'm trying to get rid of a file in the recycle bin but it won't let me. Permission denied.

When I look at the permissions of the file in question, it won't let me change them.

how do i force a delete from the bin of the offending file?

Many thanks,:(

---

### Post by kyleflan on 2009-04-21
You probably need to change the owner or permissions. Can you run "ls -l" on the directory in question?

---

### Post by amingv on 2009-04-21
try

```
sudo rm /home/user/.local/share/Trash/files/<nameoffile>
```

---

### Post by kyleflan on 2009-04-21
Also, running the command below may solve your problem:

```
sudo rm filename
```

Which runs the rm as root.

---

### Post by bumanie on 2009-04-21
Type > gksudo nautilus in terminal, put in password and then go to Places --> Computer --> Filesystem and navigate to the waste bin and you should be able to delete the file/s. gksudo is super user in graphical mode, so be careful what you remove.

---

### Post by dan1973 on 2009-04-21
Still no luck,

gksudo nautilus gives the following:
```

dan@ubuntu:/home$ gksudo nautilus
seahorse nautilus module initializedInitializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:12306): WARNING **: Unable to add monitor: Operation not supported

** (nautilus:12306): WARNING **: Unable to add monitor: Operation not supported
```
 
It does then open root file browser, but where is the trash bin to be found in file browser?

---

### Post by amingv on 2009-04-21
> **dan1973 said:**
> Still no luck,

gksudo nautilus gives the following:
```

dan@ubuntu:/home$ gksudo nautilus
seahorse nautilus module initializedInitializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:12306): WARNING **: Unable to add monitor: Operation not supported

** (nautilus:12306): WARNING **: Unable to add monitor: Operation not supported
```
 
It does then open root file browser, but where is the trash bin to be found in file browser?

See my post. I gave you the whole path.

---

### Post by dan1973 on 2009-04-21
Ok, so i run following:

```
dan@ubuntu:~$ sudo rm /home/user/.local/share/Trash/files/ndiswrapper-1.54
```

result:

```
rm: cannot remove `/home/user/.local/share/Trash/files/ndiswrapper-1.54': No such file or directory


```

Problem is that it still shows up in the trash bin,

Strange...

What am i missing?

---

### Post by amingv on 2009-04-21
> **dan1973 said:**
> Ok, so i run following:

```
dan@ubuntu:~$ sudo rm /home/user/.local/share/Trash/files/ndiswrapper-1.54
```

result:

```
rm: cannot remove `/home/user/.local/share/Trash/files/ndiswrapper-1.54': No such file or directory


```

Problem is that it still shows up in the trash bin,

Strange...

What am i missing?

Replace "user" in the command by your actual username.

---

### Post by sisco311 on 2009-04-21
```
sudo chown -R $USER\: ~/.local/share/Trash/files
```
then try to empty the Trash.

---

### Post by Michael.Godawski on 2009-04-21
You can use this command to delete the trash contents of your home folder:
 ```
rm -rf ~/.local/share/Trash/*
```
 If you get permission problems try to slip a sudo in front of the commands, but **be sure that the path is correct**.
 Sometimes it is necessary to change the ownership of the thrash files:
 ```
sudo chown -R yourusername /home/yourusername/.local/share/Trash
```

---

### Post by kiridude on 2009-04-21
Use nautilus as told by Bumanie, then follow the path as indicated by Amingv - but type ctrl h once inside nautilus otherwise you will not be able to see .local in /home/yourusername. Your trash is there and you can delete whatever you want this way.

---

### Post by sisco311 on 2009-04-21
You can open nautilus directly in the trash directory:
```
gksu nautilus ~/.local/share/Trash/files
```

---

### Post by dan1973 on 2009-04-21
OK, i think i'm getting somewhere......


```
rm: cannot remove `ndiswrapper-1.54/': Is a directory
root@ubuntu:/home/dan/.local/share/Trash/files# rmdir ndiswrapper-1.54/
rmdir: failed to remove `ndiswrapper-1.54/': Directory not empty
root@ubuntu:/home/dan/.local/share/Trash/files# 
```


Just need to be able to delete a full directory...

---

### Post by Michael.Godawski on 2009-04-21
See my first post, the -r suffix in the code means recursive and it removes directories and their contents recursively.

Be cautious with this. Do not delete your whole system ;).
Make sure the path after the rm command is correct. 

I remember days when I destroyed my whole system playing around with the rm command... long time ago.

You can always check what a command does and the additional option it has with:

```
man commandname
```
```
man rm
```

---

### Post by sisco311 on 2009-04-21
> **dan1973 said:**
> OK, i think i'm getting somewhere......


```
rm: cannot remove `ndiswrapper-1.54/': Is a directory
root@ubuntu:/home/dan/.local/share/Trash/files# rmdir ndiswrapper-1.54/
rmdir: failed to remove `ndiswrapper-1.54/': Directory not empty
root@ubuntu:/home/dan/.local/share/Trash/files# 
```


Just need to be able to delete a full directory...

Did you try the other suggestions?

In my opinion the safest is to change the owner(chown) of the Trash
and delete the content as a regular user. 

When you delete directories with the rm command, you have to use the -r flag:
```
rm -r /path/to/dir
```

---

### Post by dan1973 on 2009-04-21
Thanks Michael.godawski, popped a sudo in front of your command and finally if went away!

---

### Post by Michael.Godawski on 2009-04-21
Good to hear. I hope only the file and directory which should be deleted are now gone ;).
The rm command and sudo are dangerous friends.

---

### Post by dan1973 on 2009-04-21
Thanks for the ctrl h option - nice to see where things are!

Even so didn't manage to delete from there - permission problem, i don't think i was as 'super user' 

Problem taken care of now 

thanks again

---

### Post by dan1973 on 2009-04-21
But what great teamwork!!!!

---

### Post by LiamWilson on 2009-04-21
I always have to use sudo rm -rf to delete files from the trash i 'dont have permission' to delete. Should we do something about it?

---

### Post by dan1973 on 2009-04-21
> **sisco311 said:**
> Did you try the other suggestions?

In my opinion the safest is to change the owner(chown) of the Trash
and delete the content as a regular user. 

When you delete directories with the rm command, you have to use the -r flag:
```
rm -r /path/to/dir
```

Should have done it this way ! Definitely next time if problem raises its ugly head again.

Many thanks for the sage advice.

---

### Post by kiridude on 2009-04-21
> **dan1973 said:**
> Thanks for the ctrl h option - nice to see where things are!

Even so didn't manage to delete from there - permission problem, i don't think i was as 'super user' 

you must put gksudo in front of "nautilus" command to enter as super-user.

Anyway, glad to see you got it taken care of.

---

