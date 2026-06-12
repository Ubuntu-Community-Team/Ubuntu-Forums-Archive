---
title: "rm -f and permissions"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by new__buntu on 2010-07-14
Hi, 

I'm new to ubuntu, and I've come to love the fact that I can control the permissions granted to other users (I'm the only one who uses the computer but it makes me feel powerful :)). Anyways, my question is basically this - does the -f option of the rm command bypass permissions? I've done some tests and it seems like it does.

EDIT: after further testing it looks like rm bypasses permissions in general.

---

### Post by nothingspecial on 2010-07-14
It`s the sudo that does that, not the -f

unless you are root

---

### Post by da burger on 2010-07-14
You can delete any file in a directory where you have write permissions, even if you don't have write permissions to the file itself.

In fact it's write permissions on the directory that allows you to delete a file. Make a test dir, make it belong to root with 755 perms, now create a file in it, make it belong to you with 700 permissions. Even though the file is yours you won't be able to delete it.

---

### Post by new__buntu on 2010-07-14
But I didn't append sudo to my remove statements. Here's exactly what I did in my test:

$gedit newFile
$sudo chown root newFile
$sudo chmod 700 newFile
$rm newFile
rm: remove write-protected regular empty file 'newFile'? y

and voila it's gone

EDIT: da burger, you're too fast. And completely right. Thanks.

---

### Post by nothingspecial on 2010-07-14
I was guessing, the answer is above ;)

---

### Post by Penguin Guy on 2010-07-14
[FONT="Courier New"]-f[/FONT] simply suppresses error messages:
```

       -f, --force
              ignore nonexistent files, never prompt


```

---

### Post by sisco311 on 2010-07-14
> **da burger said:**
> You can delete any file in a directory where you have write permissions, even if you don't have write permissions to the file itself.

In fact it's write permissions on the directory that allows you to delete a file. Make a test dir, make it belong to root with 755 perms, now create a file in it, make it belong to you with 700 permissions. Even though the file is yours you won't be able to delete it.

Almost right. :)

You also need execute access to all parent directories back to the root.

[http://www.dartmouth.edu/~rc/help/faq/permissions.html](http://www.dartmouth.edu/~rc/help/faq/permissions.html)

---

### Post by da burger on 2010-07-14
> **sisco311 said:**
> Almost right. :)

You also need execute access to all parent directories back to the root.

[http://www.dartmouth.edu/~rc/help/faq/permissions.html](http://www.dartmouth.edu/~rc/help/faq/permissions.html)

Drat, so close. My answer said what was needed at least.

---

