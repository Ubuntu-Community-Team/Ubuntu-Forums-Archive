---
title: "apply permission on any file to save from accidental delete"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by konsolelover on 2011-05-17
hey everyone, i'm noob in linux world ...i wanna know that how can i apply permission on my specific file so that it can be only deleted by root user or as a root....TIA!

---

### Post by tapi0n on 2011-05-17
I'd assume using chmod to change rights to the file?

*chmod 700*? your user should be set to root then on the file (chown)

Hope this is correct and hope this is what you're looking for :)

---

### Post by ironic.demise on 2011-05-17
To change the ownership of a file use
```
sudo chown root /path/to/file
```
To set permissions use
```
sudo chmod 700 /path/to/file
```

To find out more about chmod or chown use ```
man chmod
``````
man chown
```

---

### Post by bolucpap on 2011-05-17
If i remember correctly, 700 would stop read access too. 744 perhaps? By the way, 744 would also prevent any write access to the file by non-root users, not just deletion (So would 700).

---

### Post by ironic.demise on 2011-05-17
> **bolucpap said:**
> If i remember correctly, 700 would stop read access too. 744 perhaps? By the way, 744 would also prevent any write access to the file by non-root users, not just deletion (So would 700).

The first number is root, The second is the group the file belongs to and the third number is other users.

1 = write
2 = read
4 = execute
... or something along those lines, I forget the exact number at this time.

He could use rwxrwxrwx...?
as in ```
sudo chmod rwxr--r-- /path/to/file
``` atleast then HE knows exactly what he's doing.

edit:4=read 2=write 1=execute
4+2+1=7
7 = rwx

4 = r--

```
sudo chmod 744 /path/to/file
```
OR
```
sudo chmod -R 744 /path/to/whole/directory/with/several/files/that/need/chmod
```

---

### Post by r-senior on 2011-05-17
Changing the file permissions and ownership does not prevent it being deleted if it is within a user-controlled directory. For example:

> 
$ touch temp.txt
$ sudo chown root.root temp.txt
$ sudo chmod 744 temp.txt
$ ls -l temp.txt
-rwxr--r-- 1 root root 0 2011-05-17 11:13 temp.txt
$ rm temp.txt
rm: remove write-protected regular empty file `temp.txt'? y
$ ls -l
total 0


To prevent deletion of a file, you have to remove write permissions from the containing directory. There are things you can do with the [sticky bit]("http://en.wikipedia.org/wiki/Sticky_bit") but the best solution is probably just to keep it in a directory owned by root (or another user).

---

### Post by konsolelover on 2011-05-17
thanks 4 ur replies! but i tried 
sudo chmod 700 file_with_dir
sudo chmod 744 file_with_dir
and also used chown but it didn't work.....
also could u plz explain the command with specific arguments as i am new to linux....
thnx

---

### Post by ironic.demise on 2011-05-17
> **r-senior said:**
> Changing the file permissions and ownership does not prevent it being deleted if it is within a user-controlled directory. For example:



To prevent deletion of a file, you have to remove write permissions from the containing directory. There are things you can do with the [sticky bit]("http://en.wikipedia.org/wiki/Sticky_bit") but the best solution is probably just to keep it in a directory owned by root (or another user).

So, checked this out.
the correct code would be ```
sudo chmod **1**744 /path/file
```
if I read correctly.

---

### Post by konsolelover on 2011-05-17
@ironic.demise
sorry bro ...but its not working

---

### Post by r-senior on 2011-05-17
> **ironic.demise said:**
> So, checked this out.
the correct code would be ```
sudo chmod **1**744 /path/file
```
if I read correctly.
Not quite ...

> [...] the Linux kernel ignores the sticky bit on files. [...] When the sticky bit is set on a directory, files in that directory may only be unlinked or renamed by root or their owner.

The directory permissions are the key ... try this (with a test file of course):

```

mkdir ~/Protected
mv thefile ~/Protected
chmod -w ~/Protected
rm ~/Protected/thefile
rm -rf ~/Protected

```

I think that would work. Better than using the sticky bit because you don't have to change the file ownership. If you want to prevent the file being edited, remove write permissions on the file itself:

```

chmod -w ~/Protected/thefile

```

You can achieve the above using Nautilus, by the way. Make a directory, drag your file, then set the permissions on the directory to access only.

---

### Post by dcsoldschool53 on 2011-05-17
Here is a web site explaining how to use the chmod command if you need it.

Chmod command
[http://catcode.com/teachmod/index.html](http://catcode.com/teachmod/index.html)

---

### Post by konsolelover on 2011-05-17
@r-senior
thanks bro finally it worked..:)

---

