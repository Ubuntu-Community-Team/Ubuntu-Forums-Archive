---
title: "File Owner = Nobody??? Help me please"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by ddixonr on 2008-06-12
In an attempt to reiterate the problem I'm having with still no luck, here is it again from another angle:

Why does editing a shared file change the owner to "nobody"?

Details:

1. I created html files on my web server (desktop).
2. Rather than spend all my time confined to the desktop, I opted to share the necessary files/folders so that I can work from the laptop throughout the house.
3. After editing each file from the shared www folder, the files & folders appear with locks (looking at them from the desktop). The owner says "nobody."

Now, I can ONLY edit those locked files from the laptop. I know that I can change the owner with the chown command, but I'd have to do it after every edit (which can be several times a day).

---

### Post by stasplamadeala on 2008-06-12
I have this problem too

---

### Post by ddixonr on 2008-06-12
Even though these problems are related, my biggest problem has to do with the ftp site. I have about 10 usernames that have access. Everyone can download any file on there, but they can't add or contribute to the folders already there. This bugs me the most. Why can't all the files or folders created belong to the one user?

---

### Post by ddixonr on 2008-06-12
Surely someone knows about these permission/owner issues....

---

### Post by imneo on 2008-06-12
chown the files to the user that u are using on the server

```
chown username filename
```

---

### Post by stasplamadeala on 2008-06-12
Operation not permitted

---

### Post by Yuki_Nagato on 2008-06-12
This most likely requires the use of "sudo" in front of the command.

The username part is not the "Official" username, but the name used with the password to log into your session.

[http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.cmds/doc/aixcmds1/chown.htm]("http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.cmds/doc/aixcmds1/chown.htm")

Some additional reading.

---

### Post by ddixonr on 2008-06-12
I can't seem to get to the /var/www directory in terminal. Listing the contents of /var doesn't even show the www folder. SO confused.... :(

---

### Post by ddixonr on 2008-06-13
_

---

### Post by ddixonr on 2008-06-14
Does nobody know of this problem?

---

### Post by The Cog on 2008-06-14
Firstly, I don't know how you're sharing the files (you don't say). I guess different servers put their file in different places. If you know a filename, try the command:
locate <filename>
and see where it has ended up.

Secondly, many servers run under the account name nobody as a security thing. This means the server can't be subverted into writing into your home folder for instance - it doesn't have write permissions there. You can probably configure it to run under a different account name if you want, but unless you really know what you're doing and why, it's a Bad Idea.

---

### Post by blkcat1028 on 2009-02-11
I have had the same problem. It has something to do with shares created via Samba. I've found several fixes that are quite technical and frankly I couldn't bothered... until I found this [http://ubuntuforums.org/showthread.php?t=24008](http://ubuntuforums.org/showthread.php?t=24008). This creates a launcher that you can drag the offending folder to and it will magically open as root and then you can change the permissions. It worked for me. Good luck!

---

### Post by opto09 on 2009-03-17
I don't know if anybody is still wondering about this but you can use sudo chown to CHange OWNer of the folder. For instance I've just copied over a whole bunch of files/directories from a Windows box into a folder called /newFolder. I can use sudo chown -R myName /newFolder and it will change the owner of everything inside to myName.

:popcorn:

---

### Post by arvindshes on 2010-02-24
Nice thread. Great Help.

---

### Post by mblahay on 2011-08-25
The answer for why all the newly created or saved files are changing ownership to nobody has to do with the guest access to the share (I'm assuming it is guest access since the specific access being used was not stated). All guest that save or modify files will end up creating files that are owned by the user nobody, in the same manner that any user that creates a file will create a file owned by himself or herself.

How do you get around this? It is possible to change the guest user in the smb.conf file, but this may be a bad idea if you have other shares on the system. I would instead create a share with very specific user access or create a deamon that scans for new files and then executes the chown command on them.

---

### Post by SactoBob on 2011-08-25
Permissions still bother me too at times.  One workaround I do is edit files with supervisory rights.  e.g. gksu gedit <filename optional>
After typing the requested password, you to edit the file as root.
Of course, that may later cause more complications if "root" owns the edited file.

Another workaround - gksu nautilus (or gksu thunar) so  you can use the graphic interface to change ownerships and access.

---

### Post by capscrew on 2011-08-26
> **mblahay said:**
> The answer for why all the newly created or saved files are changing ownership to nobody has to do with the guest access to the share (I'm assuming it is guest access since the specific access being used was not stated). All guest to save to modify files will end up created files that are owned by the user nobody, in the same manner that any user that creates a file will create a file owned by himself or herself.

How do you get around this? It is possible to change the guest user in the smb.conf file, but this may be a bad idea if you have other shares on the system. I would instead create a share with very specific user access or create a deamon that scans for new files and then executes the chown command on them.

Yes it is possible to change the user that is used for the guest account.  You have to set the parameters in the /etc/samba/smb.conf file. This is done with 2 parts.  The first part is set by default.  It is the parameter *map to guest*.  This is a [global] parameter that says *"...logins with an invalid password are rejected, **unless the username does not exist,** in which case it is treated as a guest login and mapped into the guest account.*  It is defined as ```
map to guest = Bad User 
```

The second part is the [global] parameter *guest account *which is used to map the user you wish to be used as the Samba guest account.  The default is the user "nobody".  It is defined as ```
guest account = nobody
```

I use an account called *smbguest* on my system.

In practice, the user is not as important as the group the file is created with.  All of my Samba users and the guest account create files with the group *smbusers* and the permissions of 3664.  This allows any user that is part of the *smbusers* to manipulate the file.  In addition any directory (folder) is created with this group and the permissions are 3775.

These parameters are set by using extended permissions.  The leading 3 (as in 3775 or 3664) set the sticky bit on folders and sets the setguid to smbusers).  The sticky bit is set so no file or folder can be deleted except by the owner (creator) or root.  The setguid is what forces the file or folder when created to have the group the same as the folder it is created in.

First you set the directory that is the root of the share with the permissions and group ownership you want (in my case it looks like this [COLOR="Red"]Note the extended attributes[/COLOR])```
drw[COLOR="Red"]s[/COLOR]rw[COLOR="Red"]s[/COLOR]r-[COLOR="Red"]t[/COLOR]  9 root smbusers 4.0K 2011-08-23 19:01 backup
```Then you can force these create modes on in the /etc/samba/smb.conf.  These are [share] parameters.  They are used like this for files```
force create mode = 3664 
```

...and for directories ```
force directory mode = 0775 
```

All the samba configuration parameters for the smb.conf file are described [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.htm").

I also set the *umask* to 002 so any file created on the system is set to the minimum of 664 and any directory is set to 775.  The default is umask=022 which has a setting of 644 and 755.  The default is not appropriate for group usage.

In addition I set the underlaying file permissions to 3664 and directories to 3775.  This is explained [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid").

This is a lot of tuning to the system, but in the end you have a setup that allows any samba user to read, write and copy any shared file or folder while only the original creator or root can delete or change permissions on the file or folder.

If you have a need to control user access you can do that by changing the user group on any particular share.

---

### Post by mblahay on 2011-08-26
Wow, thank you Capscrew. It is good to get some information from someone who is experienced in this. I'm new to Samba, and Linux in general, and will try implementing the best practices you have laid out. Beware, I may be back with additional questions. :-)

---

### Post by debd on 2011-08-26
user 'nobody' is used for running processes on your system as a non-privileged user.

you can otherwise create a different user under a different group for accessing files through your web server or ftp, and next add your username as a member of that group.

groupadd -g < group-id> <group-name>
useradd -g <group-name> -d /dev/null -s /bin/false <username>  (-d and -s flags for home and shell respectively for security reasons, you may change that)

adding the new user to the application you are using would be application specific.

next, add your own user as a member of the newly crated group:
Open Administration > Groups and users > click on manage groups > navigate to the newly created group and add your user account as a member of the group.
(am not sure if adduser will add you to the group or rather create a new user and add it to the group; therefore the GUI way )

btw, adding your username to the group 'nogroup' (which user nobody belongs to isn't a good idea)

EDIT: heck.. that doesn't solve the problem :D

---

