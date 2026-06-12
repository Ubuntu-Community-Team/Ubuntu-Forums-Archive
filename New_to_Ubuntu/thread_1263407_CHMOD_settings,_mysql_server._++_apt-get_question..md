---
title: "CHMOD settings, mysql server. ++ apt-get question."
date: 2009-09-10
forum: New to Ubuntu
---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-09-10
Hi, I'm a newb to ubuntu, but I'm getting the hang of it.
I've installed apache (apache2) mysql, php, and mysql-admin.

I'd like to know what setting to chmod /etc/mysql/ to allow me to make changes to my my.cnf file and save a backup, my.cnf.maold 

all this is done automatically by mysql-admin but it needs permissions to write on that directory. How can I check the default settings of the directory, /etc/mysql/ so I remember to set it back to those defaults after changing the settings to writeable.

Also, my partitions are like this;

sda1 = / = 10gb (ubuntu)
sda2 = EXTENDED
sda5 = /home = 120gb (personal data)
sda6 = /share = 15gb (sharing dock for windows/ubuntu)
sda7 = SWAP = 2.5gb

This way I'm hoping that the next release I can install a fresh install, but keep all my settings. I think all the aps, and libarys will be erased, how is it possible to get a copy of all the installed apts that do not come as default? That way I can just run apt-get install *app names* to reinstall all my past aps.

Thanks in advance.:)

---

### Post by GMachine_24 on 2009-09-11
Hey - for the permissions on a file or directory, there are several ways to do it but it is easy to do:

Places>computer>file system> and then on to the director in question - right click on it, go down to "properties" at the bottom, left click on that, and then look for "permissions" tab along the top of the window that opens. Should give you read/write privilege information.

Re: chmod permissions, you can check

```


:~$man chmod | more


```

There are also easier references where you can use numbers to represent what permission you can give root, the group and individual. You will have to search for this but your command ends up something like:

sudo chmod 777 /media/driveA 

which would give universal read/write access to media/driveA

I would do it but it's late and I took pills so zzzzzzzzzzzzzzzz


GM

---

### Post by mcduck on 2009-09-11
> **&#999 said:**
> Hi, I'm a newb to ubuntu, but I'm getting the hang of it.
I've installed apache (apache2) mysql, php, and mysql-admin.

I'd like to know what setting to chmod /etc/mysql/ to allow me to make changes to my my.cnf file and save a backup, my.cnf.maold 

all this is done automatically by mysql-admin but it needs permissions to write on that directory. How can I check the default settings of the directory, /etc/mysql/ so I remember to set it back to those defaults after changing the settings to writeable.

Also, my partitions are like this;

sda1 = / = 10gb (ubuntu)
sda2 = EXTENDED
sda5 = /home = 120gb (personal data)
sda6 = /share = 15gb (sharing dock for windows/ubuntu)
sda7 = SWAP = 2.5gb

This way I'm hoping that the next release I can install a fresh install, but keep all my settings. I think all the aps, and libarys will be erased, how is it possible to get a copy of all the installed apts that do not come as default? That way I can just run apt-get install *app names* to reinstall all my past aps.

Thanks in advance.:)

You don't need to (and shouldn't) change any system files's or directory's permissions or ownership just to edit it. Instead open the file for editing with root permissions by using "sudo".

For example:
```
sudo nano /etc/mysql/my.conf
```
Or, if you prefer using a GUI text editor:
```
gksudo gedit /etc/mysql/my.conf
```

What comes to partitioning, that looks like a sensible setup. All your app settings will be kept through updates since they are located in your home directory. However keeping the actual apps won't be easy, since they aren't located in any single place you could just backup. In the end, keeping them through the updates wouldn't really benefit much anyway, new Ubuntu versions tend to have new versions of all programs so after all the work you'd have to do to keep the apps they would all be updated from repositories anyway.. I'd say the best approach is to just do upgrades to new releases instead of making new fresh installs for every version. Or, if you want to make fresh installs and wish to get all the same apps back easily just keep a list of the packages you install in some text file, then you can use that list to install all the same apps with a single apt-get command..

---

### Post by nikhilbhardwaj on 2009-09-11
> **mcduck said:**
> you don't need to (and shouldn't) change any system files's or directory's permissions or ownership just to edit it. Instead open the file for editing with root permissions by using "sudo".

For example:
```
sudo nano /etc/mysql/my.conf
```
or, if you prefer using a gui text editor:
```
gksudo gedit /etc/mysql/my.conf
```


+1

---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-09-12
Thanks for the replies. I too thought to add all my program apt-get names in a text file, but this thing is i've already downloaded plenty.

Also I know I can sudo gedit.
But then what would the point of the edit feature in mysql-admin be for?
I'll follow the chmod commands, but i'd also like to know the default chmod permissions of a directory. (is it possible to run a command to find the settings?)

Thanks.

---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-09-12
Sorry, a 502 error, proxy page showed up, so i refreshed the page, this post can be deleted.

---

### Post by mcduck on 2009-09-12
> **&#999 said:**
> Thanks for the replies. I too thought to add all my program apt-get names in a text file, but this thing is i've already downloaded plenty.

Also I know I can sudo gedit.
But then what would the point of the edit feature in mysql-admin be for?
I'll follow the chmod commands, but i'd also like to know the default chmod permissions of a directory. (is it possible to run a command to find the settings?)

Thanks.

I suppose you just need to run mysql-admin as some user who has permissions to edit the settings. Can't help you there, really, since I use phpmyadmin myself.

But keep in mind that the "root" user for MySQL is not the same as the root user for your system.

To check permissions files/directories just run "ls -l" to list the files in long format. But like I said, there really should never be any need to change permissions of system files, and if it seems like you'd have to do that to use mysql-admin you must be missing something..

---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-09-20
> **mcduck said:**
> I suppose you just need to run mysql-admin as some user who has permissions to edit the settings. Can't help you there, really, since I use phpmyadmin myself.

But keep in mind that the "root" user for MySQL is not the same as the root user for your system.

To check permissions files/directories just run "ls -l" to list the files in long format. But like I said, there really should never be any need to change permissions of system files, and if it seems like you'd have to do that to use mysql-admin you must be missing something..
Late reply, but phpmyadmin and mysql-admin are completely different.
I use both, mysql-admin is more like server monitoring and settings, while phpmyadmin is more of a mysql database manager.

Thank for the commands though. ;]

---

