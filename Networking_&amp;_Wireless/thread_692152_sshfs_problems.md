---
title: "sshfs problems"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by x300 on 2008-02-09
So, the problem is that I can't open the mounted sshfs folder.

On the client I wrote:

```
sudo sshfs usr@192.168.0.7:/home/usr mnt/
```

I typed the psw for usr and got no errors.
Now I tried to change directory to usr. This gives the error:

```
usr2@othercomp:~$ cd mnt
bash: cd: usr: Permission denied
```

Then I tried to see the permissions for usr:

```
usr2@othercomp:~$ ls -l
total 3
drwx------ 2 usr2 usr2 4096 2008-02-08 22:33 Desktop
?--------- ? ?      ?         ?                ? mnt
```

When I do this with sudo I get:

```

usr2@othercomp:~$ sudo ls -l
total 7
drwx------ 2 usr2 usr2 4096 2008-02-08 22:33 Desktop
drwxr-xr-x 1 usr2 usr2 4096 2008-02-09 16:50 mnt
```

The same thing applies to other commands. When typing "ls mnt" i get permission denied but "sudo ls mnt" gives me the correct output.


Anyone knows what to do to enter the folder?

---

### Post by Nicklas Overgaard on 2008-02-11
I assume your username is "usr2". Then try to do the following:

```

sudo chown usr2 mnt/
chmod ug+rw mnt/

```

---

