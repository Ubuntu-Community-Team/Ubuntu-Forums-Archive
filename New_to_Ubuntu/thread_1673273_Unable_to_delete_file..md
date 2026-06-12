---
title: "Unable to delete file."
date: 2011-01-22
forum: New to Ubuntu
---

### Post by theboneripper on 2011-01-22
[SIZE=2]Hi, 

A couple of days back i saved some pages from firefox into a folder on my desktop and then transferred it to a drive which i also use for windows.

I came back to the folder today and it has the same name but strangely changed into a movie. What was around 2mb has turned into a 700mb file now. (I know this sounds weird)

I can't delete it and get this error.
"unable to trash file. No such file or directory." A similar error when i try to rename it.

i tried using the sudo nautilus cmd to delete it from root, but no luck.

Also logged into my windows os, got the same error. 

Please help!
Thanks.
[/SIZE]

---

### Post by meson2439 on 2011-01-22
I recommend the terminal for this job. So open one. 
**Warning: I assume you know some terminal commands such as cd and rm.**

Next you must navigate to that folder and use 

```
sudo rm -f persistent_file.avi
```

replace that with the necessary file name. Be careful of the code above because I don't want you deleting something else.

If in doubt, give the full path and filename. Me or others could instruct on the appropriate command.

---

### Post by matt_symes on 2011-01-22
Hi

> A couple of days back i saved some pages from firefox into a folder on my desktop and then transferred it to a drive which i also use for windows.

I came back to the folder today and it has the same name but strangely changed into a movie. What was around 2mb has turned into a 700mb file now. (I know this sounds weird)

I can't delete it and get this error.
"unable to trash file. No such file or directory." A similar error when i try to rename it.

Was it an external or USB drive ? Did you unmount the external drive correctly ?

If deleting it from the terminal does not work as suggested by the poster above then try fsck.

Open a terminal and type

```
sudo touch /forcefsck
```

Enter your password as normal. This will not be echoed to the screen. 

Reboot to run fsck.

Kind regards

---

### Post by theboneripper on 2011-01-22
@meson 2439 : 

Thanks a lot, I changed some file permissions and using that command it worked!

@matt_symes :

Thank you too. "fsck" could come in handy sometime. New to linux.


Any idea how that folder changed into a movie on its own?

---

### Post by meson2439 on 2011-01-22
No problem.

It's probably because firefox reserved those files for it. When you quit the download, the necessary space are been reserved. And it stays thats way.

---

### Post by theboneripper on 2011-01-22
Ok. Strange though.

---

