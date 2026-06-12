---
title: "rm command not working"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by Ghost_Mazal on 2011-03-14
Lo Guys , I'm a bit stuck.

I am trying to delete file recursively down into the tree. But it's not working and I can't figure out why.
The files is a lot of sdat file and in the form of sdatxxxx.exe
The xxxx being a number and each one has a different number.

The command I use is

```
rm -fvR sdat*
```

But it doesn't work ?
Anybody know why or can help please.

---

### Post by ikt on 2011-03-14
> **Ghost_Mazal said:**
> Lo Guys , I'm a bit stuck.

I am trying to delete file recursively down into the tree. But it's not working and I can't figure out why.
The files is a lot of sdat file and in the form of sdatxxxx.exe
The xxxx being a number and each one has a different number.

The command I use is

```
rm -fvR sdat*
```

But it doesn't work ?
Anybody know why or can help please.

what does the command output?

---

### Post by Ghost_Mazal on 2011-03-14
> **ikt said:**
> what does the command output?

It doesn't do anything. Just returns to cursor.

More info :

I am in a folder called backup when running the command.
Inside of it is folders called week1 , week2 , week3 etc.
Inside of those lies all the old backup sdat files that I want
to delete.
I am logged in as root and have permissions.
When I run a find command it works and return all the files.

I don't get why my command is not working.

---

### Post by ikt on 2011-03-14
you will want something like this:

[http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/](http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/)

You will need to find the files first, and then delete them.

edit: replaced with better url.

---

### Post by Ghost_Mazal on 2011-03-14
Yep I'm sure of the case of the filenames.

---

### Post by ikt on 2011-03-14
> **Ghost_Mazal said:**
> Yep I'm sure of the case of the filenames.

Yeah, edited my post sorry

or you can run the command you made inside each of the 3 sub folders.

---

### Post by mcduck on 2011-03-14
> **Ghost_Mazal said:**
> It doesn't do anything. Just returns to cursor.

More info :

I am in a folder called backup when running the command.
Inside of it is folders called week1 , week2 , week3 etc.
Inside of those lies all the old backup sdat files that I want
to delete.
I am logged in as root and have permissions.
When I run a find command it works and return all the files.

I don't get why my command is not working.

find searches recursively from the *subdirectories*, while rm only looks for the file/directory names in the *current* directory (and then removes directories and their contents recursively if you use the -R option). In other words, the recursive option with the rm command doesn't search recursively for things to be deleted, it only deletes recursively.

The current directory doesn't have anything that would match the filename in your command, so it doesn't do anything.

---

### Post by Ghost_Mazal on 2011-03-14
Hmmm. That's a pitty.

Gonna write a little script with this then :

```
find -name 'sdat*' -exec rm -fv {} \;
```

Should work yes ?

---

