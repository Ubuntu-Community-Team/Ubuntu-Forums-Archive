---
title: "Need help with Samba write to disk"
date: 2015-04-16
forum: Networking &amp; Wireless
---

### Post by FerryGnu on 2015-04-16
Hi, I have set up Ubuntu on an old laptop as a NAS. I followed the easy instructions on this site and all is working - almost.

I have a assigned a specific user-name in Ubuntu for access via win8.1, \\192.168.5.65 mapped as drive Z - all good. 

The data files can be read by all the programs on the win8,.1 that store their data on drive Z - but they cannot write changes back as I get a "Permissions" error. It all slams shut very fast so I can't say exactly what the full error message is but the gist of it is something like, "user does not have permission."

The user-name is needed by win8.1 Credentials when mapping the drive and will not map without that being correct, so that part is working. I have set the Folder permissions as instructed in the set up guide here. 0755, I think it is which should be for Read/Write access.

Currently I have removed the user-name from Samba and can connect with no security and it will read and write OK. BUT, I would like a little password security on the network when Guest may be using it.

What do I need to do to let win8.1 write changed or new data files back?

---

### Post by bab1 on 2015-04-16
> **FerryGnu said:**
> Hi, I have set up Ubuntu on an old laptop as a NAS. I followed the easy instructions on this site and all is working - almost.

I have a assigned a specific user-name in Ubuntu for access via win8.1, \\192.168.5.65 mapped as drive Z - all good. 

The data files can be read by all the programs on the win8,.1 that store their data on drive Z - but they cannot write changes back as I get a "Permissions" error. It all slams shut very fast so I can't say exactly what the full error message is but the gist of it is something like, "user does not have permission."

The user-name is needed by win8.1 Credentials when mapping the drive and will not map without that being correct, so that part is working. I have set the Folder permissions as instructed in the set up guide here. 0755, I think it is which should be for Read/Write access.

Currently I have removed the user-name from Samba and can connect with no security and it will read and write OK. BUT, I would like a little password security on the network when Guest may be using it.

What do I need to do to let win8.1 write changed or new data files back?
Access to the Samba share only authenticates (who are you) the user.  File system authorization ( you can do this) is set by the Linux file system (ownership/permissions).  You need to have both a Samba user (smbpasswd -a) and a Linux user (adduser) for the system to work the way you want it to.  By default if no user is defined,  the guest user (nobody) and group (nogroup) is used to access the files.

It all works best if the Windows user name is the same as the Linux and Samba user names.  What guides are you actually using?  What are the permissions of the folder you are sharing?  What is the permissions of the contents of that folder?  What is the user name you are using?

---

### Post by FerryGnu on 2015-04-17
Thanks for the reply. I am using the same names and passwords for the entire Samba thing including the windows WORKGROUP. 

The guide I started with
[https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html)

Then gleaned user stuff from here
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Properties for /srv/samba/* are as you say, owned by nobody and and anygroup. I then did

adduser asamba

sudo smbpasswd -L -a asamba
sudo smbpasswd -L -e asamba
sudo restart smbd
sudo restart nmbd

I did some searching and found CHOWN (I am new to Linux if it is not obvious) and did...

sudo chown -r asamba:asamba /srv

But, it left the owner blank and it only changes the group to asamba
I changed it all back to nobody and nogroup OK
I made sure the the active user was...
su asamba

and tried it all again but still cannot get the owner to show

Where am I going wrong?

Thanks for taking the time with this.

---

### Post by bab1 on 2015-04-17
> **FerryGnu said:**
> Thanks for the reply. I am using the same names and passwords for the entire Samba thing including the windows WORKGROUP. 

The guide I started with
[https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html)

Then gleaned user stuff from here
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
Yikes, those references are really old.  What version of Ubuntu are you using?> 


Properties for /srv/samba/* are as you say, owned by nobody and and anygroup. 

Are you sure about that?  It should be *nobody:nogroup* in most cases.
> 
I then did

adduser asamba

sudo smbpasswd -L -a asamba
sudo smbpasswd -L -e asamba
sudo restart smbd
sudo restart nmbd

I did some searching and found CHOWN (I am new to Linux if it is not obvious) and did...

sudo chown -r asamba:asamba /srv

But, it left the owner blank and it only changes the group to asamba
I changed it all back to nobody and nogroup OK
I made sure the the active user was...
su asamba

and tried it all again but still cannot get the owner to show

Where am I going wrong?

Thanks for taking the time with this.
You should set the security to ```
security = user
```...This allows you to authenticate the user access.  If you need guest access you should set that in the share definition explicitly with ```
guest ok = yes
```

I set the Ubuntu file system ownership and permissions for the share directory first.  If you are going to have multiple users (user names) accessing the share you will need to manage access via the group ownership.  You have to set the sgid bit so that the group ownership is inherited by all files and subdirectories created in the share.  I use the* user-group* **users** and add all my Samba users to that group.  If you need to separate the users you can create your own user-group(s).  The user-group **users** is created by default when Ubuntu is installed.

Lastly I would then set the share definitions.

I would need to see the directory permissions of /srv.  I usually use this as a starting point```
/srv/samba
```...this way I can do this ```

/srv/backup

/srv/samba

/srv/www

```...this separates the various directories I use for server use (backup and web and samba).  The /srv root looks like this on my home server```

drwxrwsr-x  2 root  users 4.0K Jan 22 11:18 backup
drwxrwsr-x 11 root users 4.0K Mar 25 20:04 share
drwxrwsr-x  4 root  users 4.0K Jan 22 11:18 www

```
The public Samba share definition looks like this 
```

[Public]
        comment = Shared Data
        path = /srv/samba/public
        browseable = yes
        guest ok = yes
        force group = users
        writeable = yes
        create mask = 0664
        force directory mode = 2775

```
A semi private (multiple users but not everyone) looks like following.  Note that there is a VFS module used to provide a recycle bin```

[NAS-Data]
        comment = NAS-Data
        path = /srv/samba/data
        browseable = yes
        guest ok = no
        valid users = bab,egb
        force group = users
        writeable = yes
        create mask = 0664
        force directory mode = 2775
        vfs objects = recycle
        recycle:repository = rubbish
        recycle:keeptree = yes
        recycle:versions = yes

```

If you want specific help we can do that.  I would start with moving the data to a more flexible location (e.g /srv/samba/<<<some-directory>>) where some-directory is one of the shared directories.  I have multiple directories as I said before.

---

### Post by FerryGnu on 2015-04-17
Hi, thanks for the help. I am suing the latest 14... I did a search on Samba and those two came up and since everything seemed to work, except security, I assumed nothing had changed. Uh oh, "assumed!" :)

Sorry, my mistake, you are correct of course on the nobody:nogroup 

OK, I will try rolling back out of the entire Samba thing and use a more current set of instructions. I will see what I can find and then incorporate your suggestions. I am not yet savvy enough with Linux to adapt stuff as I go along. I like to go through in sequence so I can try and understand what I am doing. I have been programming since before the was windows, but have never laid a hand on Linux/Unix. Kinda steep curve going back to a command prompt for everything. Have not seen one for serious work for probably 25-years or more.

---

### Post by bab1 on 2015-04-17
> **FerryGnu said:**
> Hi, thanks for the help. I am suing the latest 14... I did a search on Samba and those two came up and since everything seemed to work, except security, I assumed nothing had changed. Uh oh, "assumed!" :)

Sorry, my mistake, you are correct of course on the nobody:nogroup 

OK, I will try rolling back out of the entire Samba thing and use a more current set of instructions. I will see what I can find and then incorporate your suggestions. I am not yet savvy enough with Linux to adapt stuff as I go along. I like to go through in sequence so I can try and understand what I am doing. I have been programming since before the was windows, but have never laid a hand on Linux/Unix. Kinda steep curve going back to a command prompt for everything. Have not seen one for serious work for probably 25-years or more.

If you don't configure Samba with the command line you are limiting yourself to using samba usershares.  These are for the users home directory  because the user is non-privileged.  The only conf file you need to work with is */etc/samba/smb.conf *.  I can walk (and explain) you through all of this if you want.  There is no straightforward documentation of this on the web.  There are only bits and pieces.  You are using Samba V4.  This has been the Ubuntu default since Ubuntu 14.04.  Most of the documentation is for Samba V3 so you have to be careful.  Some of the info is downright wrong so be careful.

---

### Post by FerryGnu on 2015-04-18
OK, thanks, I found this one (assume it is for Samba v4) before I got to read your latest message. I am working via the Command Line, albeit with a good deal of trial and error. :D

[https://www.liberiangeek.net/2015/01/install-configure-samba-ubuntu-14-10/](https://www.liberiangeek.net/2015/01/install-configure-samba-ubuntu-14-10/)

I followed that and the Secured Folder worked fine. I was able to Map the drive with Windows requiring the Credentials. I was then able to use windows to create folders, save new files and modify existing ones all to the Secured folder tree. I checked the Secured folder with another win8.1 computer and could not Map or access anything until I entered the Credentials, so all was good. 

After a reboot of both Ubuntu and windows, the drive maps and connects at win-logon OK. I can navigate to a Secured folder, I can see the file names but I cannot do anything with them. I get a File not found error from windows if I double-click on a test.txt file or test.jpg. 

So, I am happy to scrap it all and start again as I see this all as a valuable learning experience. Frustration is always mandatory for such experiences. LOL

So please guide me with this right from the start if you have the time to do so. Very much appreciated. I am retired and time is plentiful, so please do not feel any pressure. I am trying to learn and understand as I go along with this. Probably a stiff start to Ubuntu, but I like to learn by during useful things rather than just following a tutorial that I will not use the results of when done. 

I want to store my emails etc on the Ubuntu server so security from Guests on my home network is important. I trust them, but woul not like to see and accidental "delete" take place. :D

Harry

---

### Post by bab1 on 2015-04-18
> **FerryGnu said:**
> OK, thanks, I found this one (assume it is for Samba v4) before I got to read your latest message. I am working via the Command Line, albeit with a good deal of trial and error. :D

[https://www.liberiangeek.net/2015/01/install-configure-samba-ubuntu-14-10/](https://www.liberiangeek.net/2015/01/install-configure-samba-ubuntu-14-10/)

I followed that and the Secured Folder worked fine. I was able to Map the drive with Windows requiring the Credentials. I was then able to use windows to create folders, save new files and modify existing ones all to the Secured folder tree. I checked the Secured folder with another win8.1 computer and could not Map or access anything until I entered the Credentials, so all was good. 

After a reboot of both Ubuntu and windows, the drive maps and connects at win-logon OK. I can navigate to a Secured folder, I can see the file names but I cannot do anything with them. I get a File not found error from windows if I double-click on a test.txt file or test.jpg. 

So, I am happy to scrap it all and start again as I see this all as a valuable learning experience. Frustration is always mandatory for such experiences. LOL

So please guide me with this right from the start if you have the time to do so. Very much appreciated. I am retired and time is plentiful, so please do not feel any pressure. I am trying to learn and understand as I go along with this. Probably a stiff start to Ubuntu, but I like to learn by during useful things rather than just following a tutorial that I will not use the results of when done. 

I want to store my emails etc on the Ubuntu server so security from Guests on my home network is important. I trust them, but woul not like to see and accidental "delete" take place. :D

Harry
There are several misconceptions with the tutorial you used.  It's  overly complicated and shows a lack of conceptual understanding of what is really going on when Windows style sharing (Samba) is used.  Let's start at the beginning.  Do you have only test files in the directory /samba?   I assume you still have the backup copy of the original *smb.conf * file.

We need to check some network basics.  How have you configured the IP address on the machine that is to be the Samba server?  Are you using DHCP or Reserved IP or a Static IP address?  Is the Ubuntu install a desktop (with GUI) or a server (command line only)?  Can I assume that you have a simple LAN network with only 1 IP range (e.g 192.168.1.**1 -255**)?

---

### Post by FerryGnu on 2015-04-19
Using Static IP for some devices like cameras, cnc-machines.
Router (dd-wrt) is set for DHCP to catch other devices like Fire-Stick etc.
Router Default Gateway is 192.168.0.1
The LAN Range is 192.168.0.2-100 - but I can extend that if you have a penchant for higher IP values. :)
This Ubuntu laptop is set at 192.168.0.30 (wired) and 192.168.0.31 (wifi) Both same Gateway.
Current Static IPs in use range from 192.168.0.10 to 192.168.0.49 (inclusive) + 192.168.0.99 for the DSL modem.
Leaves 192.168.0.50 to 192.168.0.98 free
Ubuntu is the full GUI and setup as a dual boot with win7-pro-x64
Installed from win7 using WUBI which is in the Ubuntu CD (.iso) Root Folder. (for future reference)
I believe WUBI is only useable for XP to 7 installs. (for future reference)

Harry

---

### Post by bab1 on 2015-04-19
> **FerryGnu said:**
> Using Static IP for some devices like cameras, cnc-machines.
Router (dd-wrt) is set for DHCP to catch other devices like Fire-Stick etc.
Router Default Gateway is 192.168.0.1
The LAN Range is 192.168.0.2-100 - but I can extend that if you have a penchant for higher IP values. :)
This Ubuntu laptop is set at 192.168.0.30 (wired) and 192.168.0.31 (wifi) Both same Gateway.
Current Static IPs in use range from 192.168.0.10 to 192.168.0.49 (inclusive) + 192.168.0.99 for the DSL modem.
Leaves 192.168.0.50 to 192.168.0.98 free
Ubuntu is the full GUI and setup as a dual boot with win7-pro-x64
Installed from win7 using WUBI which is in the Ubuntu CD (.iso) Root Folder. (for future reference)
I believe WUBI is only useable for XP to 7 installs. (for future reference)

Harry 
So we are using a single IP segment LAN (192.168.0.0/24).  I would make sure that you use only the wired (Ethernet) connection.

Explain what the following means> Ubuntu is the full GUI and setup as a dual boot with win7-pro-x64
Installed from win7 using WUBI which is in the Ubuntu CD (.iso) Root Folder.
...Dual boot and WUBI are mutually exclusive.  You can only have one or the other.

Could you mean LiveCD test mode?

---

### Post by FerryGnu on 2015-04-19
BAB, you are of course correct. They didn't mention that fact with WUBI. :) Not to worry, always up for a challenge I am currently repartitioning the drive space I allocated from the win7 installation and will do the full Partition install of Ubuntu. 

Back soon. <-- That's the optimist within me :)

---

