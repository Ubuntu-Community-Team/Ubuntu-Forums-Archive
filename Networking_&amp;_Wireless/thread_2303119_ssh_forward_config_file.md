---
title: "ssh forward config file"
date: 2015-11-16
forum: Networking &amp; Wireless
---

### Post by VlaDiSalV on 2015-11-16
Hi, all!
It is so cool feature ssh like ForwardAgent. You can have only one file in your local computer. Very usefull.
So, have ssh feature like this for **config file**? Something like ForwardConfigFile. I would go to several server with one config file.

what's the point of problem:
i have a lot of machine.
```

vladisalv@local:~$ cat .ssh/config | wc -l
    164

```

and often i have situation, when i go to server from server or need copy something from other machine:

```

vladisalv@local:~$ cat .ssh/config
Host machine1
    User user1
    HostName machine1.com
Host machine2
    User very_long_name_username
    HostName idonotwannarememberthis.com
vladisalv@local:~$
vladisalv@local:~$
vladisalv@local:~$ ssh machine1
user1@machine1:~$ scp machine2:./file .
ssh: Could not resolve hostname machine2: Name or service not known
user1@machine1:~$ # i need use complex original name
user1@machine1:~$ scp very_long_name_username@idonotwannarememberthis.com:./file .

```

Usually i copy my update config file to machine, but it's nervous and confuse (specially when you work hard)
So, it would be cool have workflow like this:
```

vladisalv@local:~$ cat .ssh/config
Host machine1
    User user1
    HostName machine1.com
Host machine2
    User very_long_name_username
    HostName idonotwannarememberthis.com
Host new_machine
    User new
    HostName new.com
vladisalv@local:~$
vladisalv@local:~$
vladisalv@local:~$ ssh machine1
user1@machine1:~$ cat .ssh/config @ old config file. no new_machine
Host machine1
    User user1
    HostName machine1.com
Host machine2
    User very_long_name_username
    HostName idonotwannarememberthis.com
user1@machine1:~$ scp machine2:./file .
file                                                                                                                100% 4618     4.5KB/s   00:00
user1@machine1:~$ # i wanna go to new machine
user1@machine1:~$ ssh new_machine
ssh: Could not resolve hostname new_machine: Name or service not known
user1@machine1:~$ # here i need open new terminal and copy update ssh config file from local machine. it interrupt from workflow. i prefer, if my local config file forward with me
user1@machine1:~$ ssh new_machine # as if we have some like ForwardConfigFile
new@new_machine:~$

```

---

### Post by Lars Noodén on 2015-11-16
You might try ansible or something like that to coordinate the configuration file among the machines.

---

