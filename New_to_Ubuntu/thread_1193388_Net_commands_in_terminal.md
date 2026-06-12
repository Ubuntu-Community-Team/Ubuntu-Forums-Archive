---
title: "Net commands in terminal"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by prvteprts on 2009-06-21
I would like to know how to view the machines in my local workgroup. In Windows, I used to use the command 'net view'. What could be the counterpart of that in Linux? I am aware there is a "net" command in Ubuntu, but I just don't know how to use it in the way I want even after reading the man page. Also, I noticed there is no net command in Puppy.

Also, could anyone suggest some other useful commands related to this? Like aside from viewing the names of the workgroup machines, could you also view their IP's as well? Thanks.

---

### Post by nhasian on 2009-06-21
did you install samba?  after you've installed it you should be able to use the net command like in windows.

```
sudo apt-get install samba
```

---

### Post by Toshubu on 2009-06-21
Look into the "arp" and "netstat" commands, and their options.

---

### Post by cariboo on 2009-06-21
The **net** command also work in Ubuntu, open a terminal and type:

```
net
```

the above command will show you a list of options for the net command.

---

### Post by llamakc on 2009-06-21
```

smbtree

```

---

### Post by prvteprts on 2009-06-22
Thanks. Silly me, I already new about arp. Samba was already installed previously, it's just that I've been focusing too much on the net command. The smbtree command works great too.

---

