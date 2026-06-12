---
title: "Is there a way to require authentication for?..."
date: 2010-04-08
forum: New to Ubuntu
---

### Post by Tidus0515 on 2010-04-08
For chmodding. Like....I chmod 000 a file....but it's so easy to chmod it back to 777. Is there a way to require authentication when running the chmod command? Thanks.

---

### Post by -humanaut- on 2010-04-08
I suppose you could try sudo chmod 600

---

### Post by Tidus0515 on 2010-04-08
> **-humanaut- said:**
> I suppose you could try sudo chmod 600
That does not really do anything. I can still simply chmod 777 it back to it's original state.

---

### Post by -humanaut- on 2010-04-08
With a regular user or through sudo?

---

### Post by Paqman on 2010-04-08
> **Tidus0515 said:**
> That does not really do anything. I can still simply chmod 777 it back to it's original state.

You can, because you own the file. Other people can't, unless they use sudo.

---

### Post by Tidus0515 on 2010-04-08
> **-humanaut- said:**
> With a regular user or through sudo?
There is just one user besides root and that is my acct. I create folder "sdf" in my home direectory and sudo chmod 600 sdf. It makes the change...but it is able to revert back by putting chmod 777 sdf without requiring sudo. And I have my timestamp set to 0 so it is not because I have lingering root permissions.

---

### Post by s_ø on 2010-04-08
use **ls -l** to see th owner of the file. As owner you can change permissions.
You could use **chown root:root file_name** to make root owner of the file, but then you would have to use sudo everytime you need to access it.
Better option is to setup another user with limited privileges for everyday use.

---

### Post by Tidus0515 on 2010-04-08
> **s_ø said:**
> use **ls -l** to see th owner of the file. As owner you can change permissions.
You could use **chown root:root file_name** to make root owner of the file, but then you would have to use sudo everytime you need to access it.
Better option is to setup another user with limited privileges for everyday use.

Thank you. This fixed my problem. Now I can do what I wanted to do.

---

