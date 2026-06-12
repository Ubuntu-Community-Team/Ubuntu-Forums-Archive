---
title: "CHMOD - From root to the user"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by Apostolique on 2010-08-19
How do I change the permission on a file that is currently owned by the root so that it becomes owned by the user?

---

### Post by surfer on 2010-08-19
```
$ sudo chown user:group the_file
```

where user is your usename, group is your group and the_file is... well... the file.

if you want do recursively change owner, chown has a -R switch and instead of the file, give the directory:

```
$ sudo chown -R user:group the_directory
```

attention: if you mistakenly chown / (or some other system directory), your system may become unusable and you will have to reinstall...

---

### Post by Rubi1200 on 2010-08-19
I have a question:

what file are you trying to change and why?

If you just want to open and look at the contents of the file or even modify it you, there are other ways of doing so.

There is a reason certain files are owned by root; it's called the security and stability of your system.

---

### Post by KdotJ on 2010-08-19
The command you will need is not chmod but in fact:

```
chown
```

I can't remember the exact usage, but type:

```
man chown
```

For details. You will need to run this with sudo to change it from root ownership

EDIT: got beaten to it lol

---

### Post by dagdeniz on 2010-08-19
You're not trying to change permissions, you're trying to change the owner. So you'll use chown, not chmod. 
chown username /path/to/file
or 
chown userid /path/to/file

---

### Post by Apostolique on 2010-11-08
> **Rubi1200 said:**
> I have a question:

what file are you trying to change and why?

If you just want to open and look at the contents of the file or even modify it you, there are other ways of doing so.

There is a reason certain files are owned by root; it's called the security and stability of your system.

My bad for taking so long to respond... The reason I needed to change the permission was because I had, by accident, executed a program as the root. It created a couple files that were owned by the root. The problem was that when I tried to run the program again, without root privileges, it wouldn't work. Changing the file permissions fixed it.

---

