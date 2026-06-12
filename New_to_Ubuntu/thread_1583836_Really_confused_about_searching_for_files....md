---
title: "Really confused about searching for files..."
date: 2010-09-28
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-09-28
Hello:

I really am have trouble with this and I don't know why!

I installed Firebird and I know that the example database, 'employee.fdb' is happily living in: /var/lib/firebird/2.1/data/ as I can see it there and work with it.

But, if I search for 'employee.fdb' in 'filesystem', I find nothing!!!!!!!!!

:confused:

Why can't I find files that I search for?

Thanks,

---

### Post by jtarin on 2010-09-28
In the terminal enter the command ```
sudo updatedb
``` it will run for a few moments, when done use the command ```
locate <filename>
``` to find your file.

---

### Post by Robert.Thompson on 2010-09-28
> **jtarin said:**
> In the terminal enter the command ```
sudo updatedb
``` it will run for a few moments, when done use the command ```
locate <filename>
``` to find your file.

It didn't work :confused:

---

### Post by ajgreeny on 2010-09-28
Are you certain you have the letter case correct?  Try```
locate -i <filename>
``` The "-i option is for "-ingnore case".

If that still does not work, and you are absolutely sure the file exists somewhere in the file-system, something must be drastically wrong somewhere, though I don't know quite where it could be.

---

### Post by Robert.Thompson on 2010-09-28
> **ajgreeny said:**
> Are you certain you have the letter case correct?  Try```
locate -i <filename>
``` The "-i option is for "-ingnore case".

If that still does not work, and you are absolutely sure the file exists somewhere in the file-system, something must be drastically wrong somewhere, though I don't know quite where it could be.

I think it has something to do with being SU. Here is my terminal output - I needed to do sudo su to find the file:


rob@rob-laptop:~$ cd /var/lib/firebird/2.1/data/
bash: cd: /var/lib/firebird/2.1/data/: Permission denied
rob@rob-laptop:~$ sudo su
[sudo] password for rob: 
root@rob-laptop:/home/rob# cd /var/lib/firebird/2.1/data/
root@rob-laptop:/var/lib/firebird/2.1/data# ls
employee.fdb  no_empty
root@rob-laptop:/var/lib/firebird/2.1/data# locate employee.fdb
/var/lib/firebird/2.1/data/employee.fdb
root@rob-laptop:/var/lib/firebird/2.1/data# 
root@rob-laptop:/var/lib/firebird/2.1/data# su rob
rob@rob-laptop:/var/lib/firebird/2.1/data$ locate employee.gdb
rob@rob-laptop:/var/lib/firebird/2.1/data$ 


Does this make sense?


I did: su firebird and entered my the password and then was able to locate the file OK.

So, does this mean that Places --> Search for files only finds files owned by the signed in user? Is there a way to find files for all users other than usiing terminal after changing to su?

---

### Post by ajgreeny on 2010-09-28
The ```
locate -i <filename>
``` command should find everything on the computer with the same letter string as <filename>.  So here is an example:-
```
user@ubuntu1004:~$ locate -i bashrc
/etc/bash.bashrc
/etc/bash.bashrc~
/etc/skel/.bashrc
/etc/skel/.bashrc~
/home/user/.bashrc
/home/user/.bashrc~
/usr/share/base-files/dot.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/bash.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bashrc
``` Note that entries include some files owned by root, not just those owned by user, so I am surprised by your situation, and rather baffled.

Are you really using the locate command or the **Places ->Search for files** menu entry?

---

### Post by SeijiSensei on 2010-09-28
> **ajgreeny said:**
> The ```
locate -i <filename>
``` command should find everything on the computer with the same letter string as <filename>. 

No, the locate command obeys file permissions.  If you run it as a local user you'll only see the directories and files to which you have permissions.  

Places like /var/lib/firebird often have only root permissions for security reasons.  Try "sudo ls -ltR /var/lib/firebird"; I bet you'll see the database file then.  

Can you see the database with a command-line or GUI client?  (I don't use firebird but have used both PostgreSQL and MySQL.  Both applications come with a command-line client into which you can type SQL commands.)

---

### Post by jtarin on 2010-09-28
> **SeijiSensei said:**
> No, the locate command obeys file permissions.  If you run it as a local user you'll only see the directories and files to which you have permissions.  

Places like /var/lib/firebird often have only root permissions for security reasons.  Try "sudo ls -ltR /var/lib/firebird"; I bet you'll see the database file then.  

Can you see the database with a command-line or GUI client?  (I don't use firebird but have used both PostgreSQL and MySQL.  Both applications come with a command-line client into which you can type SQL commands.)

Not strictly true. Your run the udatedb command as sudo, so the database includes all files regardless of permission. Access to the database is not restricted to one user, of course if you have users not included in some common groups there is that possibility.

> The locate program may fail to list some files that are present, or may list files that have been removed from the system.  This is because locate only reports files 
that are present in the database, which is typically only regenerated once a week 
by the /etc/periodic/weekly/310.locate script.

Use find(1) to locate files that are of a more transitory nature.

The locate database is typically built by user "nobody" and the locate.updatedb(8) utility skips directories which are not read-able for user "nobody", group "nobody", or world.  For example, if your HOME directory is not world-readable, none of your files are in the database.

---

### Post by SeijiSensei on 2010-09-28
> **jtarin said:**
> Not strictly true. Your run the udatedb command as sudo, so the database includes all files regardless of permission. Access to the database is not restricted to one user, of course if you have users not included in some common groups there is that possibility.

Yes, of course, *updatedb* runs with root permissions, so it can index all the files.  However, the *locate* client runs with the permissions of its user and only displays files that the user has permissions to list.

You wouldn't want it to work any other way for security purposes.  If I have two users on a server, and both of them have /home/user directories with 0700 permissions as is usual, user1 won't be able to see user2's files using locate and vice versa.  Nor will either of them be able to use locate to list files in system areas like /var/lib/postgresql.

Here's an example from Ubuntu Server 10.04: 

```

$locate pg_xlog
nothing is returned

$sudo locate pg_xlog
/var/lib/postgresql/8.4/main/pg_xlog
/var/lib/postgresql/8.4/main/pg_xlog/0000000010000000000000000
/var/lib/postgresql/8.4/main/pg_xlog/archive_status

```

Things like this aren't a matter of opinion or speculation; you can test out whether what I claimed is true empirically on your own machine.

---

### Post by egalvan on 2010-09-28
> **SeijiSensei said:**
> ...*updatedb* runs with root permissions, so it can index all the files.
  However, the *locate* client runs with the permissions of its user and [B]only displays files that the user has permissions to list.
[/B]

Here's an example from Ubuntu Server 10.04: 

```

$locate pg_xlog
nothing is returned

$sudo locate pg_xlog
/var/lib/postgresql/8.4/main/pg_xlog
.....

Things like this aren't a matter of opinion or speculation;
 you can test out whether what I claimed is true empirically **on your own machine.**


Here's an empirical example from my Hardy 8.04.4 machine.
**updatedb** has never been run by user (me).
run from a terminal opened as a simple user (me).

[CODE] locate -i  abi-2.6.24-28-generic
/boot/abi-2.6.24-28-generic

```

Perhaps **Ubuntu Server 10.04 ** is different 
than Ubuntu 8.04 Desktop?

---

### Post by beew on 2010-09-28
Well here is an extremely simple solution that works (no complicated arcane command lines :))

Go to applications > System Tools > Configuration Editor. Then choose from the left panel "apps" and then choose gnome-search tool from the drop down menu.  Then on the right hand panel check the box "disable quick search" and that's it. 

It sounds kind of counter intuitive. I think may be "quick search" requires some indexing and since it hasn't been implemented it returns nothing.

Edited: Oh, forgot to mention, the configuration editor should be installed by default, if you can't find its launcher under applications, go to preference > main menu and find its icon under "system tools" and check the box, it will then appear in the drop down menu.

---

### Post by jtarin on 2010-09-28
> **egalvan said:**
> 
Perhaps **Ubuntu Server 10.04 ** is different 
than Ubuntu 8.04 Desktop?I agree 100% as is every desktop can be configured differently. Dependent on users and priviliges. Before I came to the world of Ubuntu I ran Slackware which is installed as root being default. I consider to be optimal for my personal habits as I can lock-down everything or be selective. I think the discussion of "locate" and permissions is oft times confused with "slocate" (secure locate) where file permisions and access is the norm. In some distributions, locate is actually a symbolic link to slocate. I haven't researched this in a standard Ubuntu install.

---

### Post by SeijiSensei on 2010-09-28
> **egalvan said:**
> ```
locate -i  abi-2.6.24-28-generic
/boot/abi-2.6.24-28-generic
```

That's not a counter-example:

```

ls -l /

[...]
drwxr-xr-x   4 root root  2048 2010-09-16 11:26 boot
[...]

ls -l /boot/abi*
-rw-r--r-- 1 root root 640617 2010-04-16 09:01 /boot/abi-2.6.32-21-generic

```

Everyone has full rights to list and read the abi files in /boot.

> **jtarin said:**
> In some distributions, locate is actually a symbolic link to slocate. I haven't researched this in a standard Ubuntu install.

In Ubuntu, "locate" executes "[mlocate]("http://carolina.mff.cuni.cz/~trmac/blog/mlocate/")" which is "intended to be completely compatible to slocate."  My experience with RedHat/CentOS is identical to my experience with Ubuntu.  All those distributions enforce permissions when using locate.

---

### Post by jtarin on 2010-09-28
> **SeijiSensei said:**
> 
My experience with RedHat/CentOS is identical to my experience with Ubuntu.  All those distributions enforce permissions when using locate.Thankfully my experience hasn't been so restrictive. As a normal child if I was told not to do something I always deferred to my own experience or lack of in those matters and learned first-hand the whys and wherefores as I still do today.

---

### Post by Robert.Thompson on 2010-09-29
It works correctly today.

I was using the terminal yesterday but may I did something wrong - the output I posted was a copy paste from the terminal.

It must have been something else that I did to cause the terminal to work as posted but I have no idea what.

Thank you for your time and patience.

---

### Post by andrew.46 on 2010-09-29
Hi Robert,

> **Robert.Thompson said:**
> I installed Firebird and I know that the example database, 'employee.fdb' is happily living in: /var/lib/firebird/2.1/data/ as I can see it there and work with it.

I see you have solved your problem but I can I suggest for the future that the *find* command is often a better and more flexible tool? For your lost file the following would suffice:

```
sudo find /var -iname 'employee.fdb'
```

Time spent learning to use find is time very well spent IMHO :).

Andrew

---

