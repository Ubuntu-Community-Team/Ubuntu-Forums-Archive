---
title: "Error message. List of sources couldn't be read."
date: 2009-12-16
forum: New to Ubuntu
---

### Post by Whizpopthat on 2009-12-16
I keep getting this error message: 
'E:Type '--2009-12-16' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

Could anyone help me with this problem?

Please, Thanks.

---

### Post by daenoid on 2009-12-16
> **Whizpopthat said:**
> I keep getting this error message: 
'E:Type '--2009-12-16' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

Could anyone help me with this problem?

Please, Thanks.

Take a look at [http://ubuntuforums.org/showthread.php?t=674295]("http://ubuntuforums.org/showthread.php?t=674295"). Error seems to be the same and originating from the same file.

---

### Post by wojox on 2009-12-16
Sure open your terminal Applications > Accessories > Terminal and copy and paste this command and paste the results back up in Code (#) tags:

```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by staf0048 on 2009-12-16
> **Whizpopthat said:**
> I keep getting this error message: 
'E:Type '--2009-12-16' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

Could anyone help me with this problem?

Please, Thanks.

Open the terminal and type 
```
sudo gedit /etc/apt/sources.list.d/medibuntu.list
```
and remove (or uncomment with '#') the line that reads --2009-12-16.  

Save and run

```
sudo apt-get update
```

See if that fixes things.

---

### Post by northern lights on 2009-12-16
> **staf0048 said:**
> Open the terminal and type 
```
sudo gedit /etc/apt/sources.list.d/medibuntu.list
```
and remove (or uncomment with '#') the line that reads --2009-12-16.  

Save and run

```
sudo apt-get update
```

See if that fixes things.

Essentially the solution, unless there's more than one uncommented line that ought to be commented.

2 things.

Of lesser importance: typo. You meant to say "comment with '#'".

Of more importance: if you must run graphical applications as root, please do so with 'gksu' instead of 'sudo'.
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by staf0048 on 2009-12-16
> **northern lights said:**
> if you must run graphical applications as root, please do so with 'gksu' instead of 'sudo'.
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

I did not know that.  Learn something everyday...

---

### Post by Whizpopthat on 2009-12-16
Thanks for all the help. First one seemed to solve the problem so far.

---

