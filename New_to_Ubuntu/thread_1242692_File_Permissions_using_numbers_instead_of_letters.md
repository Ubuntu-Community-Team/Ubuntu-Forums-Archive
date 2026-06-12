---
title: "File Permissions using numbers instead of letters"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by chris1950 on 2009-08-17
I've seen in other threads people using numbers when using chmod. Can someone tell me where I can find a table/chart explaing what each number is or means?

---

### Post by jrothwell97 on 2009-08-17
chmod uses octal numbers. Open a terminal and run

```
man chmod
```

for an explanation. Once you're done, press Q to return to the terminal.

---

### Post by BDNiner on 2009-08-17
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

contains a great tutorial on both ways of settings permissions

---

### Post by oldos2er on 2009-08-17
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by CaptainMark on 2009-08-17
The short answer is 
Start with zero
+4 to make a file readable
+2 to make a file writeable 
+1 to make a file executable

Do this once for the owner once for the group and once for everyone else, that way any number between 1 and 7 represents a different combination of permissions eg. 777 can be read written to and executed by anyone, whereas 000 basically cant be seen changed or run by anyone, so really doesnt exist.

---

### Post by bostonaholic on 2009-08-17
If you 'ls -l' in a directory, for each file you'll see something like:

```
-rw-r--r-- 1 user group 17964 2009-08-06 08:59 pom.xml
```

The first portion is the permission levels of the file.  There are 10 dashes.  Dash #1 will have a 'd' if it's a directory and '-' if it's a file.

For the next 9 dashes, it helps if you understand the concepts of binary.

Think of it like this:

```
chmod XYZ
```

XYZ is compromised of 3 numbers.

X will set the permissions for the **owner** (first 3 dashes after the initial 1 for 'd').
Y will set the permissions for the **group** (second 3 dashes).
Z will set the permissions for **all users** (last 3 dashes.

Each set of 3 dashes is then broken down into rwx (Read, Write, Execute).  If a file has read access, you'll see a 'r' in the first position of the tuplet.  For write access you'll see a 'w' in the second position of the tuplet, and so on.  Here's where the binary comes in.  Think of the tuplet as a tuplet of binary 0 - 7.

```
000 = 0
001 = 1
010 = 2
...
```

Now you would link up the 'rwx' tuplet with a tuplet of binary like this:

101 = r-x --> Read and Execute.  Since 101 is '5' in decimal, you would use a '5' to represent permission levels of Read and Execute (no ability to Write).

So then you take this '5' and apply it to the tuplet of chmod XYZ to which users' accessibility of the file/directory.

So if you would like to give the owner Read, Write and Execute permissions, but the Group and everyone else only Read and Execute permissions you would do something like:

```
chmod 755 <filename>
```

Since 7 in binary is 111 --> rwx
and 5 in binary is 101 --> r-x

I hope this helps.

---

### Post by egalvan on 2009-08-17
You can also change Nautilus Column View to include Octal Permissions,
this can help visualizing.

---

### Post by chris1950 on 2009-08-17
OK that answered my question. Thanks a lot, I bookmarked the pages so I can read them later in depth, only glanced now.

---

### Post by CaptainMark on 2009-08-18
is there a command like ls -lah but will list the permissions in 777 format instead of rwxrwxrwx, i find 777 much easier to veiw at a glance?

---

### Post by bostonaholic on 2009-08-18
> **CaptainMark said:**
> is there a command like ls -lah but will list the permissions in 777 format instead of rwxrwxrwx, i find 777 much easier to veiw at a glance?

I don't believe there is such a command.  That would be useful though...  If you're good, you could modify your own 'ls' command to do so.

---

