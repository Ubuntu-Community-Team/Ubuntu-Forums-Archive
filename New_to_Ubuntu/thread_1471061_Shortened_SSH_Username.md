---
title: "Shortened SSH Username"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by musicman10489 on 2010-05-03
I have set up an ssh server with a friend of mine and everything is working well but there is one thing I have noticed. When I log in to this server instead of displaying the usual (username@domain~$) it only displays ($). When I su though it then shows (root@domain~#).  When my friend logs in using his username it shows (username@domain~$). So it seems that my account is the only one that does not display everything even though our accounts are both in the same group and have the same privileges. 

I am still getting my arms around linux so it is very possible that it is something simple that I am missing but I just can't seem to figure out why this is happening and I can't find anything about it on the forums.
Thanks in advance for the help :]

---

### Post by musicman10489 on 2010-05-03
If anyone comes across this here is the answer on how to change that. [http://ubuntuforums.org/showthread.php?t=109910](http://ubuntuforums.org/showthread.php?t=109910)

---

### Post by OffAxis on 2010-05-03
a list of all possible settings for the prompt is also in the man page for bash; it starts about line 2450.

```
man bash
```

if you want to check your syntax for the prompt variables you can use echo

```
echo $PS1
```

$PS1 = (variable) **P**rompt **S**tring **One**
in case you were wondering.

---

### Post by musicman10489 on 2010-05-03
Thank you! This helps even more!

---

