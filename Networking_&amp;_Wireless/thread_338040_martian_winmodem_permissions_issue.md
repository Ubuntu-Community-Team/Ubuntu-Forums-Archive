---
title: "martian winmodem permissions issue"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by blundr on 2007-01-13
Greetings all,

I have successfully installed the martian software in order to recognize the modem in this system.  however, i am only able to use the device when root.  here is what i've done so far:

i have: 
```
/usr/sbin/martian_modem --daemon --syslog
```

in /etc/rc.local

which creates a new device: 

```
lrwxrwxrwx 1 root root 10 2007-01-13 21:36 /dev/ttySM0 -> /dev/pts/0
```

taking a look at /dev/pts/0 i see:

```
crw--w---- 1 root tty 136, 0 2007-01-13 21:36 /dev/pts/0
```

the user needs write permission, and is a member of the 'dialout' group.  so my next step is:

```
root@tbc-desktop:~# chown root:dialout /dev/pts/0
root@tbc-desktop:~# chmod 660 /dev/pts/0
root@tbc-desktop:~# ls -l /dev/pts/0
crw-rw---- 1 root dialout 136, 0 2007-01-13 21:36 /dev/pts/0
```

now, everything appears to be all set.  next, i run gnome-ppp, click on setup, then click on Detect.  it is able to find the modem located at /dev/ttySM0.  

now when i attempt to connect, i get a permission denied error.  taking a look at /dev/pts/0, i see that the permissions have been reset to what they were before:
```
crw--w---- 1 root tty 136, 0 2007-01-13 21:52 /dev/pts/0

```

I have read where others have suggested that you run gnome-ppp via 'gksudo gnome-ppp' and that does work.  However, i'm setting this machine up for my grandmother, so the fewest steps possible is better in my opinion.

Can anyone offer help on how to resolve this issue?  if there is a way to make the permissions stick to root:dialout with 660, that would be great.  the gksudo method doesn't appear to be a good solution to me.

Thanks in advance!

---

### Post by blundr on 2007-01-13
as an update to my question, i have also done the following:

I read where making changes to the permissions via adding an item in /etc/udev/rules.d/ might fix the issue.

so i created a file called /etc/udev/rules.d/martian.rules that contains:
```
KERNEL="ttySM[0-9]", MODE="0660", GROUP="dialout", SYMLINK="modem"
KERNEL="pts0", MODE="0660", GROUP="dialout", SYMLINK="modem"
```

i tried it first with just the first line, but realizing that /dev/ttySM0 is a symlink, i added the second line for the device it points to.  doing this also did not solve the problem.

Thanks!

---

### Post by blundr on 2007-01-14
i solved the problem.  the answer was to replace: 

```
/usr/sbin/martian_modem --daemon --syslog
```

with 

```
martian_modem --daemon --user=root --group=dialout --mode=0660
```

in /etc/rc.local

subsequently, the /etc/udev/rules.d/martian.rules file can be deleted.

---

