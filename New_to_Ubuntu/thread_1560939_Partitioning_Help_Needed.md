---
title: "Partitioning Help Needed"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by Verbeck on 2010-08-25
some website gave me these instructions for manual partitioning.
10gb /
10gb /usr
2gb swap
(the rest)228gb /home

what do these mean and where are the installed programs stored (like 'c>program files' in windows)?

---

### Post by Rubi1200 on 2010-08-25
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

Hope this helps.

---

### Post by apmcd47 on 2010-08-25
Most of the system files will be installed in /, eg
[LIST]
[*]*/bin, /usr/bin* for programs
[*]*/lib* for library files, eg the Linux equivalent of dll files
[*]*/etc* for system wide configuration files
[*]*/var* for some config and also log files
[/LIST]
The swap partition is for swapping program memory to disk to allow the machine to use apparently more memory than it actually has, and for hibernating the computer.

/home is where the user data is kept.

This is very general and not a full description of what they are for.

Hope this helps.

Andrew

---

### Post by leprkhn on 2010-08-25
"10 gb /"
Means that you are dedicating a 10gb partition to your root directory "/" (where EVERYTHING lives, like C:\)

"10 gb /usr"
Means take the "/usr" (this is a lot like your "Program Files" in Windows... Kinda) directory (and everything in it) from "/" (the root directory) and mount it on a separate partition.

"2 gb swap"
Swap space is like the Windows Paging File. If your RAM overflows, it will use the swap space as extra room. This is always in it's own partition.

"228 gb /home"
Means (much like the "/usr" bit) take your "/home" directory (like your "C:\Users" or "C:\Documents and Settings" on Windows - this is where all your - and all other users besides the root user - keep their personal files; every user gets a "/home/username" directory) and mount it on a separate partition.

If you're new to Linux my advice would be to keep everything (except swap, that is) on one partition. Especially if you're using Ubuntu on the Desktop/Laptop/Workstation (Servers are a bit different). If you're still interested in why you were told that splitting them up is a better option, see the following link:
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by Verbeck on 2010-08-25
Thanx for the explanation :)

---

### Post by srs5694 on 2010-08-25
> **leprkhn said:**
> If you're new to Linux my advice would be to keep everything (except swap, that is) on one partition. Especially if you're using Ubuntu on the Desktop/Laptop/Workstation (Servers are a bit different). If you're still interested in why you were told that splitting them up is a better option, see the following link:
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

I disagree. IMHO, separating /home from everything else is a useful practice, even for new users. Doing this simplifies upgrades and re-installations, since you can easily wipe out everything on the root filesystem without damaging user files, which can remain untouched on /home. Splitting /usr off, as in the original post, is a more debatable practice. I do this myself, but its benefits aren't as clear-cut for a new user.

Depending on the available space for Linux, I'd make swap 1-2 times the available RAM, root (/) 10-20GB, and /home everything else (but ideally at least as big as the root filesystem).

---

