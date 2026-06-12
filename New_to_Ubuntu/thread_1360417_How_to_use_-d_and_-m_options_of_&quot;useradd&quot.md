---
title: "How to use -d and -m options of &quot;useradd&quot; command?"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by khuyencncn on 2009-12-20
Hello, I see this in manual of "useradd" command:

> **useradd** [**-c** *comment*] [**-d** *home_dir*]

**d** *home_dir*The new user will be created using *home_dir* as the value for the user's login directory. The default is to append the *login* name to *default_home* and use that as the login directory name.
**-m**The user's home directory will be created if it does not exist. The files contained in *skeleton_dir* will be copied to the home directory if the **-k** option is used, otherwise the files contained in */etc/skel* will be used instead. Any directories contained in *skeleton_dir* or */etc/skel* will be created in the user's home directory as well. The **-k** option is only valid in conjunction with the **-m** option. The default is to not create the directory and to not copy any files.
I'm new in Linux, so I don't know about other benifits of **-m** option, just focus on "user's home directory" part.

When I use "**useradd -m tester**", the user "tester" is added and his directory "tester" is also created.

> drwxr-xr-x  2 tester     tester     4096 2009-12-21 09:49 testerBut when I use "**useradd -d /home/tester tester**", only "tester" user is added, there is no tester's home directory in /home.

I try to create /home/tester first and then run the command but the owner of ./tester is still root.

All commands above I run without error.

So what's difference between -d and -m options and how to use them?

Thanks!

---

### Post by orlox on 2009-12-20
As far as I know, users have /home/username as a default directory. Putting the GUI aside, what this home directory means is that when you open a terminal with that user, you will start at that folder.

Now, -m creates the directory if it doesn't exist. So, if you use:

```

useradd -m test

```

The -m flag will ensure that /home/test (the default home directory) will be created with the appropiate permissions and ownership.

Now, what happens when you use -d, is that you change this default directory, so for instance, if you want a non-default location, and you want adduser to also create the directory, you would do:

```

useradd -d /strangehome/test -m test

```

So with -d, you change the default home, and -m makes sure that it's created if it doesn't exist.

---

### Post by khuyencncn on 2009-12-20
Understood!

Thank you!

---

### Post by orlox on 2009-12-20
Your welcome!

Remember to mark  your threads as solved when it corresponds. I believe the option appears under "thread tools".

---

### Post by khuyencncn on 2009-12-21
Thanks! Thanks!

---

