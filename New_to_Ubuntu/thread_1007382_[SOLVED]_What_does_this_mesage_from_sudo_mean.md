---
title: "[SOLVED] What does this mesage from sudo mean?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Tom Atkins on 2008-12-10
Whenever I use sudo I get this uable to ... message. When I put in the password everything works fine. This just seemed to happen recently.

I am using HH and have been for several months and I really like it. It is on the sdb disk and always has been.

I also installed it on the a disk and then upgraded to II as an experiment and only have had a few problems which have been resolved. I will not be upgrading my main system until a new LTS version comes out.

```

tommy1@tommy1-desktop:~$ sudo fdisk -l
sudo: unable to resolve host tommy1-desktop
[sudo] password for tommy1: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cd3b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000abcfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9355    75144006   83  Linux
/dev/sdb2            9356        9729     3004155    5  Extended
/dev/sdb5            9356        9729     3004123+  82  Linux swap / Solaris


```

---

### Post by Titan8990 on 2008-12-10
post the output of the following:

cat /etc/hosts

---

### Post by Michael.Godawski on 2008-12-10
Additionally post also the result from these:
```
cat /etc/hostname
cat /etc/network/interfaces 
```

---

### Post by Bonger1901 on 2008-12-10
[http://ubuntuforums.org/showthread.php?p=4508774](http://ubuntuforums.org/showthread.php?p=4508774)

Here's an identical topic with a solution, you could try that? :)

---

### Post by Dedoimedo on 2008-12-10
And also /etc/resolv.conf :)
Dedoimedo

---

### Post by Tom Atkins on 2008-12-10
```

tommy1@tommy1-desktop:~$ sudo /etc/hostname
sudo: unable to resolve host tommy1-desktop
sudo: /etc/hostname: command not found
tommy1@tommy1-desktop:~$ sudo cat /etc/hostname
sudo: unable to resolve host tommy1-desktop
tommy1-desktop
tommy1@tommy1-desktop:~$ sudo cat /etc/interfaces
sudo: unable to resolve host tommy1-desktop
cat: /etc/interfaces: No such file or directory
tommy1@tommy1-desktop:~$ 


```

---

### Post by Michael.Godawski on 2008-12-10
Run the cat commands without the sudo.
Edited the last one; it should be
```

cat /etc/network/intrefaces
```

---

### Post by Titan8990 on 2008-12-10
None of those commands needed sudo.

you forgot to do cat in front of /etc/hostname, and on the last one you left out part of the directory (/etc/network/interfaces).

Anyways, I'm pretty sure I can solve your problem right now.


Type the following to edit /etc/hosts:


gksu gedit /etc/hosts

The file contains one line that says this:

tommy1-desktop


On the same line as that but with a space in between add 127.0.0.1. Save, then restart networking:


sudo /etc/init.d/networking restart

---

### Post by Michael.Godawski on 2008-12-10
This is my /etc/hosts. Just being curious: I have a **127.0.1.1**, the 127.0.0.1 is reserved for the localhost.

```
127.0.0.1    localhost
127.0.1.1    michael-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by Tom Atkins on 2008-12-10
Titian

I did that and it did not solve the problem

Tom

---

### Post by cariboo on 2008-12-10
It's been asked before, but could you paste the output of:

```
cat /etc/hosts
```

in your next post. Copy and paste the above command in a terminal, then paste the output in your next post.

Jim

---

### Post by Tom Atkins on 2008-12-10
tommy1@tommy1-desktop:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.0.1	tommy1-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
tommy1@tommy1-desktop:~$

---

### Post by Titan8990 on 2008-12-10
That is different than it was when you posted the output earlier....

---

### Post by Michael.Godawski on 2008-12-10
Try this:
change the line
```
127.0.0.1	tommy1-desktop
```
to 
```
127.0.1.1	tommy1-desktop
```

No guarantee though, but when you look at my previous post this would match my host file.

---

### Post by Tom Atkins on 2008-12-10
I changed it to 127.0.1.1 and it did not solve the problem.
```

tommy1@tommy1-desktop:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	tommy1-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
tommy1@tommy1-desktop:~$ 


```

---

### Post by Dedoimedo on 2008-12-10
Hello,

Declare all hostnames for localhost in one line.

Instead of:

```

127.0.0.1 localhost
127.0.0.1 tommyl-desktop

```

Use this:

```

127.0.0.1 localhost tommyl-desktop

```

I would also add this:

```

127.0.0.1 localhost localhost.localdomain tommyl-desktop

```

Dedoimedo

---

### Post by Tom Atkins on 2008-12-10
Thanks very much! That worked
tommy1@tommy1-desktop:~$ cat /etc/hosts
127.0.0.1 localhost localhost.localdomain tommyl-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
tommy1@tommy1-desktop:~$

---

### Post by Dedoimedo on 2008-12-10
Sure it works :)
hosts files take a single entry for a give ip. A well known issue when configuring all sorts of servers ...

Cheers,
Dedoimedo

---

### Post by Elfy on 2008-12-10
Does sudo work ok now?

---

### Post by Mr_Leo on 2008-12-11
hi all,

i had a similar message, "cannot resolve host", that showed up in the terminal. I also had noticeable lag in my network (using firefox, online gaming, etc).
editing the file /etc/hosts as descibed above, solved the problem.
thanks!

---

### Post by battlesound on 2008-12-25
wow, this seems to have cleared up a similar problem for my dad's computer.

First of all, I saw an old domain name in it.  So that had to go, anyway, but setting it up as Dedoimedo said worked.

*It's also much more responsive for networking, now.

Good job.  thanks.

---

