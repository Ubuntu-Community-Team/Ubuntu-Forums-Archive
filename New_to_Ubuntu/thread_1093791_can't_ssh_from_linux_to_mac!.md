---
title: "can't ssh from linux to mac!"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by jmd9qs on 2009-03-11
hi all,

weird problem... i am trying to connect to my friend's mac to scp some files (he is, of course, aware of this)... i know ssh works on that mac cause i ssh'd my comp from his house a few days ago. however, when i attempt to login via:

```
ssh myfriendsusername@hisIPaddress
```

i am presented with the "enter password", and i do so. it says "Permission denied, please try again" 3 times, and then "Permission denied (publickey,password)."

i know i have the correct password! in fact, this exact error is reproducible on my mom's MacBook (i can login FROM but not TO)... any help on this issue?

---

### Post by madverb on 2009-03-11
Are you attempting to logon as the root user?
There may be settings blocking you from logging in from a remote IP rather than a local.

---

### Post by jmd9qs on 2009-03-11
i am not attempting to login as root, no. i have tried ssh with the "sudo" command, and it still doesnt work. if i do have these limitations, how can i take them off? i tried pinging my friends IP and it works, so i know that's right...

---

### Post by madverb on 2009-03-11
I am guessing there is definitely something in the config file that doesn't allow remote login. You need to add your IP or just 0.0.0.0 to the config to allow it.
Not sure with Mac's how the config is done. You may just have to search for it.

---

### Post by jmd9qs on 2009-03-11
that's weird... i had him enable "Remote Login" on his comp and port 22 is open w/ his firewall. i also had him set up port forwarding on his router to port 22 (both TCP and UDP)... i don't know what else to do!

---

### Post by Kareeser on 2009-03-12
You do realize that starting an ssh session FROM the macbook is not the same as starting one TO the macbook, right?

You need your FRIEND'S login credentials.

i.e.
```
ssh [friend's hostname] -l foo
```

---

### Post by jmd9qs on 2009-03-12
> **Kareeser said:**
> You do realize that starting an ssh session FROM the macbook is not the same as starting one TO the macbook, right?

You need your FRIEND'S login credentials.

i.e.
```
ssh [friend's hostname] -l foo
```

i have realized that, yes. i'm not a total noob to ssh... as i stated before, i login with his username and password and THEN it gives me the "(publickey,password)" error. i have no idea what the problem is

---

