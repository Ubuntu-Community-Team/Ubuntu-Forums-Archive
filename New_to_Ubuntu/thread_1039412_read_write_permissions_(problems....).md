---
title: "read write permissions (problems....)"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by 4E.Kipper on 2009-01-14
hi there, trying to change permissions of /media/crap

i've used sudo chown kipper:kipper /media/crap to change the owner, and yet it says i do not have permissions?

the /etc/fstab file reads like this for the partion i want to read/write to...

```
# Entry for /dev/sda7 : UUID=dd4f83b8-4dc9-4fd4-9070-b557093dc152 /media/crap ext3 relatime,errors=remount-ro 0 2
```

should it be -rw ? or not?

i'm a tad confused as on my desktop all i did was the sudo chown command and it worked fine, now on my laptop it has decided that instead of letting me own it, it wont even let me read the files!!!


halp!

thanks,
kipper

---

### Post by Titan8990 on 2009-01-14
Edit: it should be:

sudo chown -R kipper:kipper /media/crap

---

### Post by 4E.Kipper on 2009-01-14
cheers, i;ve done that. yet i still get

```
You do not have the permissions necessary to view the contents of "crap".
```

what could cause this?

---

### Post by Bölvaður on 2009-01-14
> **Titan8990 said:**
> Edit: it should be:

sudo chown -R kipper:kipper /media/crap

wouldnt it be enough to ```
sudo chown kipper /media/crap
``` as there shouldnt be any subdirectories and saying kipper just makes him the user of the directory.

I think you are trying to connect your laptop with your desktop computer with nfs am I correct? (I do that too)

You should have rw instead of ro in fstab.

here is my line from fstab
```

192.192.192.192:/home/laptop/public/ /media/mountedLaptop/ [COLOR="Red"]nfs[/COLOR] rsize=8192,wsize=8192,timeo=14,intr
```

hope it helps

btw I see that your entry is trying to mount a local hdd partition, but I cannot see anything wrong with it.. perhaps try to use /dev/sda7 instead of the uuid



> **4E.Kipper said:**
> cheers, i;ve done that. yet i still get

```
You do not have the permissions necessary to view the contents of "crap".
```

what could cause this?

chmod a+x may help

---

### Post by 4E.Kipper on 2009-01-14
no, i have no intention of connecting them.  i;ve got a 0.5tb exthd for that shifting stuff between.

i can now have permissions to read /media/crap

just cannot write to it.  this is annoying me now. it worked perfectly before...********

---

### Post by Bölvaður on 2009-01-14
sudo chmod 755 /media/crap

check if it works and then send us the output of:

ls -l /media | grep crap

(this command lists out all the information on /media/ and then filters out only the crap directory)

---

### Post by Michael.Godawski on 2009-01-14
hi, 
can you please post the output of 

```
ls -la /media
```

---

### Post by 4E.Kipper on 2009-01-14
output of ls -la /media

```
total 40
drwxr-xr-x  6 root   root    4096 2009-01-14 18:57 .
drwxr-xr-x 20 root   root    4096 2009-01-14 18:33 ..
drwxrwxrwx  1 root   root   16384 2009-01-14 16:06 ACER
lrwxrwxrwx  1 root   root       6 2009-01-14 16:57 cdrom -> cdrom0
drwxr-xr-x  2 root   root    4096 2009-01-14 16:57 cdrom0
drwxrwxrwx  3 kipper kipper  4096 2009-01-14 16:57 crap
-rw-r--r--  1 root   root      86 2009-01-14 18:37 .hal-mtab
-rw-------  1 root   root       0 2009-01-14 18:37 .hal-mtab-lock
drwxr--r--  2 root   root    4096 2009-01-14 18:57 PQSERVICE

```

output of ```
ls -l /media | grep crap
```

```
drwxr-xr-x 3 kipper kipper  4096 2009-01-14 16:57 crap
```


that ok?  anything else needeD?

---

### Post by Titan8990 on 2009-01-14
That is odd, ls -al showed different permissions that ls -l?

---

### Post by 4E.Kipper on 2009-01-14
i dont know....but it works now.  rebooted..abd..well..it works

it normally works after unmounting then mounting. but nevermind. all gravy now.

cheers guys!

still cant find a reason to fault these forums, all my problems have been sorted on the day i posted, if i cant find an existing thread.

---

