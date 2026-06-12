---
title: "etc corrupt after chmod"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by gnidde on 2009-01-11
Hi,

I did something really stupid.

First I did (located at root)

sudo chmod 777 etc

then I did

sudo chmod 766 etc

I know, stupid.

However, now my system is really corrupt since all files in /etc has corrupt owner etc. How can I restore it?

Please help

---

### Post by spiderbatdad on 2009-01-11
If the above are the commands you ran, you have not changed the permissions of all the files in /etc. To correct /etc: ```
sudo chmod 755 /etc
```

---

### Post by kestrel1 on 2009-01-11
OOps

---

### Post by gnidde on 2009-01-11
Thanks, but I solved it by going in recovery mode to root shell and run 

chmod 755 /etc

The problem was that I wasn't able to run sudo without execute rights on /etc...

Learned my lesson...

---

### Post by spiderbatdad on 2009-01-11
According to your post sudoers never lost execute permissions. Perhaps the user account you are working from is not a member of sudoers. /etc is owned by root so 777, 766 7** never removes execute permissions from sudoers, and any admin could still run sudo chmod to fix the problem without the need of recovery mode.

---

### Post by lswb on 2009-01-11
> **gnidde said:**
> Hi,
I did something really stupid.
First I did (located at root)
sudo chmod 777 etc
then I did
sudo chmod 766 etc
I know, stupid.

However, now my system is really corrupt since all files in /etc has corrupt owner etc. How can I restore it?

Please help

Well, it's not as bad as if you had done it to /.

Really, it may be recoverable if all you did was a chmod. (You didn't do any chown commands  or use -R I hope) Almost all files in /etc are owned by root and rwxr-xr-x or rw-r--r-- There are a few directories and files that are ( by default) only read/writeable by root.

I would start by **sudo chmod 755 /etc** which hopefully will at least give you a useable system. The unneeded x permissions on non-script files shouldn't keep anything from running. The hard part will be identifying the files and directories that should not be readable/executable by regular users. If the chmod 755 gets you a useable system you could backup what you want to keep and reinstall, or you could slog through the /etc directory and change permissions, which would be a real chore IMHO. The files that come to mind are the password and shadow files. 

If you are the only user of your system and it works OK after the chmod 755, maybe you can just live with it until your next upgrade.

---

