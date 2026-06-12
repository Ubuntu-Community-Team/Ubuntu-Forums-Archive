---
title: "Can't Share files on network!"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by silvercue on 2011-08-23
I am trying to set up a backup job between my NAS and a HDD on my computer.  But the NAS can't see the folders on the computer.

I have installed file sharing and personal file sharing and looks like I have "shared the folders".  Still can't be seen by the NAS.

When I go to system and click on "personal file sharing options" I can't tick the option as it says:

"the feature cannot be enabled because the required software packages are not installed on your system".

But I have set up a shared folder called m*yname shared files *and the share folder box is ticked on that!??

Anything I can try??

---

### Post by skatinjj on 2011-08-23
Can you provide what OS and versions you are running?

---

### Post by madjr on 2011-08-23
> **silvercue said:**
> I am trying to set up a backup job between my NAS and a HDD on my computer.  But the NAS can't see the folders on the computer.

I have installed file sharing and personal file sharing and looks like I have "shared the folders".  Still can't be seen by the NAS.

When I go to system and click on "personal file sharing options" I can't tick the option as it says:

"the feature cannot be enabled because the required software packages are not installed on your system".

But I have set up a shared folder called m*yname shared files *and the share folder box is ticked on that!??

Anything I can try??

you have samba installed?

---

### Post by silvercue on 2011-08-24
> **skatinjj said:**
> Can you provide what OS and versions you are running?
 
Hi - yes I will do that tonight.  You need ubuntu version?  Anything else?

---

### Post by silvercue on 2011-08-24
> **madjr said:**
> you have samba installed?
 
Will check as soon as I get home :)

---

### Post by Frozen Forest on 2011-08-24
The option for file-sharing in systems isn't related to personal file sharing but to apache, configuration of samba is done in.
```
/etc/samba/smb.conf
```The shares are stored in the following folder, the program that manage the shares is gnome-user-share
```
/var/lib/samba/usershares
```If you are using ufw or iptables, will you have to allow traffic to and from some ports, you probably only want to allow traffic from LAN (usually 192.168.1.0/24)
```

netbios-ns -    137/udp                         # NETBIOS Name Service
netbios-dgm -  138/udp                         # NETBIOS Datagram Service
netbios-ssn  - 139/tcp                         # NETBIOS session service
microsoft-ds  - 445/tcp                        # if you are using Active Directory 

```[http://ubuntuforums.org/showthread.php?t=1823165](http://ubuntuforums.org/showthread.php?t=1823165)
[http://ubuntuforums.org/showthread.php?t=1824876](http://ubuntuforums.org/showthread.php?t=1824876)
[http://www.cyberciti.biz/faq/what-ports-need-to-be-open-for-samba-to-communicate-with-other-windowslinux-systems/](http://www.cyberciti.biz/faq/what-ports-need-to-be-open-for-samba-to-communicate-with-other-windowslinux-systems/) (137 & 138 are udp)

---

### Post by psylencer on 2011-08-24
**Important - SAMBA uses a different password to the system password
Make new SAMBA password for user
sudo smbpasswd  -a yourusername
(you will then be asked to type in and confirm the new SAMBA password).

You say your NAS cant see the folders?  NAS's don't usually communicate directly with other systems - other systems usually communicate directly with your NAS.  What NAS are you using?  Does it have an option to enter a Workgroup, username and passowrd?

---

### Post by Morbius1 on 2011-08-24
This is a very confusing post.

[1] The biggest confusion is what psylencer said:
> You say your NAS cant see the folders?  NAS's don't usually communicate  directly with other systems - other systems usually communicate directly  with your NAS.  What NAS are you using?  Does it have an option to  enter a Workgroup, username and passowrd?     [2] You appear to be using 3 completely different ways to share files:
> When I go to system and click on "personal file sharing options" I can't tick the option as it says:Personal File Sharing ( aka gnome-user-share ) is not Samba. It sets up a baby Apache file server and uses avahi to broadcast its only share - Public. It's unlikely that your nas ( or even Windows ) can communicate with this share so I wouldn't bother with it.

You make vague references to sharing folders and I'm guessing you are using Samba to do that but there are two different ways to share using Samba:

Classic - shares are defined in /etc/samba/smb.conf
Usershares - a.k.a. Nautilus-shares - shares are defined in /var/lib/samba/usershares

If you post the output of the following commands it will tell us what samba method you are using and how you are using it:
```
testparm -s
``````
net usershare info --long
```[3] If you post the output of this diagnostic command it would help the folks here determine the scope of the problem:
```
smbtree
```

---

### Post by silvercue on 2011-08-24
Hi - appreciate the replies.
 
When I say the NAS cannot see the drives, I should clarify that.
 
I have a ReadyNas Ultra 2 which I am using RAIDar to set up a backup job. RAIDar cannot see the drives on my computer - it only shows folders local to the NAS, which is a useless place to backup to, USBs attached to the NAS or you can remotely connect to FTP server etc.
 
There is an option to connect to an IP address and share name. This doesn't work with the way I have shared the folders. There is no way to browse drives or shares local to the computer becuase "something" can't see them.
 
So I assumed that making folders "shared" on the network may allow me to see them when I am in RAIDar.
 
I guess secondly - reading the posts above (thanks for those) I am rather bemused as to how difficult it seems to be to do something as simple as sharing files and folders in Linux. Starting to think this OS is really not for me at all.
 
I do appreciate the help though and if I can fix this I will stick with Ubuntu. If I can't it will be back to Windows as this is the main reason I want to use Ubuntu.

---

### Post by Morbius1 on 2011-08-24
> I have a ReadyNas Ultra 2 which I am using RAIDar to set up a backup  job. RAIDar cannot see the drives on my computer - it only shows folders  local to the NAS, From the Users Manual for that device:
> RAIDar Setup Utility
RAIDar is a discovery tool for the ReadyNAS devices on your network and enables easy setup and management of all your ReadyNAS units.

It automatically discovers the device or devices in the network without needing their IP addresses, and makes it easy to see the status of your units. You should see your ReadyNAS device or devices listed.

When you select a unit from the list and click the Setup button, RAIDar opens your default browser and connects you to the selected ReadyNAS.It would appear that it's working as designed. Users Manuals often confuse me but it would appear that RAIDar is used to find the NAS from the client not the other way around.

Do you have any further questions?

---

### Post by madjr on 2011-08-24
i've never really had problems sharing folders over the network on my lan, but with a nas it seems to be a bit different and since am not using one right now i cant help directly.

anyway, i found this (not sure if its your same problem, but give it a try):

[http://askubuntu.com/questions/22559/fstab-for-goflex-home-2tb-nas](http://askubuntu.com/questions/22559/fstab-for-goflex-home-2tb-nas)

---

### Post by Morbius1 on 2011-08-24
He's trying to create a backup job on the NAS not trying to access it from the client. There appears to be some level of confusion as to what a share is, for example:
> There is an option to connect to an IP address and share name. This doesn't work with the way I have shared the folders.
He's either using Personal File Sharing or Samba. If he's using Personal File Sharing there is a 107.36% chance that his NAS will never find it. If he's using Samba he refuses to tell us how he's using it.

---

### Post by silvercue on 2011-08-24
> **Morbius1 said:**
> From the Users Manual for that device:
It would appear that it's working as designed. Users Manuals often confuse me but it would appear that RAIDar is used to find the NAS from the client not the other way around.

Do you have any further questions? Hi Morbius - the set up has a separate section to set up backups - that bit I should be able to see shared folders on the computer.

I have shared a folder in Samba now also (sorry all was not at computer before).

The only difference that makes is that in the "source" option for backup there is now a heading for "all home shares" but "browse" is still greyed out and typing share location does not work....anyway this is not available in "destination" so I still can't do the back up I want.

---

### Post by Morbius1 on 2011-08-24
Crikey, I'll try this one more time. Please post the output of each of the following commands since none of here have telepathic powers to know how you are sharing your directories on Ubuntu:
```
testparm -s
net usershare info --long
smbtree

```As for this:
> The only difference that makes is that in the "source" option for backup  there is now a heading for "all home shares" but "browse" is still  greyed out and typing share location does not work....anyway this is not  available in "destination" so I still can't do the back up I want.     It sounds like a question for the ReadyNas forum.

---

### Post by silvercue on 2011-08-24
silvercue@silvercue-desktop:~$ 
silvercue@silvercue-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Backup]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Backup]
    comment = NAS Backup Folder
    path = /home/silvercue/Backup
    read only = No
    guest ok = Yes
silvercue@silvercue-desktop:~$ net usershare info --long
[shared files]
path=/home/silvercue/Shared Files
comment=
usershare_acl=Everyone:F,
guest_ok=n

[backup folder]
path=/home/silvercue/Backup
comment=
usershare_acl=Everyone:F,
guest_ok=n

silvercue@silvercue-desktop:~$ smbtree
Enter silvercue's password: 
WORKGROUP
    \\WDTVLIVE               WDTV LIVE
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
    \\SILVERCUE-DESKT        silvercue-desktop server (Samba, Ubuntu)
cli_start_connection: failed to connect to SILVERCUE-DESKT<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\MAMA_NAS               MAMA_NAS
        \\MAMA_NAS\addons-config      
        \\MAMA_NAS\backup             Backup Share
        \\MAMA_NAS\media              Media Server Share
        \\MAMA_NAS\webroot            
        \\MAMA_NAS\IPC$               IPC Service (MAMA_NAS)
silvercue@silvercue-desktop:~$ ^C
silvercue@silvercue-desktop:~$ ^C
silvercue@silvercue-desktop:~$ ^C
silvercue@silvercue-desktop:~$

---

### Post by Morbius1 on 2011-08-24
> silvercue-desktopEdit /etc/samba/smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section of smb.conf - right under the "workgroup" line would be my choice:
```
netbios name = silvercue-desk
```[COLOR=Blue]*It doesn't have to be that exact name but it has to be 15 characters or less in length. Anything longer and your machine is pretty much invisible on the lan.*[/COLOR]
[COLOR=Black]
Then restart samba and nmbd:
[/COLOR]```
[COLOR=Black]sudo service smbd restart
sudo service nmbd restart[/COLOR]
```[COLOR=Black]

You have two samba shares created using 2 different methods both pointing to the same target:
This is a Classic share:
[/COLOR]> [Backup]
    comment = NAS Backup Folder
    path = /home/silvercue/Backup
    read only = No
    guest ok = YesThis is a Usershare ( Created from Nautilus ):
> [backup folder]
path=/home/silvercue/Backup
comment=
usershare_acl=Everyone:F,
guest_ok=nOne allows guests the other does not. I would go into Nautilus and remove that share so that you only have the classic share.

[COLOR=Blue]**EDIT**[/COLOR]: Then run "smbtree" again and see how many errors are left.

---

### Post by silvercue on 2011-08-26
Thanks for your time and patience.

I think I must have done something wrong:  Should I have added a # in the config amendment?

Here is the result:

silvercue@silvercue-desktop:~$ smbtree
Enter silvercue's password: 
WORKGROUP
    \\WDTVLIVE               WDTV LIVE
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
    \\SILVERCUE-DESK         silvercue-desktop server (Samba, Ubuntu)
cli_start_connection: failed to connect to SILVERCUE-DESK<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\PC1                    PC1
cli_start_connection: failed to connect to PC1<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
    \\MAMA_NAS               MAMA_NAS
        \\MAMA_NAS\addons-config      
        \\MAMA_NAS\backup             Backup Share
        \\MAMA_NAS\media              Media Server Share
        \\MAMA_NAS\webroot            
        \\MAMA_NAS\USB_HDD_1          Freecom ToughDrive
        \\MAMA_NAS\IPC$               IPC Service (MAMA_NAS)
silvercue@silvercue-desktop:~$

---

### Post by Morbius1 on 2011-08-26
We have a serious problem here because you are running smbtree ( a samba client utility ) from SILVERCUE-DESK and it can't see it's own shares ( samba server ).

Just to make sure this isn't a Samba problem please run the following command and see if you can access your own shares:
```
nautilus smb://192.168.0.100
```[I][COLOR=Blue]Change 192.168.0.100 to the ip address of SILVERCUE-DESK[/COLOR]

[/I]If you can access the server then the problem isn't samba it's your network. BTW, if that works then just use the ip address in your NAS device to do the backup instead of the host name.

---

### Post by silvercue on 2011-08-26
when I run that command it opens the windows shares folder only.  No text is displayed in terminal.

The NAS is not in windows shares and nor are any of the shares on the NAS.

---

### Post by Morbius1 on 2011-08-26
> when I run that command it opens the windows shares folder only.I don't know what that means. Does it display and can you open the "Backup" share?
> The NAS is not in windows shares and nor are any of the shares on the NAS.     Don't know what that means either.

If you can access using the samba client of SILVERCUE-DESK the samba server share of SILVERCUE-DESK by ip address then use that same ip address from the NAS.

---

### Post by silvercue on 2011-08-26
it opens a view titled "Windows Share" which has three folders in it.

1. Backup
2. Print$
3. Shared Files

However, when I click on "shared files" I am prompted for my password as I get a message that the keyring did not unlock at login.  Backup I can access.


The other thing I meant was that I could not see any shares on my NAS I guess that may be what I should expect?)

EDIT - I think I may have manged to set up the back up job using IP address (needs testing though).  Though I have not got static IP address, and it doesn't  work with computer name.

EDIT2 - nope back up failed with permission error.

---

### Post by Morbius1 on 2011-08-26
OK, So it displays your shares and you can access the Backup guest share. That tells me that Samba itself is working.

So on the NAS use the same ip address where it asks for "Host" . 

> However, when I click on "shared files" I am prompted for my password as  I get a message that the keyring did not unlock at login.The first part about asking for a password I understand because you created that share requiring credentials. You are going to have to create a local user and add him to the samba database. Or you can connect using your own username and just add yourself to the database:
```
sudo smbpasswd -a your-user-name
```The second part of that error message about unlocking the keyring I'm not at all familiar with I'm afraid.

---

