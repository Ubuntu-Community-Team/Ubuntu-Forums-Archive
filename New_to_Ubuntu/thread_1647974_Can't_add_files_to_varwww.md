---
title: "Can't add files to /var/www"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by samaniac on 2010-12-18
Hey guys, I'm creating a website and I'm new to all this. I created some .php files and can't open them with firefox since I get a box that asks if I want to save file or open with... Anyway so I installed Apache and I was told to add the .php files to /var/www folder.But the problem is I can't put my files there. I get an error that says: Error moving file: Permission denied.
Could you please help?

---

### Post by davidmohammed on 2010-12-18
this [thread]("http://ubuntuforums.org/showthread.php?t=1509302") should get you going.

---

### Post by aikikode on 2010-12-18
Are you root? Ony root can copy/move files there.

---

### Post by sikander3786 on 2010-12-18
> **aikikode said:**
> Are you root? Ony root can copy/move files there.
sudo is enough. Root is disabled by default in Ubuntu.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

To the OP: This should work.

```
gksudo nautilus
```

---

### Post by gordintoronto on 2010-12-18
If you used Gedit to create the files, instead of just running Gedit, go to the terminal and enter the command:
gksudo gedit
Then you will be allowed to save the files wherever you want.

---

