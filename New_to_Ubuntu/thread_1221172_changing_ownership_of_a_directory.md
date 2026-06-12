---
title: "changing ownership of a directory"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by inanutshellus on 2009-07-23
I'm logged in as "bob". I'm a member of groups "a" and "b". I have the following directory:
```

drwxr-xr-x  8 a         a         4096 Jul 23 14:40 .
drwxr-xr-x  8 a         a         4096 May 14 18:31 ..
drwxr-xr-x  3 a         a         4096 Dec 24  2007 some_directory

```

I want to change "some_directory" (ownership a:a) to be owned/grouped as "b:b". I can sudo as "a" and I can sudo as "b" (but can't sudo as root). 

chown/chgrp is failing me:

```

$ sudo -u a chgrp b some_directory
/bin/chgrp: changing group of `some_directory': Operation not permitted
$ sudo -u b chgrp b some_directory
/bin/chgrp: changing group of `some_directory': Operation not permitted

```

I tried copying the directory to /tmp (the copy was then owned by me instead of "a") then changing the copy to be owned by b:b and that worked, so then I copied (with -p to preserve ownership) it back to the original folder .... and it changed ownership back to "a".

Surely I'm just missing something. I mean, I understand why it's failing (As user "a" I'm not allowed to give "b" my file because I'm not "b". As user "b" I'm not allowed to copy the directory because its parent is owned by "a"), but it seems like this should be doable.

---

### Post by lykwydchykyn on 2009-07-23
You don't have write access to the folder, according to what you've put here.  The folder is owned by user "a" and writeable only by the user.  You are in a group called "a" but that group doesn't have write access to the folder.

The thing confusing you seems to be that there is a user "a" and a group "a".  These share nothing but a name, there is no actual relationship in terms of privilege between group "a" and user "a".

Even if you did have write access to the folder, you can't actually change ownership unless you own the folder (or are root), AFAIK.

---

### Post by Bodsda on 2009-07-23
> **inanutshellus said:**
> I'm logged in as "bob". I'm a member of groups "a" and "b". I have the following directory:
```

drwxr-xr-x  8 a         a         4096 Jul 23 14:40 .
drwxr-xr-x  8 a         a         4096 May 14 18:31 ..
drwxr-xr-x  3 a         a         4096 Dec 24  2007 some_directory

```

I want to change "some_directory" (ownership a:a) to be owned/grouped as "b:b". I can sudo as "a" and I can sudo as "b" (but can't sudo as root). 

chown/chgrp is failing me:

```

$ sudo -u a chgrp b some_directory
/bin/chgrp: changing group of `some_directory': Operation not permitted
$ sudo -u b chgrp b some_directory
/bin/chgrp: changing group of `some_directory': Operation not permitted

```

I tried copying the directory to /tmp (the copy was then owned by me instead of "a") then changing the copy to be owned by b:b and that worked, so then I copied (with -p to preserve ownership) it back to the original folder .... and it changed ownership back to "a".

Surely I'm just missing something. I mean, I understand why it's failing (As user "a" I'm not allowed to give "b" my file because I'm not "b". As user "b" I'm not allowed to copy the directory because its parent is owned by "a"), but it seems like this should be doable.

I'm not too sharp on groups, but I think a chown should be able to do it (im not on ubuntu so this is a best guess)
```

sudo chown -R a:a some_directory

```

Regards,

Bodsda

EDIT: Probably best to listen to the guy above me

---

### Post by mcduck on 2009-07-23
> **Bodsda said:**
> I'm not too sharp on groups, but I think a chown should be able to do it (im not on ubuntu so this is a best guess)
```

sudo chown -R a:a some_directory

```

Regards,

Bodsda

EDIT: Probably best to listen to the guy above me

Actually this will work just fine (since it's ran with "sudo", so who owns the directory now and what permissions it has is meaningless).

Still, only add the -R option if you want to chown recursively (which might or might not be the case since the OP didn't ask for it.)

---

### Post by inanutshellus on 2009-07-23
> **mcduck said:**
> Actually this will work just fine (since it's ran with "sudo", so who owns the directory now and what permissions it has is meaningless).

Still, only add the -R option if you want to chown recursively (which might or might not be the case since the OP didn't ask for it.)

That would be the case if I could run sudo as root, as in his command. Instead I have to specify "sudo -u a" or "sudo -u b", which... basically means it's not possible. =/

---

### Post by mcduck on 2009-07-23
> **inanutshellus said:**
> That would be the case if I could run sudo as root, as in his command. Instead I have to specify "sudo -u a" or "sudo -u b", which... basically means it's not possible. =/

use the command I was talking about, the one I quoted in my post.

```
sudo chown a:a some_directory
```

You don't need to be user "a" or in group "a" to do that, root is able to change any file's ownership to any user. :)

---

