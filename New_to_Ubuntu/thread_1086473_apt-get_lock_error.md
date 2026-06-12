---
title: "apt-get lock error"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by romitm on 2009-03-04
I've looked in the forums and while others had a similar problem, I've tried to apply the solution given but it didn't work.

I'm on Ubuntu 8.04, and i was using the Update Manager when i realised it had frozen. So I killed the process and tried to restart it but it froze again. I tried invoking the software sources app but i got a blank dialog which i closed.

I tried running apt-get update and it gave me this error (after going through the software sources):
W: Not using locking for read only lock file /var/lib/apt/lists/lock
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

I tried deleting the lock file (as su) but get the following error:
rm: cannot remove `lock': Read-only file system

running apt-get clean doesn't remedy the situation.

What do I do?

Thanks a lot, folks.

---

### Post by yeats on 2009-03-04
what is the exact command you are running?  I'm wondering why it's telling you it's "read-only" - how are you using Ubuntu?  Installed on your hard drive?  Live CD?  Wubi?

---

### Post by linuxfreak1996 on 2009-03-04
This happned for me once. Luckely i was using wubi, so i did a reinstall :p

---

### Post by romitm on 2009-03-04
> **chrissharp123 said:**
> what is the exact command you are running?  I'm wondering why it's telling you it's "read-only" - how are you using Ubuntu?  Installed on your hard drive?  Live CD?  Wubi?

I'm running it of my Hard drive. I have the entire drive dedicated to the installation - no partitions.

Didn't understand what more detail you wanted about the command.

Thanks a lot!

---

### Post by tarps87 on 2009-03-04
What was the exact command you tried to use to remove the lock file?

---

### Post by DBrocks on 2009-03-04
```
 
sudo rm -f  /var/lib/apt/lists/lock
sudo rm -f /var/lib/dpkg/lock

```
 
If that doesnt work, post the output of 
```
 
 
ls -l /var/lib/apt/lists/lock

```
 
and
 
```
 
ls -l /var/lib/dpkg/lock

```

---

### Post by romitm on 2009-03-04
I just did a restart and the problem went away.

In order to remove i used sudo rm lock but didn't use rm -f. Maybe that was the problem?

Thanks a lot for your help - if I get to the same situation, I'll try the rm -f and post here what I get.

cheers

---

### Post by DBrocks on 2009-03-04
rm -f /path/to/file/you/wanna/destroy is for forcing deletion (thus the -f). Sounds like another instance of apt happened to lock the file, and that's probably why a restart worked. Well glad your back again.

---

### Post by DBrocks on 2009-03-05
Well, I looked into it. It seems that the reason you would get a lock error like that is because
 
A) Synaptic Package Manager si running
B) apt-get install is already running.
A reboot/Kill -9/ Closing of the offending programs should fix it in the future.
 
And also, I had the same thing happen to me a few hours ago. I tried the rm -f fix, and that seems to work. Just for future refrence.

---

### Post by bsgjn on 2011-10-17
I have the same issue on a new ubuntu 11.4 install. Installed 3 times same issue when I go to use apt-get:

Not using locking for read only lock file /var/lib/dbkg/lock, unable to write to /var/cache/apt.

any idea?

---

