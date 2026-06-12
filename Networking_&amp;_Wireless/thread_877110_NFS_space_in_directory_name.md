---
title: "NFS space in directory name"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by 47_MasoN_47 on 2008-08-01
I have the same problem listed in [this thread]("http://ubuntuforums.org/showthread.php?t=435548").  Here is what I tried and the results of it.

/etc/exports
```
/home/<username>/Desktop/"Users Shared Folders"/<AnotherUserName> ###.###.###.### (rw,sync,no_subtree_check)
```

```
<username>@<servername>:~$ sudo exportfs -ra
exportfs: Warning: /home/<username>/Desktop/Users Shared Folders/<AnotherUserName> does not support NFS export.
```

How can I go about fixing this?

Oh, I'd rather not rename the "Users Shared Folders" directory because I'd have to re-setup all the Samba shares that the other users use, which isn't a huge deal but an annoyance.

---

### Post by Growbag on 2008-08-01
Put the quotes at the beginning and end of the path:

```
"/home/<username>/Desktop/Users Shared Folders/<AnotherUserName>"

```
or use the backslash:

```
/home/<username>/Desktop/Users\ Shared\ Folders/<AnotherUserName>
```

That should do it!

---

### Post by 47_MasoN_47 on 2008-08-01
I tried the Users\ Shared\ Folders trick and that didn't work.  Quotes around the whole thing didn't work either...

Thanks for the replies though.

---

### Post by Growbag on 2008-08-01
OK, make a link to that folder but give it a Linux friendly name (without spaces) and use that instead :)

You can do that easily with Nautilus (right click on the folder -> make link) or from the terminal.

Maybe they should have been single quotes now that I think about it?  

lol

But the link trick should work ;)

---

### Post by 47_MasoN_47 on 2008-08-01
Tried the link thing too, someone had mentioned that in another thread and it doesn't work.  Apparently NFS follows to where the link is and tries to export that folder instead of the link.

---

### Post by Growbag on 2008-08-01
Oh well, I tried :(.

Good luck!

---

### Post by Growbag on 2008-08-02
OK, last resort, try this:

Use %20 instead of the space, like so:

```
/home/<username>/Desktop/Users%20Shared%20Folders/<AnotherUserName>
```

I hope that works :).

---

### Post by dmizer on 2008-08-02
If that doesn't work, try this:
```
/home/<username>/Desktop/Users\040Shared\040Folders/<AnotherUserName>
```

---

### Post by mosaic2s on 2011-04-15
created link - that worked. all other methods failed.

link takes a little time to get activated - else working fine. allows me to use thunderbird in both OS.

---

