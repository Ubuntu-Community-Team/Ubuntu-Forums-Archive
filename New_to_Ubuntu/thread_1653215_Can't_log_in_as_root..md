---
title: "Can't log in as root."
date: 2010-12-26
forum: New to Ubuntu
---

### Post by IWantFroyo on 2010-12-26
In trying to log in as root, I put su -
It asked me for a password.
I put in my usual password, which didn't work.
What am I doing wrong?

The reason I tried to log in as root is because it wouldn't let me move a download (d-bus) from downloads to etc OR otd.](*,)

---

### Post by TeoBigusGeekus on 2010-12-26
```
sudo mv /path/to/file/filename /etc/new/path/filename
```

---

### Post by mcduck on 2010-12-26
You are not even supposed to be able to log in as root that way.

Su asks for target user's password. And root account is locked on Ubuntu, so you don't have such password.

Use "sudo" to run your command instead, or "sudo -i" to open a terminal session as root.

And you should probably read this as well: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by lisati on 2010-12-26
The security model used with Ubuntu is aimed at using the "sudo" command in preference to "logging in as root."

Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Edit: Beaten to it! :D

---

### Post by mike555 on 2010-12-26
if your going to do a lot of file moving you might want to install "Nautilus-gksu" , it will let you open Nautilus as SU ....

---

### Post by theozzlives on 2010-12-26
> **mike555 said:**
> if your going to do a lot of file moving you might want to install "Nautilus-gksu" , it will let you open Nautilus as SU ....

Or just hit alt+F2 and type "gksu nautilus" (without the quotes) in the run box. You don't want to much access to root. The easier it is for you, the easier it is for a hacker.

---

### Post by IWantFroyo on 2010-12-26
OK thanks for all your help guys! :)

---

