---
title: "Need help using MD5SUM,  please."
date: 2011-06-06
forum: New to Ubuntu
---

### Post by L Campbell on 2011-06-06
I want to check the .iso file of 10.04.2 and started reading here:-

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

In here it states:-

First open a terminal and go to the correct directory to check a downloaded iso file:

    cd download_directory

This is what I got:-

qwer@qwer-P9852A-ABA-753N:~$ cd download_directory
bash: cd: download_directory: No such file or directory
qwer@qwer-P9852A-ABA-753N:~$ 

So then, since the file is in my Downloads, I tried:-

cd downloads

and got this:-

qwer@qwer-P9852A-ABA-753N:~$ cd download_directory
bash: cd: download_directory: No such file or directory
qwer@qwer-P9852A-ABA-753N:~$ 

I would appreciate it if you would tell me what I'm doing wrong.

TIA

---

### Post by raja.genupula on 2011-06-06
there download_dir is  just given for general understanding
that means there you need to give the name of the directory where you had download that file or something 
check in which dir u had download that and go on

---

### Post by seawolf167 on 2011-06-06
Try this

```
cd ~/Downloads
```

---

### Post by L Campbell on 2011-06-06
> **seawolf167 said:**
> Try this

```
cd ~/Downloads
```

That worked PERFECTLY,thanks.

Also, the numbers matched perfectly.

---

### Post by seawolf167 on 2011-06-06
Awesome :) Take a look at the link "LinuxCommands" in my signature if you are interested in learning more about linux commands.

---

### Post by dFlyer on 2011-06-06
I see your problem. When you tried to cd downloads, that directory doesn't exist in linux. Yes there is a Downloads directory. Notice the Capital D. Under linux, downloads/Downloads/DOWNLOADS/DownLoads and all different. You must use proper case when typing in linux. Now cd to Downloads if that is where you saved the file and run:

md5sum name.of.file.you.want.to.check

---

### Post by ajgreeny on 2011-06-06
First point to remember that is **VERY** important, is that unlike windows and DOS, the Linux command line **is** case sensitive, so **downloads** is not the same as **Downloads**.

It's one of the things that catches out a lot of users when they first move to Linux

---

### Post by CharlesA on 2011-06-06
> **ajgreeny said:**
> First point to remember that is **VERY** important, is that unlike windows and DOS, the Linux command line **is** case sensitive, so **downloads** is not the same as **Downloads**.

It's one of the things that catches out a lot of users when they first move to Linux
Yep, and it can cause hell with Windows too, if you share files between Linux and Windows.

---

### Post by ajgreeny on 2011-06-06
I'm sure it can, but I've no windows to share with, thank goodness.

---

