---
title: "new account problem"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by dennisntstar on 2008-12-13
I am a new user of ubuntu.My first account which created during install
works fine.However when i create a new account from 'Add users and groups'
I can login but the screen goes black? can anyone help me?.

---

### Post by nhasian on 2008-12-13
hmm try adding the user from a terminal with the commands.  to add the user enter:

```
sudo useradd -d /home/username -m username
```

then set the password with:

```
sudo passwd username
```

---

### Post by dennisntstar on 2008-12-13
Thanks but it didn't help me. I think it is with configuration.

---

### Post by RealPSL on 2008-12-13
Maybe X is failing for that user. Does that users directory have a .xsession-errors file. By default you should have read access to that users directory so use at the command line ```
cd /home/broken_user_name
``` to get to it or do it in nautilus. Take a look at the file and share it maybe it will help.

---

### Post by dennisntstar on 2008-12-16
I also think the problem with the x-sessio.I am including the file as u said.

---

### Post by RealPSL on 2008-12-18
I think you are right but I am not sure I know how to fix it. I would try renaming the /home/jk/.config directory and try logging into X again. You can rename the directory as that user from the terminal with ```
mv /home/jk/.config /home/jk/.config.bak
```

---

