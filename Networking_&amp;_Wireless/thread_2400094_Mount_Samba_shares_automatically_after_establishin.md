---
title: "Mount Samba shares automatically after establishing Wifi"
date: 2018-09-02
forum: Networking &amp; Wireless
---

### Post by Atalanttore on 2018-09-02
Hi

I use Ubuntu 18.04 on a Notebook and have some Samba shares in my home network. These Samba shares are not always available (only when at home), but if available they should be  mounted automatically system-wide after establishing a Wifi connection.

What's the easiest way to do this?

Regards,
Atalanttore

---

### Post by TheFu on 2018-09-02
Well, for sometimes connected storage, I'd recommend using **autofs**.  When the storage is requested, then it is mounted.  Be certain to use "soft" mounts, so the machine doesn't lock up looking for amount that doesn't exist when you are away.

Of course, I've got to suggest using NFS for Unix-to-Unix storage. It provides native access, native permissions, and is a little faster.   autofs works well with NFS too.

Or you could write a script that checks what network you are on and mounts the storage. Drop this into your login autorun setup.

I don't think Samba does mounts for all users without a user mapping solution between Windows and Unix systems.  I haven't done that in a few decades now.  We had thousands of users and doing it with all the added/removed users was a pain for someone, not me.  Samba mount permissions are determined at mount time, so if you have multiple users who need access, more thought will be needed.

---

### Post by Atalanttore on 2018-09-04
Samba resp. SMB is mainly used because of the Windows computers in my home network.

Would you recommend to use NFS in addition to Samba for network shares?

---

### Post by Morbius1 on 2018-09-04
For the samba part you might consider Gigolo.

** Install it: 
```
sudo apt install gigolo
```

** Run it

** Go to Edit > Preferences > Interface > select "Start minimized in the Notification Area" and Disable "Show auto-connect error messages" 

** Then go to Edit Bookmarks > Add > Fill in the blanks - Don't forget to check "Auto-Connect":
[ATTACH=CONFIG]280983[/ATTACH]



** The only missing step which gigolo will not do for you is to make sure the applications itself runs at login. So go to Startup Applications > Add > And for the Command enter gigolo

The next time you log into your machine your share will be mounted. If you are not in that network where the server exists or if WiFi is not up at that moment gigolo will wait until both exist and then mount it.

---

### Post by Atalanttore on 2018-09-07
Gigolo looks nice and is already installed on my Ubuntu Notebook.

Does it offer a way to mount a network share in a specific mount directory (e.g. **/mnt/**<share>) on my Notebook?

---

### Post by SeijiSensei on 2018-09-07
> **Atalanttore said:**
> Would you recommend to use NFS in addition to Samba for network shares?

I run both Samba and NFS on my file server.  I only occasionally have need for CIFS, but I do run Win7 in a VirtualBox from time to time and connect to Samba from there.  I export the home directory on that server both ways.  I have a couple of other NFS-only shares that are exported only to Linux clients.

---

### Post by TheFu on 2018-09-07
The main downside for GUI tools is they usually use the very slow gvfs mount method, based on FUSE.  Very slow is giving too much credit, IMHO. People have reported 50% slower file transfers, but I don't know the truth. But it is *easier* and has a GUI.

If you want performance from networked storage, use config files (nfs or CIFS/samba) and a "real mount".  But it is your system, the choice is yours.  "Real mounts" show up in a list when you type "mount."

---

### Post by Morbius1 on 2018-09-07
>  Does it offer a way to mount a network share in a specific mount directory (e.g. **/mnt/**<share>) on my Notebook? 				
Nope. The closest you can get would be a link to the parent folder: /run/user/$UID/gvfs

---

### Post by Atalanttore on 2018-09-08
> **TheFu said:**
> The main downside for GUI tools is they usually  use the very slow gvfs mount method, based on FUSE.  Very slow is giving  too much credit, IMHO. People have reported 50% slower file transfers,  but I don't know the truth. But it is *easier* and has a GUI.

If you want performance from networked storage, use config files (nfs or  CIFS/samba) and a "real mount".  But it is your system, the choice is  yours.  "Real mounts" show up in a list when you type "mount."
I do prefer a working network share with 50% slower file transfers rather than a non-working network share with no file transfers.


> **Morbius1 said:**
> Nope. The closest you can get would be a link to the parent folder: /run/user/$UID/gvfs
Thank you for that hint.

---

### Post by TheFu on 2018-09-08
And if you use **autofs**, then you don't have the performance drop and the shares would be mounted on-demand, as requested. You seemed interested in other solutions, so I stopped making suggestions.

autofs acts as a smart mounter based on configuration files.  I do have a few CIFS mounts on 1 machine.
```
win7ult  -fstype=cifs,rw,iocharset=utf8,file_mode=0660,dir_mode=0770,credentials=/root/data/win7.credentials  ://172.22.22.8/Data
```
That's the main /etc/auto.Data file on my client Linux system. No spaces in any of the options, all on a single line. /etc/auto.master on the same machine has to point to auto.Data.

The mount looks like this:
```
/Data/win7ult$ df -h .
Filesystem          Size  Used Avail Use% Mounted on
//172.22.22.8/Data  101G   23G   79G  22% /Data/win7ult
```
You can force a username and groupname for the mount, if needed.  The mount options are part of the mount.cifs and get passed through directly. It won't be slow like FUSE and there isn't any GUI to configure it.

I also use autofs to mount USB storage devices, since they are sometimes available and sometimes not available.

---

### Post by Atalanttore on 2018-09-16
I've installed the ***autofs*** package and added the following lines to ***/etc/auto.master ...***
```
/mnt/ata   /etc/auto.cifs-shares
```

... the following lines to ***/etc/auto.cifs-shares*** ...
```
home -fstype=cifs,rw,credentials=/home/ata/.smbcredentials,file_mode=0777,dir_mode=077 ://192.168.178.250/ata
```

... and created the credentials file ***/home/ata/.smbcredentials***
```
username=<my_username_on_NAS>
password=<my_password_on_NAS>
```


The result is that ***autofs*** _doesn't_ mount the network share on-demand when the folder ***/mnt/ata*** is accessed.

---

### Post by TheFu on 2018-09-16
From the code above, it would be mounted into /mnt/ata/home, if I'm reading the config correctly.   This is a common mistake for people new to autofs.  It isn't exactly intuitively obvious the relationship between the settings in both config files and where things are actually mounted.  

If you want it in /mnt/ata, then auto.master should be 
```
/mnt   /etc/auto.cifs-shares
```
and the auto.cfs-shares ... 
```
ata  -fstype=cifs,rw,credentials=/home/ata/.smbcredentials,file_mode=0777,dir_mode=0777 ://192.168.178.250/ata
```
I fixed your dir_mode and suggest you might want to restrict both file_mode and dir_mode settings so that other doesn't have full delete/write access. But it is your machine.

If you don't want the auto.master file to have any control over the mount location, you can use **/-** at the beginning.
But there is a good reason that auto.master gets to control the top directory for all mounts in each separate config file.  Imagine you have 10,000 users and need 26 separate autofs HOME directory groups a,b,c, d, .... z based on the userids.  It is easier to have /u in the master file and a, b, c, d, ... z in the auto.nfs file.  This was inherited from the automounter tool, which predates autofs, I believe.  I think having the setting in the auto.master like we do is confusing, the more I think about it.

BTW, I wouldn't place mounts like this into either /mnt/ or /media/ ... those locations are for other purposes. The FHS spells out what they are for.

---

### Post by Atalanttore on 2018-09-16
I've applied your suggestions, but the only consequence is that the directory **ata** in **/mnt** has disappeared. There's still no mounting on-demand.


**autofs** is not intuitive at all, but fortunately I only have to setup it once.


What's the correct location for mounting Samba shares?

---

### Post by Morbius1 on 2018-09-16
You are restarting the autofs daemon after each of these changes, right?
```
sudo service autofs restart
```

---

### Post by Atalanttore on 2018-09-16
Yes. ;)

---

### Post by TheFu on 2018-09-16
> **Atalanttore said:**
>  What's the correct location for mounting Samba shares?

I can only suggest to check the settings again. If you post the updated lines ... 

As for "correct locations", I don't think there are any besides 
a) to avoid /mnt/ for non-temporary mounts used for admin stuff and 
b) to avoid /media/ because that is where the OS places things.  Having multiple service daemons trying to manage the same storage area is asking for trouble.
c) don't mount under a user's HOME.  This is mostly to prevent backup confusion.

For temporary mounts, like for USB storage, I'll use /misc/.
For network mounts, like NFS storage, I'll use /D/ or /Data/ if there isn't some good reason to do something else, like HOME directories.  For media, /D, /D2, /D3, /D4, .... you get the idea.  For backup storage, I use /misc/b-WHATVER.
But those are just my places and there are certainly exceptions.  Over time, storage changes purposes.

There are different opinions about these locations.   [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) might provide clues.

---

### Post by Atalanttore on 2018-09-30
I've created a new directory **/nas** for my NAS data after thinking several days about it.

**/etc/auto.master** now contains the following lines:
```
#
# Sample auto.master file
# This is a 'master' automounter map and it has the following format:
# mount-point [map-type[,format]:]map [options]
# For details of the format look at auto.master(5).
#
#/misc    /etc/auto.misc
#
# NOTE: mounts done from a hosts map will be mounted with the
#    "nosuid" and "nodev" options unless the "suid" and "dev"
#    options are explicitly given.
#
#/net    -hosts
#
# Include /etc/auto.master.d/*.autofs
# The included files must conform to the format of this file.
#
+dir:/etc/auto.master.d
#
# Include central master map if it can be found using
# nsswitch sources.
#
# Note that if there are entries for /net or /misc (as
# above) in the included master map any keys that are the
# same will not be seen as the first read key seen takes
# precedence.
#
+auto.master

# configure nfs automount (for ad-hoc connection to local NAS) 
/nas   /etc/auto.cifs-shares
```


**/etc/auto.cifs-shares** contains this:
```
ata -fstype=cifs,rw,credentials=/home/ata/.smbcredentials,file_mode=0660,dir_mode=0770 ://192.168.178.250/ata
```


**/home/ata/.smbcredentials** was not changed and contains this:
```
username=<my_username_on_NAS>
password=<my_password_on_NAS>
```



After editing these files the **autofs** daemon was restarted with ...
```
sudo service autofs restart
```
... but is still not working. The directory **/nas** is empty.

---

### Post by Morbius1 on 2018-09-30
> ata -fstype=cifs,rw,credentials=/home/ata/.smbcredentials,file_mode=0660,dir_mode=0770 ://192.168.178.250/ata
It's empty or you cannot access it?
How about adding your uid to the list of options so you own the mounted share:
> ata -fstype=cifs,rw,credentials=/home/ata/.smbcredentials,file_mode=0660,dir_mode=0770[COLOR=#0000cd]**,uid=atalanttore**[/COLOR] ://192.168.178.250/ata
You can also use your uid number. To verify what that is run:
```
id
```
> ata -fstype=cifs,rw,credentials=/home/ata/.smbcredentials,file_mode=0660,dir_mode=0770[COLOR=#0000cd]**,uid=1000**[/COLOR] ://192.168.178.250/ata

---

### Post by Atalanttore on 2018-09-30
> **Morbius1 said:**
> It's empty or you cannot access it?

The directory **/nas** is entirely empty. Accessing it is no problem.

> **Morbius1 said:**
> How about adding your uid to the list of options so you own the mounted share:

You can also use your uid number. To verify what that is run:
```
id
```

My uid number is 1000. I've added it to **/etc/auto.cifs-shares** and restarted the **autofs** daemon, but the problem hasn't changed.

---

### Post by Morbius1 on 2018-09-30
Have you done a manual mount of this thing. Try to mount it to say your Public folder:
```
sudo mount -t cifs //192.168.178.250/ata /home/atalanttore/Public -o username=xxx,password=yyy,file_mode=0770,dir_mode=0770,uid=1000,nounix
```
Note: If it's a nas device you may have to drop down to a lower level of security by adding the option: **sec=ntlm** and even an earlier smb dialect **vers=1.0**

---

### Post by Atalanttore on 2018-09-30
It's a NAS device and a manual mount works fine even without reduced security (**sec=ntlm**) or an earlier smb dialect (**vers=1.0**).

But why does it work manually and not automatically?

---

### Post by Morbius1 on 2018-09-30
The only difference between the manual cifs mount I suggested above and your autofs mount is the option nounix.
>                                                          ata -fstype=cifs,rw,credentials=/home/ata/.smbcredentials,file_mode=0660,dir_mode=0770[COLOR=#0000cd]**,uid=1000**[/COLOR][COLOR=#0000cd]**,nounix**[/COLOR] ://192.168.178.250/ata                      

     
 


---

### Post by TheFu on 2018-09-30
Did you restart the autofs service?  That is required with every config change.  Also, the mount will only show up when requested.  You need to ask for** /nas/ata/** to get it mounted.  Any request should work, open a terminal and do an **ls /nas/ata/**.  That's one example. I don't know how to make it work using a file browser, since the 'ata' directory won't show up until requested.

There is an option to make available mounts "ghost" before they are mounted.  This is specific to autofs.master and the line.   --ghost is the option.
```

/nas   /etc/auto.cifs-shares --timeout=60 --ghost
```
This should make using a file browser work, since the empty, unmounted, 'ata' will be there.

And don't forget to restart the autofs service after any config changes.

---

### Post by Atalanttore on 2018-10-03
> **TheFu said:**
> Did you restart the autofs service? That is required with every config change.
Yes.;)


> **TheFu said:**
> Also, the mount will only show up when requested.  You need to ask for** /nas/ata/** to get it mounted.  Any request should work, open a terminal and do an **ls /nas/ata/**.  That's one example. I don't know how to make it work using a file browser, since the 'ata' directory won't show up until requested.
**ls /nas/ata/** does work, but I want to use this share with GUI applications.


> **TheFu said:**
> There is an option to make available mounts "ghost" before they are mounted.  This is specific to autofs.master and the line.   --ghost is the option.
```

/nas   /etc/auto.cifs-shares --timeout=60 --ghost
```
This should make using a file browser work, since the empty, unmounted, 'ata' will be there.
Great! The parameter **--timeout=60 --ghost** solved the problem.

I've tested it with different GUI applications each after a reboot.


> **TheFu said:**
> And don't forget to restart the autofs service after any config changes.
I will never forget it (again).:wink:

[HR][/HR][SIZE=3][B]
Summary[/B][/SIZE]

1. I've created the new directory **/nas** on my machine.

2. Then I've created the new credentials file **/home/ata/.smbcredentials**:```
username=<my_username_on_NAS>
password=<my_password_on_NAS>
```

3. Then I added the following line to **/etc/auto.master**:
```
/nas   /etc/auto.cifs-shares --timeout=60 --ghost
```

4. Then I changed **/etc/auto.cifs-shares** to this:
```
ata -fstype=cifs,rw,credentials=/home/ata/.smbcredentials,file_mode=0660,dir_mode=0770,uid=1000 ://192.168.178.250/ata
```

---

### Post by TheFu on 2018-10-03
Very nice summary!  Please mark the thread as SOLVED - thread tools, near the top.

> 
I will never forget it (again).
Yes, you will. We all do. ;)  And in another 20 yrs, it will still happen even when you know better.  ;) ;) ;)

BTW, I really like your /nas mount name.

---

### Post by Atalanttore on 2018-10-03
I did the summary for other users, because as mentioned in comment #13 before, **autofs** is not intuitive at all, but fortunately you only have to do the setup once.

I called the mount point **/nas**, because my file server is a NAS.;)

---

### Post by Atalanttore on 2019-04-06
Today, I set up the same Samba mount point like described here on another Notebook running Ubuntu 18.04 and add a second mount point for another directory on my NAS.

For the second mount point I've added a second line to [B]/etc/auto.cifs-shares:
[/B]```
ata -fstype=cifs,rw,credentials=/home/ata/.smbcredentials,file_mode=0660,dir_mode=0770,uid=1000 ://192.168.178.250/ata
public -fstype=cifs,rw,credentials=/home/ata/.smbcredentials,file_mode=0660,dir_mode=0770,uid=1000 ://192.168.178.250/public
```

Unfortunately it doesn't work like this. No share is mounted at all. :sad:

---

