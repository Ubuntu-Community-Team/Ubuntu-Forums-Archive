---
title: "ls -l"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by lanceps on 2009-02-25
hi there i am just starting to use ubuntu/ linux 

my friend told me this command and when i type it i see the name of my directory the person who made it and stuff. with that i also see some numbers

right after where they write the drwx--x--x stuff pls tell me what those numbers mean

---

### Post by binbash on 2009-02-25
r read w write x execute etc.They are permissons.

---

### Post by .Maleficus. on 2009-02-25
Those are the permissions of the folder/file.  

In the first position you have a d - The 'd' means directory.  If it was an 'l' it would be a link, and a '-' is a file.  There are more but they aren't important for you.

The 2-4 permissions show the owner's permissions - yours.  You have 'rwx', meaning 'read, write, execute'.  You can do anything to that folder.

5 - 7 show the group permissions -  they are only allowed to execute.

8 - 10 show all other users permissions for the file, and they too are only allowed to execute.

Read more here.  [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

---

### Post by Joeb454 on 2009-02-25
I think the numbers directly after the permissions correspond to the number of files in the directory :)

If the item in question is a file, it should read 1. Directories will always have 2 ( . and  .. )

---

### Post by WakkiTabakki on 2009-02-25
For a lengthier  description, check:
[http://en.wikipedia.org/wiki/Unix_permissions](http://en.wikipedia.org/wiki/Unix_permissions)
[http://www.hackinglinuxexposed.com/articles/20030417.html](http://www.hackinglinuxexposed.com/articles/20030417.html)
[http://dsl.org/cookbook/cookbook_9.html](http://dsl.org/cookbook/cookbook_9.html)

/N

---

### Post by lanceps on 2009-02-25
> **Joeb454 said:**
> I think the numbers directly after the permissions correspond to the number of files in the directory :)

If the item in question is a file, it should read 1. Directories will always have 2 ( . and  .. )

in some places i have seem 7 8 9 124 etc

---

### Post by sisco311 on 2009-02-25
> **Joeb454 said:**
> I think the numbers directly after the permissions correspond to the number of files in the directory :)

If the item in question is a file, it should read 1. Directories will always have 2 ( . and  .. )

nope. it's the number of hard links.

---

### Post by geirha on 2009-02-25
> **lanceps said:**
> in some places i have seem 7 8 9 124 etc

He meant at least 2. Since the special . and .. will always take up 2 entries.

If the number is 7, then that means the directory has 5 directories directly underneath it. The . + the .. + 5 directories == 7.

---

### Post by Joeb454 on 2009-02-25
> **sisco311 said:**
> nope. it's the number of hard links.

Isn't that essentially what files are? :)

---

### Post by sisco311 on 2009-02-25
. is a hard link to the current directory and
.. is a hard link to the parent dir

/dir
/dir/d1
/dir/d2

d1 -> 2 hard links: /dir/d1 and /dir/d1/.
d2 -||-
dir -> 4: /dir, /dir/. , /dir/d1/.. and /dir/d2/..


```

touch file
ln -i file file2
ls -l
```;)

---

### Post by Lunx on 2009-02-25
> **lanceps said:**
> hi there i am just starting to use ubuntu/ linux 

my friend told me this command and when i type it i see the name of my directory the person who made it and stuff. with that i also see some numbers

right after where they write the drwx--x--x stuff pls tell me what those numbers mean


Have you had a look at the [[COLOR="Purple"]Pocket User Guide[/COLOR]]("http://www.ubuntupocketguide.com/")? It's a great resource for newcomers to Ubuntu (and Linux)

Chapter 5 Hands-on at the Comand-line gives a very good description of exactly the info you're after. I'm very new to all this myself and have found this guide to be the best resource I've found so far in terms of being easy to understand.

---

### Post by geirha on 2009-02-25
> **Joeb454 said:**
> Isn't that essentially what files are? :)

On ext2/3 filesystems, files does not have a name, only a number (inode). You create a hardlink to it to give it a name and a place in the directory structure. If you want to make a new hardlink to a file that already has a hardlink, you can use the ln command
```

$ touch a          # Creates a file with one hardlink
$ ls -i a          # Shows the inode of the file
279528 a
$ ln a b           # Creates a new hardlink to the file
$ cp a c           # Creates a new file with a hardlink with the same content as the file a.
$ ln -i a b c
279528 a  279528 b  279529 c
$ echo hello >> a  # Write some text to the file
$ cat b            # Since a and b is the same file, viewing either will show the same content
hello
$ cat c            # c is a copy of the old a, so it's still empty
$ ls -l a b c
-rw-r--r-- 2 geirha geirha 6 2009-02-25 13:18 a
-rw-r--r-- 2 geirha geirha 6 2009-02-25 13:18 b
-rw-r--r-- 1 geirha geirha 0 2009-02-25 13:18 c

```

---

