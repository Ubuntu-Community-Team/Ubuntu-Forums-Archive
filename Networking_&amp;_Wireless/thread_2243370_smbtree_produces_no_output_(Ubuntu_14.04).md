---
title: "smbtree produces no output (Ubuntu 14.04)"
date: 2014-09-08
forum: Networking &amp; Wireless
---

### Post by goodstuff9 on 2014-09-08
Ubuntu 14.04 installed.  Also installed samba, system-config-samba, samba-common-bin, samba-common, smbclient, nautilus-share, fusemb, winbind, and cifs-utils, among others.   

I'm trying to get Samba to work.  Right now I have machines running either Ubuntu 14.04 or Lubuntu 14.04, but will soon be adding a Windows box to the mix.  I call my workgroup, "workgroup".  

After installing all the packages listed above, I thought the first thing I should do is make sure all is in order.  So, I ran testparm:  

```
main1@system1:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[shared_stuff]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    guest account = main1
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = bcast, host
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb
    guest ok = Yes

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

[shared_stuff]
    path = /home/main1/shared_stuff
    read only = No


```


I then ran smbtree, expecting to see the share "shared_stuff" in the output, but instead get nothing for the output:  

```
main1@system1:~$ smbtree
Enter main1's password: 
main1@system1:~$ 


```

I have looked all over the internet for any posting by an earthling regarding no output for smbtree, but I cannot figure out what is wrong.  Any help will be greatly appreciated.  


I also ran smbtree -d3:  

```
main1@system1:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.2 bcast=192.168.1.255 netmask=255.255.255.0
Enter main1's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f06594e7800] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f06594e7770] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f06594e7800] mpx_fde[(nil)] fd[7] - disabling


```


And, I do not have ufw running:  

```
main1@system1:~$ sudo ufw status
[sudo] password for main1: 
Status: inactive


```

---

### Post by bab1 on 2014-09-08
> **goodstuff9 said:**
> Ubuntu 14.04 installed.  Also installed samba, system-config-samba, samba-common-bin, samba-common, smbclient, nautilus-share, fusemb, winbind, and cifs-utils, among others.

Yikes!  You don't need all of that.  Some might even be detrimental to your setup.
>   

I'm trying to get Samba to work.  Right now I have machines running either Ubuntu 14.04 or Lubuntu 14.04, but will soon be adding a Windows box to the mix.  I call my workgroup, "workgroup".  

After installing all the packages listed above, I thought the first thing I should do is make sure all is in order.  So, I ran testparm:  

```
main1@system1:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[shared_stuff]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    guest account = main1
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = bcast, host
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb
    guest ok = Yes

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

[shared_stuff]
    path = /home/main1/shared_stuff
    read only = No


```

Testparm doesn't tell you what to use.  It really just tests that the parameters you have selected are correctly formed.
> 


I then ran smbtree, expecting to see the share "shared_stuff" in the output, but instead get nothing for the output:  

```
main1@system1:~$ smbtree
Enter main1's password: 
main1@system1:~$ 


```

I have looked all over the internet for any posting by an earthling regarding no output for smbtree, but I cannot figure out what is wrong.  Any help will be greatly appreciated.  


I also ran smbtree -d3:  

```
main1@system1:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.2 bcast=192.168.1.255 netmask=255.255.255.0
Enter main1's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f06594e7800] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f06594e7770] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f06594e7800] mpx_fde[(nil)] fd[7] - disabling


```

This shows that you can't resolve the names of the Workgroup or the Master Browser.  With out the name resolution nothing will be show.
> 


And, I do not have ufw running:  

```
main1@system1:~$ sudo ufw status
[sudo] password for main1: 
Status: inactive


```

When you use the parameter ```
name resolve order = bcast
```...you need to also declare the netbios name like this```
netbios name = SOME-NAME
```...where SOME-NAME is a name you chose that is less than 15 characters.  I would place this directly below the name resolution parameter.

Restart the smbd daemon (process) with this```
sudo service smbd restart
```...and after waiting a few minutes for the system to reconfigure itself post the output of this again```
smbtree -d3
```

---

### Post by goodstuff9 on 2014-09-08
Thanks for the reply BAB1.  

I added the netbios name line to the /etc/samba/smb.conf file as you suggested, as shown here:  

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = workgroup
    name resolve order = bcast host
    netbios name = system1


and then restarted smbd (and nmbd).  After a few minutes, I ran smbtree again.  No change - still the same problem, smbtree shows no output.  Any other ideas on what may be the problem?

---

### Post by goodstuff9 on 2014-09-08
I forgot to include the output of smbtree -d3 after making the change you suggested, here it is:  


```
main1@system1:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.2 bcast=192.168.1.255 netmask=255.255.255.0
Enter main1's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f9a1c1d67e0] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f9a1c1d6780] mpx_fde[(nil)] fd[7] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f9a1c1d6730] mpx_fde[(nil)] fd[7] - disabling


```

---

### Post by bab1 on 2014-09-08
Post the output of these commands ```

ifconfig -a

cat /etc/samba/smb.conf

pgrep -l mbd

```

---

### Post by goodstuff9 on 2014-09-13
Thanks Bab.  Sorry for the late response, been gone for a few days......  

In the meantime, before I saw your response above, just trying this and that, I found that doing this *seemed* to solve the problem:  

In the [Global] section of the Samba configuration file, I entere these two parameters:  

preferred master = Yes
    domain master = Yes

After making just that change, smbtree works, and the computer can now "see" the other computers.  


This may sound like a funny question after having written that above, but.....  Have I *really* solved the problem?  I read about these two parameters, I have to say I don't fully understand the true purpose of them nor their full impacts, so I am wondering if I've *solved* the problem while also unknowingly screwed up something else.

---

### Post by bab1 on 2014-09-13
> **goodstuff9 said:**
> Thanks Bab.  Sorry for the late response, been gone for a few days......  

In the meantime, before I saw your response above, just trying this and that, I found that doing this *seemed* to solve the problem:  

In the [Global] section of the Samba configuration file, I entere these two parameters:  

preferred master = Yes
    domain master = Yes

After making just that change, smbtree works, and the computer can now "see" the other computers.  


This may sound like a funny question after having written that above, but.....  Have I *really* solved the problem?  I read about these two parameters, I have to say I don't fully understand the true purpose of them nor their full impacts, so I am wondering if I've *solved* the problem while also unknowingly screwed up something else.

Using these parameters just reinforce the suspicion that you have a naming problem.  But if it works then so be it.

These parameters are use to insure that the Master Browse list is located on this specific Samba server.  The downside can be constant attempts to force an election to that condition in the background.

Why is this happening?  Most likely caused by you installing everything you cold find that had the name Samba in it.  :-(  
What can be done?  If it were me I would start over and install only the *samba package*.

---

