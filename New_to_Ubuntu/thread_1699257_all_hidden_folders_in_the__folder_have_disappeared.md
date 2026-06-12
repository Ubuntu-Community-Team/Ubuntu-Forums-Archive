---
title: "all hidden folders in the / folder have disappeared"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by moonpoppy on 2011-03-03
hi,

i'm using ubuntu 10.10

the hidden folders in the / folder have disappeared.

in preferences > file management > Views

i have "show hidden and back up files" checked.

nothing changed

i opened the synaptic file manager and entered ctrl + h. nothing changed.

i went into terminal and typed

cd /
ls -a

hidden folders still didn't appear

1015PEM:~$ cd /
1015PEM:/$ ls
AppFiles  System  Temporary  Users  Volumes
1015PEM:/$ ls -a
.  ..  AppFiles  .hidden  System  Temporary  Users  Volumes

what can i do to make the folders visible again?

---

### Post by maqtanim on 2011-03-03
Which hidden folder are you trying to view? When you say / folder, did you mean ROOT folder or the HOME folder?

Synaptic is not a file manager, it is a package manager. So Ctrl+h will not work there.

Just for a test, go to Places > Home Folder and press Ctrl+h. Then see what happen?

---

### Post by moonpoppy on 2011-03-03
all my hidden home folders are visible. i have no problem with hidden folders in any other directory.

by /

i mean root folder

i mean file management
not synaptic file manager.

---

### Post by Verbeck on 2011-03-03
in a normal ubuntu installation there wouldnt be any hidden files/folders in the file system root.
unless you created them yourself..

edit: are you sure it's ubuntu? because 'AppFiles  System  Temporary  Users  Volumes' is not how the folders are in the root filesystem of ubuntu 
(iirc, theres another distro that uses the mac like file tree)

---

### Post by moonpoppy on 2011-03-03
ok

i am a noob, clearly. but you gotta start somewhere.

98% of the root folders have disappeared. 

such as /usr, /var, /bin, etc. 

in terminal i typed

cd /usr
bash: cd : /usrs: no such file or dircetory.

how do i get these files back?

i'm using moonos 4 which is ubuntu 10.10. it has simply changed the name of a few folders. [http://moonos.org/forum/5-general-questions/453-file-system](http://moonos.org/forum/5-general-questions/453-file-system). by ctrl +l i canhave everything named as any other ubuntu 10.10 distro.

you can change it back. for all intents and purposes it is exactly the same.

---

### Post by CharlesA on 2011-03-03
If they were deleted, I don't see how the system would be running.

If they are indeed gone, the only way to recover from it is to reinstall.

---

### Post by moonpoppy on 2011-03-03
i dont know how the system is running either. that's why i don't think they are deleted and assumed they were hidden somehow.

if they aren't deleted, where did they go?

i use eudora for email and you have to back up from the /opt folder which has disappeared.

can someone please help?

---

### Post by moonpoppy on 2011-03-03
actually something i don't understand just happen

i opened a file window

i typed ctrl + l

and typed /usr

all the folders under usr appeared.

then i typed /bin

all the folders under /bin appeared.

but why are these folders not being listed when i open root folder or in terminal?

---

### Post by CharlesA on 2011-03-03
That doesn't make sense.

Can you post the output of this please:

```
ls -la /
```

---

### Post by moonpoppy on 2011-03-03
```
ls -la
total 32
drwxr-xr-x 23 root root 4096 2011-02-19 23:45 .
drwxr-xr-x 23 root root 4096 2011-02-19 23:45 ..
drwxr-xr-x  2 root root 4096 2011-02-27 17:57 AppFiles
-rw-r--r--  1 root root   19 2010-12-18 22:54 .hidden
drwxr-xr-x 10 root root 4096 2010-12-18 02:20 System
drwxrwxrwt 14 root root 4096 2011-03-03 12:55 Temporary
drwxr-xr-x  3 root root 4096 2011-02-01 23:37 Users
drwxr-xr-x  2 root root 4096 2011-03-03 12:51 Volumes

```

---

### Post by Verbeck on 2011-03-03
acording to this thread > [http://moonos.org/forum/5-general-questions/261-how-does-the-new-file-layout-work](http://moonos.org/forum/5-general-questions/261-how-does-the-new-file-layout-work) , check the files
/System/Settings/gobohide.conf
and
/System/Shared/initramfs-tools/init

---

### Post by moonpoppy on 2011-03-03
also i just tried to save a .png file of desktop. and then i tried to save some other files. i wanted to show you that i can access the usr directory via the ctrl + l method.

i can't save anything now.

---

### Post by moonpoppy on 2011-03-03
here is the gobohide folder settings

```
# configuration file of GoboHide in moonOS system
# Write down the path that you want to hide here

# +++ Old Unix file and directory +++
/bin
/cdrom
/etc
/home
/initrd.img
/initrd.img.old
/lib
/lib32
/lib64
/lost+found
/media
/mnt
/opt
/root
/sbin
/selinux
/srv
/tmp
/usr
/var
/vmlinuz
/vmlinuz.old

# +++ custom here +++
# /Users/foo/bar
```

---

### Post by moonpoppy on 2011-03-03
i searched for
/System/Shared/initramfs-tools/init

i have no shared folder under /Systems

---

### Post by matt_symes on 2011-03-03
Hi

> i'm using moonos 4 which is ubuntu 10.10. it has simply changed the name of a few folders. [http://moonos.org/forum/5-general-qu...53-file-system](http://moonos.org/forum/5-general-qu...53-file-system).

I think it might be a bit more than that. Which version are you using ? Why did you choose it as a distribution ?

Kind regards

---

### Post by Verbeck on 2011-03-03
try commenting out all of them in /System/Settings/gobohide.conf (put a # infront of each line)save the file, and restart the system. if it doesnt work, just revert the changes

---

### Post by moonpoppy on 2011-03-03
matt - 

moonos neak 4 is ubuntu 10.10 with a diff file system, lots of codecs preinstalled, appshell. apps preinstalled and lovely visuals. i use it because i love the way it looks and feels. it suits me. i tried about 7 or 8 distros over a 6 week period before i made my choice. i don't regret it. 

i'm going to put hash marks in front of folders and see what happens.

---

### Post by moonpoppy on 2011-03-03
how do i get root access into the gobohide.conf file?

i have a meeting now. i'll be back in about two hours...

shoot....

thanks for your help so far!

---

### Post by Verbeck on 2011-03-03
> **moonpoppy said:**
> how do i get root access into the gobohide.conf file?


```
gksu gedit /System/Settings/gobohide.conf
```assuming gedit is installed by default in moonos. else, replace gedit with your favorite text editor

edit: also take a look at [http://www.gobolinux.org/?page=doc/articles/gobohide](http://www.gobolinux.org/?page=doc/articles/gobohide)
```
gobohide -u* /bin*
```replacing /bin with the folder to unhide

---

### Post by matt_symes on 2011-03-03
Hi

> matt - 

moonos neak 4 is ubuntu 10.10 with a diff file system, lots of codecs preinstalled, appshell. apps preinstalled and lovely visuals. i use it because i love the way it looks and feels. it suits me. i tried about 7 or 8 distros over a 6 week period before i made my choice. i don't regret it. 


You have piqued my curiosity :P I am downloading both now and will have both installed in VM's within the hour.

Their forum is very quite. I can see why you posted here.

Kind regards

---

### Post by xaegis on 2011-03-03
> **matt_symes said:**
> Hi



I think it might be a bit more than that. Which version are you using ? Why did you choose it as a distribution ?

Kind regards

I'm a total novice but I found this on the moon Os Website:

"Chanrithy Thim has announced the release of moonOS 4, an Ubuntu-based desktop distribution with a ***_custom file hierarchy _***and a new experimental application framework."

Have you tried doing a search for the missing files in the filesystem?

---

### Post by moonpoppy on 2011-03-03
> **Verbeck said:**
> try commenting out all of them in /System/Settings/gobohide.conf (put a # infront of each line)save the file, and restart the system. if it doesnt work, just revert the changes

Verbeck, the # (hash marks) worked. thank you very much :). i can save files again. do you think this is sufficient to not have the issue again? but now the file browser menu launcher in awn is crashing! ridic. its like dominoes... 

Matt, i installed cardapio and recoll for searching for files. i am using a netbook, so i installed the global menu applet. i also like the file system, even though it's acting out right now.

---

