---
title: "ls -d"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by john77eipe on 2010-12-05
Hi

ls -d should be listing all directories (including . and ..) in a folder. But it's not!

```

eipe@eipe-john://usr/lib$ ls -d 
. 

```

---

### Post by squaregoldfish on 2010-12-05
That's not what ls -d does. ls -d prevents listing of directory contents.

For example, if you run 'ls x*', it will list the contents of any directory starting with 'x'. Running 'ls -d x*' will list the directory names only, and not their contents.

Since 'ls' on its own will list the current directory, 'ls -d' lists only the name of the current directory, i.e. '.'

To list only directory names in the current dir, use:

```
ls -d */
```HTH
Steve.

---

### Post by skillet-thief on 2010-12-05
I think that the -d option doesn't quite do what we expect. It doesn't filter the results, but, apparently, shows a directory instead of its contents.

If you type 

```
ls dir
```you get a list of files contained in "dir". But if you type

```
ls -d dir
```you just get:

```
$ dir/
```that is, the directory and not its contents. Try 

```
ls *
```and 

```
ls -d *
```and you'll see why it might be useful sometimes.

If you just want directories, you can try something like:

```
ls -l | grep -e '^d'
```

---

### Post by john77eipe on 2010-12-05
Thank you skillet-thief and squaregoldfish.
So i conclude that -d is for printing directories that we are in.

When used as 
```
ls -d
```
it shows the current directory (directory the ls command has access)

```
ls -d *
```
it shows only the directories (because ls * has access into all the dir within)

I know access is not the right word but couldn't think of a better one! Maybe "eye's"?

skillet-thief@
What does ^d mean?

---

### Post by Rubi1200 on 2010-12-05
Forget what I posted here; was not thinking clearly!
Sorry :-(

---

### Post by john77eipe on 2010-12-06
> **john77eipe said:**
> Thank you skillet-thief and squaregoldfish.
So i conclude that -d is for printing directories that we are in.

When used as 
```
ls -d
```
it shows the current directory (directory the ls command has access)

```
ls -d *
```
it shows only the directories (because ls * has access into all the dir within)

I know access is not the right word but couldn't think of a better one! Maybe "eye's"?


Is my above conclusion correct? Also could someone explain ^d in ```
ls -l | grep -e '^d'
```

---

### Post by matt_symes on 2010-12-06
Hi

The ^ matches just the first character from the line and matches the character to a ***d***. I.E. ^d

It will match 

drwxr-xr-x 19 matthew matthew    4096 2010-12-01 21:22 Music

as the  first character is a d but not the **d**  in launchpad

-rw-r--r--  1 matthew matthew      60 2010-11-02 11:56 Ubuntu_launchpa**d**.txt

This  has section on  regular expressions.

[http://www.robelle.com/smugbook/regexpr.html](http://www.robelle.com/smugbook/regexpr.html)

Kind regards

---

### Post by john77eipe on 2010-12-06
Thanks matt :)

---

