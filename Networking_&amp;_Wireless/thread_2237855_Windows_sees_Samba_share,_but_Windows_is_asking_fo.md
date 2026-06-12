---
title: "Windows sees Samba share, but Windows is asking for password"
date: 2014-08-04
forum: Networking &amp; Wireless
---

### Post by bulrush2 on 2014-08-04
[LIST]
[*]Server config: Ubuntu 14.04 running as a VM under Vsphere. Server machine name: 'ubuntucomp'. Server is part of workgroup (which is the default setup on the Windows end), and not part of a domain. 
[*]Client PC: Windows 7 running Putty 0.62 and Xming 6.9.0.31 
[*]Server hardware is already behind a firewall and there will only be one user using this server, me. 
[*]I only have Gnome installed, and only on the console. 
[*]It's a very new install of Ubuntu, so I have limited things installed, no file transfer at all, no email, etc. 
[*]I want Windows to be able to see a shared folder on Ubuntu. Namely, /home/chuck and everything under that dir. 
[*]I'm editing /etc/samba/smb.conf, but /usr/share/samba/smb.conf also exists. 
[*]Our IT guys has not done anything to add the new VM to a workgroup, domain, etc. We just created the VM on vSphere. 
[*]If I do Windows, Run, and type in the \\IP.of.the.Ubuntu machine, I get the Apache 2 default page. 
[*]Firewall (ufw) is disabled. 
[*]I'm not a network guy, I'm a programmer, and a newbie with any Linux administration. 
[/LIST]

I can see the Samba share in my Windows Explorer, so when I double click on it, it appears to ask me for a Windows password. The window's title box says "Windows Security", then at the top of the password window it says "Enter network password. Enter your password to connect to: UBNUNTUMACHINENAME".

My user in the dialog is already WINDOWSDOMAIN\chuck (my Windows network logon).

So, what username and password do I use? Does IT have to set something up on their end? 

These are the steps I've done.

[LIST=1]
[*]Ubuntu user "chuck" already exists. 
[*]"sudo smbpasswd -a chuck" # This adds the user to the Samba database. 
[*]sudo restart smbd; sudo restart nmbd 
[*]In the Windows dialog, I have tried my normal Windows network username and password, which doesn't work. 
[*]I've tried my Ubuntu username and password, which doesn't work. 
[*]I added my Ubuntu user using smbpasswd. 
[/LIST]

# Output of: net usershare info
```
get_share_list: file /var/lib/samba/usershares/home is not a regular file. Ignoring.
```

# Output of: testparm -s
```
[global]
    server string = %h server (Samba, Ubuntu) Machine: %m
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 100
    name resolve order = wins, lmhosts, hosts, bcast
    logon path = \\%N\profiles\%U
    os level = 65
    preferred master = Yes
    domain master = Yes
    dns proxy = No
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb
    create mask = 0644

[homes]
    comment = Home Directories
    read only = No
    create mask = 0700
    directory mask = 0700

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    write list = root, @lpadmin

[chuckshare]
    comment = Chuck's home dir share
    path = /home/chuck
    read only = No
    create mask = 0755
    guest ok = Yes
```

# Last 2 lines of the most recent /var/log/samba/log.ubuntucomp, which repeat through the whole file. I also noticed there are other machines on our networks creating log files here. 

```
[2014/08/04 10:57:11.089550,  0] ../source3/param/loadparm.c:4094(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/home owned by uid 0 is not a regular file

[2014/08/04 10:58:36.051563,  0] ../source3/param/loadparm.c:4094(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/home owned by uid 0 is not a regular file
```

---

### Post by wyliecoyoteuk on 2014-08-04
A while since I had to do this, but you need to realise that SAMBA users and Linux users are separate, although you may synchronise them.
also, you need to allow encrypted passwords in SAMBA.

Unless you are using Winbind to link SAMBA to the domain, you will need to use the username:  ubuntuservername\username or username@ubuntuservername

might be worth installing SWAT or WEBmin.

---

### Post by bulrush2 on 2014-08-04
What's the executable file for SWAT? I installed it, but when I do "which swat" i get nothing. 

I just installed gnome (package: "gnome", which has lots of extra stuff) and when I run gnome-desktop, I get an error: "libEGL warning: GLX/DRI2 is not supported. Failed to connect to session bus: Could not connect: Connection refused". I thought apt-get was supposed to install all dependencies. 

As mentioned above I'm running Xming, and other X win apps work, like nedit.

---

### Post by bab1 on 2014-08-04
> **bulrush2 said:**
> [LIST]
[*]Server config: Ubuntu 14.04 running as a VM under Vsphere 
[*]Client PC: Windows 7 running Putty 0.62 and Xming 6.9.0.31 
[*]Server hardware is already behind a firewall and there will only be one user using this server, me. 
[*]I want Windows to be able to see a shared folder on Ubuntu. Namely, /home/chuck and everything under that dir. 
[*[COLOR="#FF0000"]]I'm editing /etc/samba/smb.conf, but /usr/share/samba/smb.conf also exists.[/COLOR]
[*]I'm not a network guy, I'm a programmer, and a newbie with any Linux administration. 
[/LIST]
The smb.conf file at /usr/share is for documentation (a spare file)  The smbd daemon only parses the file /etc/samba/smb.conf by default. > 

I can see the Samba share in my Windows Explorer, so when I double click on it, it appears to ask me for a Windows password. The window's title box says "Windows Security", then at the top of the password window it says "Enter network password. Enter your password to connect to: UBNUNTUMACHINENAME".

My user in the dialog is already DOMAIN\chuck.
That should be the username you are logged in as on the Windows machine (i.e. the samba client)> 

So, what username and password do I use? Does IT have to set something up on their end? 

You shoud use the name and pass you set up in Samba.  This should set this up to be the same username and password for all machines you use.  Is the Samba server part of a Windows domain or are you just using workgroups.  If it is just using workgroups then the authentication used is stored on the local machine (the Ubuntu/Samba server).  If this is a domain situation then the DC holds the user names and passwords.  You would have to configure the Ubuntu machine to be part of the domain for user **authentication** (who are you).

The *authorization * (do you have the right) is via the directory/file ownership and permissions.  That is always the local machines responsibility.  In a domain situation this is coordinated with the DC.  
> 

These are the steps I've done.

[LIST=1]
[*]Ubuntu user "chuck" already exists. 
[*]"sudo smbpasswd -a chuck" # This adds the user to the Samba database. 
[*]sudo restart smbd; sudo restart nmbd 
[*]In the Windows dialog, I have tried my normal Windows network username and password, which doesn't work. 
[*]I've tried my Ubuntu username and password, which doesn't work. 
[*]I added my Ubuntu user using smbpasswd. 
[/LIST]


From the Samba server CLI post the of this```
sudo pdbedit -L
```...this lists all the users that are in the Samba user database.
> 
# Output of: net usershare info
```
get_share_list: file /var/lib/samba/usershares/home is not a regular file. Ignoring.
```


This indicates that as sometime you tried to create a share using the GUI interface.  These shares are stored at /var/lib/samba/usershares.  They do not depend upon a listing in the smb.conf file.  In fact they can create conflicts in permissions and access.
> 

# Output of: testparm -s
```
[global]
    server string = %h server (Samba, Ubuntu) Machine: %m
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 100
    name resolve order = wins, lmhosts, hosts, bcast
    logon path = \\%N\profiles\%U
    os level = 65
    preferred master = Yes
    domain master = Yes
    dns proxy = No
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb
    create mask = 0644

[homes]
    comment = Home Directories
    read only = No
    create mask = 0700
    directory mask = 0700

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    write list = root, @lpadmin

[chuckshare]
    comment = Chuck's home dir share
    path = /home/chuck
    read only = No
    create mask = 0755
    guest ok = Yes
```

This shows that you are using the Samba server in a workgroup (stand alone) situation.  It looks fine to me.
> 


# Last 2 lines of the most recent /var/log/samba/log.ubuntucomp, which repeat through the whole file. I also noticed there are other machines on our networks creating log files here. 

```
[2014/08/04 10:57:11.089550,  0] ../source3/param/loadparm.c:4094(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/home owned by uid 0 is not a regular file

[2014/08/04 10:58:36.051563,  0] ../source3/param/loadparm.c:4094(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/home owned by uid 0 is not a regular file
```
These are the usershares that were made using the GUI.  You can delete the file under /var/lib/samba/usershares .

I think you problem is with the Samba server's Linux permissions of the underlying file and directory permissions.

The first thing is to actually debug the login attempt.  From the Samba server CLI, post the output of this command```
smbtree -d3
```...log in using the Samba/Ubuntu user you set up (we should see that user with the pdbedit command above).

Testparm is used to check the well formedness of the various parameters.  It doesn't list all the parameters used.  Neither does the smb.conf  file.  But the smb.conf file does list all the changes from the default (good or bad).  Post the output of ```
cat /etc/samba/smb.conf
```

---

### Post by wyliecoyoteuk on 2014-08-04
swat is web based 
open a browser and type 

[http://localhost:901](http://localhost:901)

The glx/dri refers to 3d acceleration, which is probably not supported by Xming

---

### Post by bab1 on 2014-08-04
> **bulrush2 said:**
> What's the executable file for SWAT? I installed it, but when I do "which swat" i get nothing. 

Don't use SWAT.  It really can harm the smb.conf file comments.  It provides you nothing that you can't do with a simple text editor.
> 

I just installed gnome (package: "gnome", which has lots of extra stuff) and when I run gnome-desktop, I get an error: "libEGL warning: GLX/DRI2 is not supported. Failed to connect to session bus: Could not connect: Connection refused". I thought apt-get was supposed to install all dependencies. 

As mentioned above I'm running Xming, and other X win apps work, like nedit.
These are video driver errors.  The apt-get system itself doesn't seek out the dependancies.  It is a framework for the packager to add the dependencies needed.   The package needs to have the dependencies built into it.  It's possible that there is a bug in the package.  sorry but I can't help you with this.

---

### Post by wyliecoyoteuk on 2014-08-04
Swat is useful for understanding the options.

Xming needs to be installed with mesa support for 3D acceleration to work.

---

### Post by bab1 on 2014-08-04
> **wyliecoyoteuk said:**
> Swat is useful for understanding the options.

I wouldn't say *understanding the options *as much as SWAT makes the options available.  For a web based page the explains all the options I use [this]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html") when pondering the options.  You could use the text based version with ```
man smb.conf
```

SWAT has a nasty habit of deleting things it doesn't like.  Even if you want them in the smb.conf file.  It is not maintained any more so it is out of date.

[COLOR="#0000FF"]Edit:  Thinking about this further I would say that SWAT is not Samba 4.1 aware at all.  There have been slight changes to the defaults and options of some parameters. [/COLOR]

---

### Post by wyliecoyoteuk on 2014-08-04
Haven't used it in some time, so you are probably right if it is unmaintained.

---

### Post by bulrush2 on 2014-08-05
Thank you for your help. Here is the information you requested. Again, the Linux machine name is 'ubuntucomp' and you can see my user on Linux is 'chuck'. That is also my username on Windows. Please indicate if you are referring to the Linux or Windows username 'chuck'.


[LIST=1]
[*]Our IT guy has not done anything to add the new VM to a workgroup, domain, etc. We just created the VM on vSphere. 
[*]Looks like the machine ubuntucomp is in the default workgroup called "WORKGROUP". I'll fix the smb.conf to reflect that. 
[*]Firewall (ufw) is disabled. 
[/LIST]
 
Output of 'sudo pdbedit -L':

```
chuck@ubuntucomp:~/share$ sudo pdbedit -L
[sudo] password for chuck:
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
chuck:1000:Chuck R.
samba:1001:Samba server
nate:118:
chuck@ubuntucomp:~/share$
```

Output of 'smbtree -d3':

```
chuck@ubuntucomp:~/share$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=10.n.n.n bcast=10.19.255.255 netmask=255.255.0.0
Enter chuck's password:
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WKGP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WKGP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WKGP<0x1d>
Got a positive name query response from 10.19.3.13 ( 10.19.3.13 )
Connecting to 10.19.3.13 at port 445
Connecting to 10.19.3.13 at port 445
chuck@ubuntucomp:~/share$
```

When I enter my Linux username \\ubuntucomp\chuck into the Windows logon window I get the error: "\\UBUNTUCOMP is not accessible. You might now have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions."

Not sure what that means. I'm pretty new to this.

Output of smbstatus: 

```
chuck@ubuntucomp:/var/cache/samba$ smbstatus

Samba version 4.1.6-Ubuntu
PID     Username      Group         Machine                        
-------------------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED

Service      pid     machine       Connected at
-------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED
Failed to traverse sessions: NT_STATUS_ACCESS_DENIED

No locked files

```

[LIST=1]
[*]What should the permissions be for /var/cache/samba/gencache.tdb? I just changed /var/cache/samba/* to 0755 and that didn't help.
[*]Just so I understand this right, if I'm trying to get Windows Explorer to see my dir on Linux, then Windows is the client in this case? And Ubuntu has the share?
[*]Sounds like this is a bug: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1292548 ]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1292548")
[*][SIZE=2][FONT=arial]I've tried some ideas listed in the bug to fix it (use Ubuntu 13.10 smb.conf), but i cannot transfer files to Linux, nor paste into an Xwin editor like nedit, gedit from windows. [/FONT][/SIZE]
[*][SIZE=2][FONT=arial]Does IT have to add ubuntucomp to our domain? [/FONT][/SIZE]
[/LIST]
[SIZE=2][FONT=arial][/FONT][/SIZE]

---

### Post by wyliecoyoteuk on 2014-08-05
You might have to use the IP address instead of the name if it is not resolving e.g. chuck@10.19.3.13
Also remember that Linux is Case sensitive.
You will need password encryption enabled in the samba settings.

---

### Post by bab1 on 2014-08-06
> **bulrush2 said:**
> Thank you for your help. Here is the information you requested. Again, the Linux machine name is 'ubuntucomp' and you can see my user on Linux is 'chuck'. That is also my username on Windows. Please indicate if you are referring to the Linux or Windows username 'chuck'.


[LIST=1]
[*]Our IT guy has not done anything to add the new VM to a workgroup, domain, etc. We just created the VM on vSphere. 
[*]Looks like the machine ubuntucomp is in the default workgroup called "WORKGROUP". I'll fix the smb.conf to reflect that. 
[*]Firewall (ufw) is disabled. 
[/LIST]
 
Output of 'sudo pdbedit -L':

```
chuck@ubuntucomp:~/share$ sudo pdbedit -L
[sudo] password for chuck:
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
chuck:1000:Chuck R.
samba:1001:Samba server
nate:118:
chuck@ubuntucomp:~/share$
```

Output of 'smbtree -d3':

```
chuck@ubuntucomp:~/share$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=10.n.n.n bcast=10.19.255.255 netmask=255.255.0.0
Enter chuck's password:
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WKGP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WKGP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WKGP<0x1d>
Got a positive name query response from 10.19.3.13 ( 10.19.3.13 )
Connecting to 10.19.3.13 at port 445
Connecting to 10.19.3.13 at port 445
chuck@ubuntucomp:~/share$
```

When I enter my Linux username \\ubuntucomp\chuck into the Windows logon window I get the error: "\\UBUNTUCOMP is not accessible. You might now have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions."

Not sure what that means. I'm pretty new to this.

Output of smbstatus: 

```
chuck@ubuntucomp:/var/cache/samba$ smbstatus

Samba version 4.1.6-Ubuntu
PID     Username      Group         Machine                        
-------------------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED

Service      pid     machine       Connected at
-------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED
Failed to traverse sessions: NT_STATUS_ACCESS_DENIED

No locked files

```

[LIST=1]
[*]What should the permissions be for /var/cache/samba/gencache.tdb? I just changed /var/cache/samba/* to 0755 and that didn't help.
[*]Just so I understand this right, if I'm trying to get Windows Explorer to see my dir on Linux, then Windows is the client in this case? And Ubuntu has the share?
[*]Sounds like this is a bug: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1292548 ]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1292548")
[*][SIZE=2][FONT=arial]I've tried some ideas listed in the bug to fix it (use Ubuntu 13.10 smb.conf), but i cannot transfer files to Linux, nor paste into an Xwin editor like nedit, gedit from windows. [/FONT][/SIZE]
[*][SIZE=2][FONT=arial]Does IT have to add ubuntucomp to our domain? [/FONT][/SIZE]
[/LIST]
[SIZE=2][FONT=arial][/FONT][/SIZE]

There is no doubt that you have authentication problems.  I believe it is more related to [this]("http://ubuntuforums.org/showthread.php?t=2214042") problem which has to do with syncing the local linux user and the samba user ( libpam-smbpass).  Pay close attention to post #7 and on.

I would sure like to take a look at the /etc/samba/smb.conf file.

I have had no problems using Samba4 as a stand alone server.  It acts just like Samba3.  

Is this a stand alone **workgroup** Samba server?  if so the only login you need is the username (e.g chuck).  There is no provision for UNC naming in Samba (\\server\share) the convention of //servername/chuck or //ip-address/chuck is also not valid.  This is the format for the SMB resource (i.e. the samba or Windows share).  

At the Ubuntu servers command line the Samba login for sure is only "chuck".  If that doesn't work for you then the username authentication is broken.  If this is the case, I would start thinking about purging all Samba packages (e.g. sudo apt-get purge <package name>).  There is no need to delete the /etc/samba directory or its contents.  I would copy the original smb.conf file back after re installing the packages samba and samba-common.

---

### Post by bulrush2 on 2014-08-06
I actually got it working. I was using the wrong login in the Windows password entry dialog. 


[LIST=1]
[*]The Windows network domain was "MYDOMAIN" so in the password dialog I just entered the linux user "samba" and that user's password. I didn't have to specify a new domain, but domain was the same as the workgroup specified in /etc/samba/smb.conf. (To help other users). 
[*]I believe the user "samba" also had an entry via smbpasswd. 
[*]Once I was in, I had read access to my Perl files, but not write access. I added MY Ubuntu user ("chuck") to a group called "users", which already existed for some reason. 
[*]In my /home/chuck dir I have a subdir called "perl". I the did the following. 
[*]'sudo adduser --group sambagrp' # Create group 
[*]'sudo adduser chuck sambagrp' # add chuck to sambagrp 
[*]Show who's in group 'sambagrp': getent group sambagrp 
[*]Went to perl/gilson/testdbi/ and did 'sudo chmod a+rw *'. '''That saves the file.''' 
[*]Went to $HOME and did 'sudo chmod -R a+rw perl/*' (Recursively change all file permissions. Giving rw to only user and group did not work.) 
[/LIST]

Marking closed, and thanks for all your help. :)

---

### Post by bab1 on 2014-08-06
> **bulrush2 said:**
> I actually got it working. I was using the wrong login in the Windows password entry dialog. 


[LIST=1]
[*]The Windows network domain was "MYDOMAIN" so in the password dialog I just entered the linux user "samba" and that user's password. I didn't have to specify a new domain, but domain was the same as the workgroup specified in /etc/samba/smb.conf. (To help other users). 
[*]I believe the user "samba" also had an entry via smbpasswd. 
[*]Once I was in, I had read access to my Perl files, but not write access. I added MY Ubuntu user ("chuck") to a group called "users", which already existed for some reason. 
[*]In my /home/chuck dir I have a subdir called "perl". I the did the following. 
[*]'sudo adduser --group sambagrp' # Create group 
[*]'sudo adduser chuck sambagrp' # add chuck to sambagrp 
[*]Show who's in group 'sambagrp': getent group sambagrp 
[*]Went to perl/gilson/testdbi/ and did 'sudo chmod a+rw *'. '''That saves the file.''' 
[*]Went to $HOME and did 'sudo chmod -R a+rw perl/*' (Recursively change all file permissions. Giving rw to only user and group did not work.) 
[/LIST]

Marking closed, and thanks for all your help. :)
Well, partially working.  All new files and directories will still have the ownership of user:user-group.  There is no directory group inheritance in  Linux by default.

Let us know when you get tiered of chmoding and chowning every file and directory you create.  There definitely is a proper method for allowing multiple user access to common files.  FYI:  These common group owned files should not be in your's or any one else's home.directory.

---

