---
title: "Mounting a Windows partition over LAN."
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by Fr0ns on 2007-08-18
Hello,

I've been trying to build a dedicated virus scanner for scanning over lan. Therefore I want to automount my Windows partition over LAN. This has to appear as a folder since it won't scan a file. I've tried some articles but I couldn't get them to work since they were quite vague.

Thanks in advance!

[I]
Ubuntu 7,04 i386
Windows XP Pro SP2, partition is NTFS and is called C
IP: 192.168.2.40, Lan name: FRANSPC
[/I]

---

### Post by Jamie Jackson on 2007-08-19
Your question is a little confusing.

*Isn't the partition on the same machine as Ubuntu?
*If so, why do you want to involve networking?

---

### Post by Fr0ns on 2007-08-20
No the partition is located on my Windows XP machine. And i need it mounted on my Ubuntu machine.

---

### Post by Jamie Jackson on 2007-08-20
Assuming you've already shared the drive in XP, [this]("http://ubuntuforums.org/showthread.php?t=501575") should get you going.

---

### Post by Fr0ns on 2007-09-04
> **Jamie Jackson said:**
> Assuming you've already shared the drive in XP, [this]("http://ubuntuforums.org/showthread.php?t=501575") should get you going.

Thanks for your reply and sorry for reading it so late.

I've used the [thread]("http://ubuntuforums.org/showthread.php?t=501575") you linked to and used the [link]("http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html") from there to make a permanent mount using /etc/fstab. Also installed smbfs.

I' m having problems though, to test my setup I use.
```
frans@fransserver:~$ sudo mount -t smbfs //franspc/c /media/cfrans
```

This works fine, when I add this to /etc/fstab the problems start. The guide states the example:
```
//servername/sharename /mountdirectory smbfs username=windowsuserename,password=windowspassword 0 0
```

So I used:
```
//franspc/c/    /media/cfrans   smbfs     defaults        0       0
```

What did I do wrong?

---

### Post by Jamie Jackson on 2007-09-04
What sort of problems are you having? Also, have you tried it with the windows credentials, as in the example?

---

### Post by Fr0ns on 2007-09-04
> **Jamie Jackson said:**
> What sort of problems are you having? Also, have you tried it with the windows credentials, as in the example?

Can't because I don't have a password, and it does work without a username and pass when mounting from command line.

The problem is that nothing shows up in /media/cfrans :(

---

### Post by Jamie Jackson on 2007-09-04
Gotcha. I haven't used fstab for automounting network shares, but hopefully someone else will step in.

---

