---
title: "/etc/passwd entries"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by A_M_S on 2010-07-05
Hi.

As fas a i known the etc/passwd file stores user account information. But there are also entries linked to some applications that are installed in my system.

root: x :0:0:root:/root:/bin/bash
daemon: x :1:1:daemon:/usr/sbin:/bin/sh
bin: x :2:2:bin:/bin:/bin/sh
sys: x :3:3:sys:/dev:/bin/sh
sync: x :4:65534:sync:/bin:/bin/sync
games: x :5:60:games:/usr/games:/bin/sh
man: x :6:12:man:/var/cache/man:/bin/sh
                .
                .




What are the purpose of those entries?


Tnx.

---

### Post by Crazedpsyc on 2010-07-05
those progs have their own unpriveledged user accounts for doing some things where that is necessary. Don't worry they are completely useless to hackers.

---

### Post by A_M_S on 2010-07-05
Tnx for the reply!

Do you where can i find more detailed information about those accounts?

---

### Post by Crazedpsyc on 2010-07-05
What kind of info?

---

### Post by A_M_S on 2010-07-05
> **Crazedpsyc said:**
> What kind of info?

Technical info about the way these accounts  are used by the applications that create them.

---

### Post by Crazedpsyc on 2010-07-05
Oh,  i'm not sure about that, you can see basic activities of them with the last command, if they have been active. like mine shows me root and "reboot" doing stuff

---

### Post by A_M_S on 2010-07-05
Ok. Tnx for the replies :)

---

### Post by stmiller on 2010-07-05
Yeah - leave those alone and don't touch that file! If it gets corrupted you may be in bad shape. 

Those are sort of the 'system' users and groups. These are there by default from Ubuntu or any Linux distro.

Linux uses users, permissions, and groups to operate. Different system users have set restrictions and such to do task from starting background processes, to doing maintenance jobs and other stuff.

---

