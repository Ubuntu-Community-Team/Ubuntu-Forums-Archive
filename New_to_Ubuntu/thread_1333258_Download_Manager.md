---
title: "Download Manager"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Dinesh Balaji on 2009-11-21
I need a good download manager for ubuntu... like Internet Download manger for Windows.. or equivalent to that!!!..Tnx

---

### Post by llamakc on 2009-11-21
There are more than a few available in the repositories. Care to share an example of when you would need one?

---

### Post by mick222 on 2009-11-21
What about DownThemAll! 1.1.7 for firefox . There's also prozilla but cant find a deb for it .

---

### Post by cm06mrs on 2009-11-21
is there a linux download manager for handling rapidshare links?

---

### Post by Vadi on 2009-11-21
Yep, Tucan is a good one. It's in the Ubuntu Software Centre, or click [here to install]("apt:tucan")

---

### Post by cm06mrs on 2009-11-21
awesome, thanks

---

### Post by ayenack on 2009-11-21
wget is an excellent download manager and it's already installed on your system. I pretty much use it exclusively these days.

It's run in terminal. So at command prompt.

```
wget http://www.file.com/file
``` (Where "www.file.com/file" is the file you want to download.)

and if the download stalls you can use the -c (continue) command to resume it.

```
wget -c http://www.file.com/file
```

It's also possible to drag files into the terminal if you are not sure what the address is, however this does not always work.

So lets say you want to download one of the older Ubuntu versions you'd open a terminal type in wget and then drag that link into the terminal and get this.

```
wget http://releases.ubuntu.com/6.06/ubuntu-6.06.2-server-i386.iso
```

It a very good and light solution to downloads and far more reliable than the default down-loader in FireFox. Use the man pages for a run down of all commands for wget.

---

### Post by Dinesh Balaji on 2009-11-24
awesome...thnx!!!:popcorn:

---

