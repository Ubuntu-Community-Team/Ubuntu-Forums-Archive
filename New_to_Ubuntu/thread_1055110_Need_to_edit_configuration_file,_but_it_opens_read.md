---
title: "Need to edit configuration file, but it opens read-only"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by littlegreenman on 2009-01-30
Hello,

If in wrong forum, please apologise.

I've been installing Project Open ([http://www.project-open.org]("http://www.project-open.org")) on my Ubuntu machine, and followed these instructions [https://help.ubuntu.com/community/ProjectOpen]("https://help.ubuntu.com/community/ProjectOpen") .

At some point in the help file the writer mentions that there are some bugs in Project Open running under Ubuntu, and we have to edit some configuration files exclusive to Project Open, but everytime I try to open them they only open Read Only.

I opened the file sudo gedit /location/of/file/file.name

So I think the reason it is opening read only is because it is being used by another service and therefore cannot be modified, but I am not sure what this service might be. I tried shutting down Postgresql, but the file still opens read only.

Also I thought that maybe it might be aolserver that is running, but I am not sure about it. In order to start the Project Open server I run:

```
/usr/sbin/aolserver4-nsd -f -t /web/projop/etc/config.tcl -u projop -g projop
```

And I have CTRL+C that, so that is not working anymore. Wonder if aolserver still running though?

Also, the Live CD does not work on this machine, it gives loads of erros. I could only install Linux on this machine using Wubi.

Sorry for the long post. Any help will be apreciated.

Thanks,
Diogo

---

### Post by jerome1232 on 2009-01-30
Well you can determin if another program has a file open like this

```
lsof /path/to/file
```

to determine if your program is open

```
ps ax | grep aolserver4-nsd
```

to kill an open program

```
killall programname
```

lastly what are the permissions set to on this file (just to make sure the file isn't read only or something)

```
ls -l /path/to/file
```

---

### Post by littlegreenman on 2009-01-30
Thank you jerome.

That helped, but some problems arose:

```
root@ubuntu:~# lsof /web/projop/packages/calendar/www/view-week-display-postgresql.xql
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/littlegreenman/.gvfs
      Output information may be incomplete.
```

and

```
root@ubuntu:~# ps ax | grep aolserver4-nsd
 6463 pts/0    S+     0:00 grep aolserver4-nsd
root@ubuntu:~# killall aolserver4-nsd
aolserver4-nsd: nenhum processo abortado
```


finally,

```
root@ubuntu:~# ls -l /web/projop/packages/calendar/www/view-week-display-postgresql.xql
-r--r--r-- 1 projop projop 2780 2007-09-11 20:10 /web/projop/packages/calendar/www/view-week-display-postgresql.xql
```

I cannot read this -r--r--r-- don't understand the system :-(

Thanks,
Diogo

---

### Post by k3rnelmustard on 2009-01-30
> I cannot read this -r--r--r-- don't understand the system.

This means it is read-only in the filesystem.  The r's mean, in order, read permissions for owner, group, others.  You just need to add write (w) permissions to owner, (and maybe group) should do it.

```

sudo chmod u+w /web/projop/packages/calendar/www/view-week-display-postgresql.xql
sudo chmod g+w /web/projop/packages/calendar/www/view-week-display-postgresql.xql

```

This means, make the owner and group have write permissions, everyone else is read-only.  You'll still need to open the file with sudo.

---

### Post by jerome1232 on 2009-01-30
Okay well what it is saying is this

permissions have 3 flags r = read, w = write, x = execute

you have owner, group, and all other permissions, the first three letters are owner permissions, the second 3 group, and the last there everybodies.

-r--r--r-- projop projop means that the owner has read only permissions, the group has read only permissions, and everybody else has read only permissions.

if you are user projop then you just need to make the file  writeable

```
chmod ug+w /path/to/file
```

then you can edit it as normal
```
gedit /path/to/file
```

if projop is not you then I would chmod it like this

```
sudo -u projop chmod ug+w /path/to/file
```

then to edit it
```
gksu -u projop gedit /path/to/file
```

I hope that helps.

ps
-------------------

From what you output from those command that file wasn't open by any program, your program was still open, and I can't read what the output from killall is but it appears to say the process was aborted to me.

---

### Post by littlegreenman on 2009-01-30
That worked like a charm....

:-)

I used kernelmustard option and the output is this:
```

 ls -l /web/projop/packages/calendar/www/view-week-display-postgresql.xql
-rw-rw-r-- 1 projop projop 2780 2007-09-11 20:10 /web/projop/packages/calendar/www/view-week-display-postgresql.xql
```

so that means owner can read and write, group can read and write, and everybody can read...

cool... :p

I can edit the file using sudo. I guess if i logged in as projop i could as well.

I am not projop, projop is a user for project open.

Thanks a bunch. This thread can be closed.

Diogo

---

### Post by jerome1232 on 2009-01-30
I suggested using sudo to escalate your privileges as projop instead of root just because I think if a task can be done without using root privileges, let's not use root privileges. Just my opinion, glad you got it working.

---

