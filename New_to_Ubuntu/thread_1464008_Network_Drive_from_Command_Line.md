---
title: "Network Drive from Command Line"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by rboesch on 2010-04-27
Hello,

If I use "Connect to Server" and add an shh location, can I get to these files in the command line? 

The reason I need to do this is I want to run MATLAB from one linux server and access files on another server (i.e. sftp to server B, launch MATLAB from server A, open files from server B from MATLAB on server A). If I do this from Windows, it is simple (I map the network drive and then when I launch MATLAB I can just change my "Current Directory" to that drive). It doesn't seem to be so simple on Ubuntu (when I go to change directories, I can only see root and not my mapped drives). 

I am currently using a workaround where I scp the files to the server that MATLAB is on, but this is killing to much of my time. 

Thanks for the help,

Ryan

---

### Post by jvc26 on 2010-04-28
Well, do you want to access the files?

```
ssh <user>@<server>
```

and then trundle round in the directories in a session on the remote server.

Or, you can use sshfs (part of fuse) to mount the remote filesystem locally (you may need to install sshfs via apt-get):

```
sshfs <remote location> <local dir>
```

sshfs is, I think the method that gnome uses to mount such dirs as you describe. I think gnome itself puts them under the .gvfs/ folder in your home directory when you mount through the connect to server.

Hope that helps,

J

---

### Post by Ollytheninja on 2010-08-07
Yes you can:

the location is:

/home/[username]/.gvfs/[name of volume]/...

I only got this by opening a a file on the remote server with Quanta+.

I found this thread because I want to know how to 
1: map it from commandline instead of through the connect to server menu
2: how to put it at a more accessible location like /media/myserver

keen to know how you get on

---

### Post by nothingspecial on 2010-08-07
> **Ollytheninja said:**
> 
1: map it from commandline instead of through the connect to server menu
2: how to put it at a more accessible location like /media/myserver


```
sshfs -o idmap=user user@address:/path/to/directory /where/you/want/it/mounted
```

eg, to mount my music collection on my netbook when at home

```
sshfs -o idmap=user ns@192.168.1.11:/home/ns/Music ~/Music
```

---

