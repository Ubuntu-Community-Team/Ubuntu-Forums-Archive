---
title: "Need help using regex with apt-get"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by learningcurb on 2009-06-04
When I try to get all packages ending with 'webkit', I get this error.
```
$ sudo apt-get install *webkit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Regex compilation error - Invalid preceding regular expression

```

However, if I put the * after webkit, like this, the regex works fine.  What am I doing wrong?
```
$ sudo apt-get install webkit* -s
```

---

### Post by Celauran on 2009-06-04
```
$ sudo apt-get install .*webkit
```

---

### Post by learningcurb on 2009-06-04
Aha, that worked, thank you. :)  Why is the .* is required though?

---

### Post by Celauran on 2009-06-04
. matches any character, * matches it any number of times. * alone, then, is meaningless -- match something any number of times, but not mentioning what that something is.

---

### Post by learningcurb on 2009-06-04
Aha, so * always to have a character before it to work.  Thanks again.  The Ubuntu forums are fantastic. :)

---

### Post by learningcurb on 2009-06-05
Hmm, I'm trying to use regexes to manage permissions now.

```
$ ls -la
total 16
drwxr-xr-x 2 root root 4096 2009-06-05 13:03 .
drwxr-xr-x 7 root root 4096 2009-06-04 22:42 ..
-rw-r--r-- 1 root root  220 2009-06-04 22:39 .bash_logout
-rw-r--r-- 1 root root  675 2009-06-04 22:39 .profile

$ sudo chown nobody *.*
chown: cannot access `*.*': No such file or directory
$ sudo chown nobody .*

$ ls -la
total 16
drwxr-xr-x 2 nobody root 4096 2009-06-05 13:03 .
drwxr-xr-x 7 nobody root 4096 2009-06-04 22:42 ..
-rw-r--r-- 1 nobody root  220 2009-06-04 22:39 .bash_logout
-rw-r--r-- 1 nobody root  675 2009-06-04 22:39 .profile

```

It works okay except that I also changed the permissions of the parent folder by mistake.  I guess I'll need to find a way to exclude .. from the regex.

---

