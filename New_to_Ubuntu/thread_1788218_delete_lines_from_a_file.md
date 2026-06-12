---
title: "delete lines from a file"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by shalomm on 2011-06-22
Hi guys, 

I having a problem, 
I need to delete all lines except last 50 from a file.
The problem is I can use "sed" or bash commands (can't use awk and tail), and I don't know the how many lines the file contain.

Thanks

---

### Post by sisco311 on 2011-06-22
> **shalomm said:**
> can't use awk and tail

Why? tail is part of coreutils which is installed on almost any Linux system (even on my router). 

Is this your homework?

---

### Post by shalomm on 2011-06-22
Thanks for the quick reply.
I need to do it while the system is booting up and not all the partition are mounted.
I'm working on very old machine, and can't change any thing there, not the mounting order or the programs/commands location.
I know how to delete the last 50 lines form a file by using "sed", but is there a way to revers the output and print out these last 50 lines?

Thanks

---

### Post by sisco311 on 2011-06-22
> **shalomm said:**
> Thanks for the quick reply.
I need to do it while the system is booting up and not all the partition are mounted.
I'm working on very old machine, and can't change any thing there, not the mounting order or the programs/commands location.
I know how to delete the last 50 lines form a file by using "sed", but is there a way to revers the output and print out these last 50 lines?

Thanks

Oh, I see... Check out: [http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)

You can do something like:
```
sed -e :a -e '$q;N;**51**,$D;ba' file
```

---

### Post by shalomm on 2011-06-22
Thanks a lot!!
That's exactly what I was looking for.

Thanks

---

### Post by sisco311 on 2011-06-22
You're welcome!

---

