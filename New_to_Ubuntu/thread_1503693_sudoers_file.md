---
title: "sudoers file"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by Drenriza on 2010-06-07
Well i havnt edited the sudoers file before, and aparently it cant quite work when i try to edit it.

_What i want to do._
I want my normal user to be able to do apt-get update/upgrade without giving the root password.

_What i have done_
```
sudo visudo
```
line added to the file
```
%my-normal-group-name ALL=(ALL) NOPASSWD:/usr/bin/apt-get
```

Thanks on advance.
Kind Regards

i tried changing the line a little
```
%cristian ALL=(root) NOPASSWD:/usr/bin/apt-get
```

but still i cant get the right permissions.

---

### Post by sica07 on 2010-06-07
For a specific user:
```
cristian ALL=NOPASSWD: /usr/bin/apt-get
```
For all users:
```
%users ALL=NOPASSWD: /usr/bin/apt-get
```

---

### Post by Drenriza on 2010-06-07
What dont u put % infront of a username.

Is it for groups only?

---

### Post by sica07 on 2010-06-07
Exactly

---

### Post by Drenriza on 2010-06-07
now ive done
```
cristian ALL=NOPASSWD: /usr/bin/apt-get
```

and i still havnt the right permissions.

edited: typo

---

### Post by John Bean on 2010-06-07
> **Drenriza said:**
> now ive done
```
cristian ALL=NOPASSWD:/usr/bin/apt-get
```and i still havnt the right permissions.

You have no space after ALL=NOPASSWD:

See example in post #2.

---

### Post by Drenriza on 2010-06-07
```
cristian@cristian-laptop:~$ apt-get update
E: Kunne ikke åbne låsefilen /var/lib/apt/lists/lock - open (13: Permission denied)
E: Kunne ikke låse listemappen
cristian@cristian-laptop:~$ cat /etc/sudoers
cat: /etc/sudoers: Permission denied
cristian@cristian-laptop:~$ sudo cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

#cristians sektion
cristian ALL=NOPASSWD: /usr/bin/apt-get
```

---

### Post by sica07 on 2010-06-07
I don't know if that is the problem but, try using spaces like this:
```
cristian ALL = NOPASSWD: /usr/bin/apt-get
```
And one more thing. I hope you know that you still have to type:
```
sudo apt-get
```
the only thing is that it will not ask for a password anymore. I'm asking this because I just made the same change in my sudoers file and it works fine.

---

### Post by Drenriza on 2010-06-07
it works with ```
sudo apt-get
```

cant you get it to work without the sudo? thats kinda annoying

---

### Post by sica07 on 2010-06-07
make an alias in .bashrc:
```
alias apt-get='sudo apt-get'
```

---

### Post by Drenriza on 2010-06-07
ye thats an option.

Anyways, thanks for the help guys.

---

