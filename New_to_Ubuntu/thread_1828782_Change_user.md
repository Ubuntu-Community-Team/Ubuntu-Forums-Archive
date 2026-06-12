---
title: "Change user"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by vagelism on 2011-08-19
Hello to all.
I did something stupid and changed my /Desktop owner to root.
The rest files and folders are still on users ownership.
I type
sudo chown user /Desktop 

No errors appear but still the owner of the user/Desktop is the root.
Hopfully no other problems  coused!
Any ideas?
Thank you!

---

### Post by Bachstelze on 2011-08-19
If you really ran that command, it should have told you that /Desktop does not exist? What command did you run, **exactly**?

---

### Post by fdrake on 2011-08-19
can you post :
```

ls -al /home/YOUR_USERNAME/Desktop
```




> 
I did something stupid and changed my /Desktop owner to root


what eactly did you type?
use
```

 history | less 
```
and copy and paste the command in here please.

---

### Post by vagelism on 2011-08-19
> **fdrake said:**
> can you post :
```

ls -al /home/YOUR_USERNAME/Desktop
```






what eactly did you type?
use
```

 history | less 
```
and copy and paste the command in here please.


#unknown@unknown-DURABOOK:~$ ls -al /home/unknown/Desktop/
total 12
drwsr-xr-x  3 root    root    4096 2011-08-19 19:34 .
drwxr-xr-x 39 unknown unknown 4096 2011-08-19 23:07 ..
drwxr-xr-x  3 unknown unknown 4096 2011-08-19 19:56 test
unknown@unknown-DURABOOK:~$ 

#

Ok this is it!
I did many things...first accidently delete Deskto folder then create it again.
THANK YOU

---

### Post by fdrake on 2011-08-19
> **vagelism said:**
> #unknown@unknown-DURABOOK:~$ ls -al /home/unknown/Desktop/
total 12
drwsr-xr-x  3 root    root    4096 2011-08-19 19:34 .
drwxr-xr-x 39 unknown unknown 4096 2011-08-19 23:07 ..
drwxr-xr-x  3 unknown unknown 4096 2011-08-19 19:56 test


first of all the Desktop folder is still under root's ownership

second the home folder of your username and the test folder on the desktop have as user "unknown" and as group "unknown". are those your usernmae and groupname? if yes then try:
```

sudo chown unknown /home/unknown/Desktop
sudo chgrp unknown /home/unknown/Desktop

```

---

### Post by vagelism on 2011-08-19
> **fdrake said:**
> first of all the Desktop folder is still under root's ownership

second the home folder of your username and the test folder on the desktop have as user "unknown" and as group "unknown". are those your usernmae and groupname? if yes then try:
```

sudo chown unknown /home/unknown/Desktop

```

Correct...USERNAME=unknown and GROUP=unknown
so I suppose /Desktop should be also unknown
correct? How can I change it?

---

### Post by fdrake on 2011-08-19
> **vagelism said:**
> Correct...USERNAME=unknown and GROUP=unknown
so I suppose /Desktop should be also unknown
correct? How can I change it?

check my post . I edited with the commands to use

---

### Post by vagelism on 2011-08-19
> **fdrake said:**
> check my post . I edited with the commands to use

Thank you!
Works great!

---

