---
title: "Managing users in ubuntu 10.04"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by karthick87 on 2010-10-25
I have multiple users in my ubuntu..Everyone has thier own home directory,how can i lock them in their home directory..?So that they cant view others home directory..

---

### Post by NertSkull on 2010-10-25
from my understanding, when you create the new user it should automatically set permissions for their home directory to read and write only for them (at least write).

you can always change permissions using the chmod and chown commands.  

i.e. you could chmod -r 700 the /home/user directory so that only the owner of the directory can use it.

also chgrp is useful, you can assign groups so the certain groups can see certain folders.

there's lots of info on directory permissions on the forums, its one of my favorite parts of linux

---

### Post by karthick87 on 2010-10-25
karthick@Ubuntu-desktop:~$ sudo chmod -R  700 /home/karthick
chmod: cannot access `/home/karthick/.gvfs': Permission denied
chmod: changing permissions of `/home/karthick/.recently-used.xbel': Operation not permitted

---

### Post by ubudog on 2010-10-25
> **NertSkull said:**
> from my understanding, when you create the new user it should automatically set permissions for their home directory to read and write only for them (at least write).

you can always change permissions using the chmod and chown commands.  

i.e. you could chmod -r 700 the /home/user directory so that only the owner of the directory can use it.

also chgrp is useful, you can assign groups so the certain groups can see certain folders.

there's lots of info on directory permissions on the forums, its one of my favorite parts of linux

Thanks for this....useful.

---

### Post by Rubi1200 on 2010-10-25
> **getyourkarthick said:**
> karthick@Ubuntu-desktop:~$ sudo chmod -R  700 /home/karthick
chmod: cannot access `/home/karthick/.gvfs': Permission denied
chmod: changing permissions of `/home/karthick/.recently-used.xbel': Operation not permitted
Post the output of ```
ls -l
```please.

---

### Post by karthick87 on 2010-10-25
```
karthick@Ubuntu-desktop:~$ ls -l
total 64
drwx------ 18 karthick karthick  4096 2010-10-26 12:03 Desktop
drwx------  5 karthick karthick  4096 2010-09-27 22:44 Documents
drwx------  7 karthick karthick  4096 2010-10-19 23:48 Downloads
drwx------ 22 karthick karthick  4096 2010-10-19 23:44 DUMPS
drwx------  2 karthick karthick  4096 2010-10-19 23:46 Forum Ranking
drwx------ 64 karthick karthick 12288 2010-10-25 10:02 Guides
drwx------ 16 karthick karthick 12288 2010-10-02 07:14 Music
drwx------  5 karthick karthick  4096 2010-10-19 23:48 Pictures
drwx------  5 karthick karthick  4096 2010-06-06 12:00 Programming
drwx------  3 karthick karthick  4096 2010-10-26 12:05 Public
drwx------  2 karthick karthick  4096 2010-05-26 10:33 Templates
drwx------  2 karthick karthick  4096 2010-05-19 19:10 Videos

```

---

### Post by Rubi1200 on 2010-10-25
The output means that the chmod -R  700 command you ran worked.

[COLOR=Red]drwx[/COLOR]:

to break it down:
d = directory
rwx = you, and only you, have read, write, and execute privileges.
No other user can read or access these directories.
Try it as another user and you will see what I mean.
The warnings are nothing to be concerned about (as far as I am aware).

All files that were in the directories at the time also had their permissions changed recursively.

But, any new file you add will not have 700 permissions.

However, because the directory has 700 permissions, no other user will be able to access the files.

I hope this helps explain things for you.

---

### Post by sisco311 on 2010-10-25
~/.gvfs is a virtual filesystem, so you can ignore the *Permission denied* error. 


> **Rubi1200 said:**
> 
All files that were in the directories at the time also had their permissions changed recursively.


Making all files executable is not only a security risk, but may cause other problems too, e.g. see: [thread=976610]Solving .dmrc and $HOME Permission Errors[/thread].

I would change the permissions back to the default ones:
```
find ~ -type d -exec chmod 0755 '{}' +;
find ~ -type f -exec chmod 0644 '{}' +;
```

then change only the permissions of the home directory:
```
chmod 0700 ~
```

For more info about Unix/Linux file and directory permissions check out:
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by NertSkull on 2010-10-25
> **getyourkarthick said:**
> karthick@Ubuntu-desktop:~$ sudo chmod -R  700 /home/karthick
chmod: cannot access `/home/karthick/.gvfs': Permission denied
chmod: changing permissions of `/home/karthick/.recently-used.xbel': Operation not permitted

So it changed permissions on everything but that .gvfs and .recently-used.xbel files.

The .gvfs file has something to do with fuse and mount point for certain system files.

Basically .gvfs doesn't actually store anything if you aren't logged in.  So not changing permissions on it probably isn't a big deal for your set up.

I assume the xbel file is something similar (but don't know for sure).

As you can see from you ls -l output (try ls -la as well) that all your files are now dwrx------  

The d (or -) in the first means its a directory of file.

The next 3 are the owner setup (wrx) and the next three (---) are the group and the last three (---) are world.  Group and world have no access now.

So you should be good to go.




whoops, sisco beat me to it, with better information

---

### Post by Rubi1200 on 2010-10-25
> **sisco311 said:**
> ~/.gvfs is a virtual filesystem, so you can ignore the *Permission denied* error. 




Making all files executable is not only a security risk, but may cause other problems too, e.g. see: [thread=976610]Solving .dmrc and $HOME Permission Errors[/thread].

I would change the permissions back to the default ones:
```
find ~ -type d -exec chmod 0755 '{}' +;
find ~ -type f -exec chmod 0644 '{}' +;
```then change only the permissions of the home directory:
```
chmod 0700 ~
```For more info about Unix/Linux file and directory permissions check out:
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

@sisco311: I understand the security concern you are talking about by making ALL files executable in the home directory.

But, I have 1 problem and 2 questions.

Problem1: I just tried on a test version of Ubuntu to change permissions with and without the -R switch. It does not work without using the -R switch!?! In other words, I ran these commands:
chmod 700 ~ (had no effect)
chmod -R 700 ~ (changes permissions as seen above)
chmod 755 ~ (attempt to change permissions back again has no effect)
chmod -R 755 ~ (worked)

Q1: how is this possible?

Q2: how can permissions be changed to make the home directory 700 without recursively changing permissions for files within the directory?

I would appreciate any input you have about this matter because it is of some concern to me (and most likely other users).

---

### Post by karthick87 on 2010-10-26
Thank you and how to give internet access to a particular user?

---

### Post by NertSkull on 2010-10-26
I'm not sure on this, cause I've never done it.  

But I seem to remember (at least when using a static IP and the interfaces file) that you can set a group for internet users.  Then assign who you want to that group.

Then go and make the permissions correct (including proper group permissions and deny others) to the /etc/network/interfaces file.

Again I'm not positive thats the best way or if it will even work, but might be worth a try. 

Also, I think in the user management box (found in system>administration>users & groups) you may be able to define who can or cannot use the network there as well.

---

### Post by Rubi1200 on 2010-10-26
@sisco311:

Further testing has revealed something interesting. The ```
chmod 700 ~
``` command does work, but it does not show when running the```
 ls -l 
```command. In other words, whether I use 700 or 755 permissions, the ls command still shows the following for the home directory: > drwxr-xr-x 2 If I log out and then back in as another user, the second user cannot access my home directory when the permissions are set to 700 (as one would expect).

Is this deliberate, a bug in the ls command, or something else?

I would appreciate any input about this.

Thanks in advance.

---

### Post by karthick87 on 2010-10-26
Actually wat i want to do is i want to control rest of the users,like an administrator,and all those user accounts should act like limited accounts like in windows.Such that they cant make any changes to system..

---

### Post by linux-hack on 2010-10-26
Normal users can't make changes to the system if they don't have sudo rights or the root password. they can change only there files and nothing more. so don't worry about that.

---

### Post by karthick87 on 2010-10-26
> **linux-hack said:**
> Normal users can't make changes to the system if they don't have sudo rights or the root password. they can change only there files and nothing more. so don't worry about that.

But i want to give internet access to normal users,how to do it?

---

### Post by CharlesA on 2010-10-26
Note: Doing a recursive (chmod -R) 700 on a user's home directory is a bad idea. You'd only need to do it on the directory in /home.

As for the internet access thing: Are you using network manager? I believe there is a setting there to allow all users to use a connection.

---

### Post by Paddy Landau on 2010-10-26
> **getyourkarthick said:**
> But i want to give internet access to normal users,how to do it?
System > Administration > Users and Groups > *[the user]* > Advanced Settings > User Privileges.

Tick "Connect to the Internet using a modem" and "Connect to wireless and Ethernet networks". Actually, if you trust your users, you can tick everything there except "Administer the system".

---

### Post by Paddy Landau on 2010-10-26
> **CharlesA said:**
> As for the internet access thing: Are you using network manager? I believe there is a setting there to allow all users to use a connection.
Quite right!

System > Preferences > Network Connections.

[LIST=1]
[*]If you have Ethernet: Wired > [click the connection] > Edit > tick Available to all users > Apply.
[*]If you have wireless: Wireless > [click the connection] > Edit > tick Available to all users > Apply.
[/LIST]

---

### Post by ubudog on 2010-10-26
> **CharlesA said:**
> As for the internet access thing: Are you using network manager? I believe there is a setting there to allow all users to use a connection.

Yeah there is, and that works for me.

---

### Post by uRock on 2010-10-26
This,

---

### Post by karthick87 on 2010-10-26
Am not using network manager..I use the command "sudo pon dsl-provider" to connect to internet.

---

### Post by sisco311 on 2010-10-26
> **getyourkarthick said:**
> Am not using network manager..I use the command "sudo pon dsl-provider" to connect to internet.

You have to add the user to the "dip" and "dialout" groups:
```
sudo gpasswd -a **username** dip
sudo gpasswd -a **username** dialout
```

[uhelp]community/DialupModemHowto/SetUpDialer[/uhelp]

---

### Post by amac777 on 2010-10-26
> **Rubi1200 said:**
> Is this deliberate, a bug in the ls command, or something else?

I would appreciate any input about this.

Thanks in advance.

Instead of looking at the permissions of the files in your own home directory, try looking at the permissions of the home directories like this:

```
ls -l /home
```

---

### Post by karthick87 on 2010-10-26
```
karthick@Ubuntu-desktop:~$ ls -l /home
total 8
drwx------ 64 karthick karthick 4096 2010-10-27 11:50 karthick
drwxrwxrwx 30 vivek    vivek    4096 2010-10-27 11:45 vivek

```

---

### Post by CharlesA on 2010-10-26
Is there a reason vivek is set to 777?

Normally a home directory is set to 755.

---

### Post by Rubi1200 on 2010-10-26
> **amac777 said:**
> Instead of looking at the permissions of the files in your own home directory, try looking at the permissions of the home directories like this:

```
ls -l /home
```
Thank you amac777, I appreciate the feedback :)

See here for sisco311's answer too:
[http://ubuntuforums.org/showthread.php?t=1606245](http://ubuntuforums.org/showthread.php?t=1606245)

(and if you have an answer to the question in the link in my last post that, too, would be excellent!)

---

### Post by karthick87 on 2010-10-26
> **CharlesA said:**
> Is there a reason vivek is set to 777?

Normally a home directory is set to 755.

No reason,i want to give only read and write permission to the user vivek but not delete..How can i do this..?

---

### Post by CharlesA on 2010-10-26
You can't really do that with normal linux permissions.

You'd have to look into ACLs: [http://linux.die.net/man/5/acl](http://linux.die.net/man/5/acl)

---

### Post by karthick87 on 2010-10-26
> **CharlesA said:**
> You can't really do that with normal linux permissions.

You'd have to look into ACLs: [http://linux.die.net/man/5/acl](http://linux.die.net/man/5/acl)

That sounds to be more technical,what is an ACL..?What it can do..?

---

### Post by CharlesA on 2010-10-26
> **getyourkarthick said:**
> That sounds to be more technical,what is an ACL..?What it can do..?

Access control lists. It sounds very... complicated.

Check here: [http://stackoverflow.com/questions/869536/linux-directory-permissions-read-write-but-not-delete](http://stackoverflow.com/questions/869536/linux-directory-permissions-read-write-but-not-delete)

---

### Post by sisco311 on 2010-10-26
> **getyourkarthick said:**
> No reason,i want to give only read and write permission to the user vivek but not delete..How can i do this..?

Not sure if this helps, but if you set the sticky bit on the directory, then only the owner of a file or the owner of the directory will be able to delete that file.

---

### Post by karthick87 on 2010-10-26
Do i want to install any additional package to use[COLOR=Red] ACL[/COLOR]..?

---

### Post by CharlesA on 2010-10-26
> **sisco311 said:**
> Not sure if this helps, but if you set the sticky bit on the directory, then only the owner of a file or the owner of the directory will be able to delete that file.
The link I posted mentioned the sticky bit, but I don't really know the ins and outs of that.

---

