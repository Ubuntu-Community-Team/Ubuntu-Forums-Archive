---
title: "Unable to delete a file"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by karthick87 on 2010-04-01
I am unable to delete a file from my home directory,it says “[COLOR=Red]Error removing file: Operation not permitted[/COLOR]” So how to delete that file?

---

### Post by mcoleman44 on 2010-04-01
Just to be sure, You are using sudo rm?

---

### Post by karthick87 on 2010-04-01
Am sure i am using sudo infront of the command..

```

karthick@Learners-desktop:~/Temp$ sudo rm "Register Number"
rm: cannot remove `Register Number': Operation not permitted

```

---

### Post by jms1989 on 2010-04-02
use rm -r to delete directories and if you need root, put sudo in front.

---

### Post by karthick87 on 2010-04-02
Thats not a directory.!

---

### Post by ven_ on 2010-04-02
You could try changing permissions before you delete it, although that probably isn't the issue if you are using sudo.  Also, you could try checking if the file is being used somewhere you dong' know about?  Another option could be to move it to a different folder and try to delete from there, on the off-chance that would make a difference...
 
Good luck!

---

### Post by wojox on 2010-04-02
Did you try:

```
sudo rm -f Register\ Number
```

---

### Post by karthick87 on 2010-04-02
Sorry immutable flag is set,thats why i couldn't delete the file.I have unset the flag and now i am able to delete the file..

---

### Post by @rizz on 2010-04-02
hi,

   I agree with WOJOX, the space between the two words is the problem I believe!

try this first:

```
$ rm -f Register\ Number 
```

 It should work...... if in case it doesn't
 then go sudo:

```
$ sudo rm -f Register\ Number
```

---

