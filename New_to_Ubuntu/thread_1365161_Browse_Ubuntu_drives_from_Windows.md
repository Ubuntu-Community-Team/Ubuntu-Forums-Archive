---
title: "Browse Ubuntu drives from Windows"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by exup1000 on 2009-12-26
Hi

I have searched the forums on this topic but the only answers I see are the reverse "browse window shares from ubuntu"
In my case I can browse windows shares ok. Eg smb://machinename/c$

When I try the reverse from a windows box, I cannot see anything, probably because I have not shared out the drives within Ubuntu.

I can ping the ubuntu box both by netbios name and Ip address. I can even enter the computers name in windows explorer eg \\testw100\

it resolves it ok but obviously is blank or empty.
Is there such a thing as c$ Admin shares in ubunutu?

So in order to browse all the drives on my Ubuntu box what do I need to do. I have about 5 drives. (some are ex windows NTFS)

I assume I dont have to turn it into a server?

Cheers Exup
(Sorry for the windows terminology)

---

### Post by adam814 on 2009-12-26
Your samba shares are defined in /etc/samba/smb.conf.  I would suggest mounting the extra drives under /media or something similar and then adding a share definition for each of them.  Maybe something like this:

```
[extdrive1]
     read only = no
     path = /media/extdrive1
     browseable = yes
     create mask = 775
```

---

### Post by adam814 on 2009-12-26
Err...I guess I shouldn't assume you already have samba installed (not just samba-common and samba-common-bin).  If not go ahead and do that.

P.S. I wouldn't really recommend sharing "/" over samba, but it already has a share in place you can un-comment to share home directories.  Also you might be interested in the system-config-samba package that provides a GUI for configuring samba shares.

---

### Post by exup1000 on 2009-12-26
Hi thanks for the direction to take. What is the terminology used when sharing out files or drives, is it "to mount" a folder?

also the gui version is that another package named "system-config-samba"

also how do I share out the printer, its still not seen even after going into printer configuration > Server > Settings and ticking publish shared printers?

cheers

---

### Post by jim-fwb on 2009-12-26
I could be wrong, but so far as I know, default Windows installs do not have an installed driver to read ext2/3/4 or other *nix filesystems.  A driver has to be installed, presumably MS or some 3rd party has such driver, but I'm clueless as to where you'd get it from.  Seems like some people occasionally format a /media partition as FAT 32 when installing, so that they have a place to exchange data "between dimensions/universes" as it were.

---

### Post by bodhi.zazen on 2009-12-27
> **jim-fwb said:**
> I could be wrong, but so far as I know, default Windows installs do not have an installed driver to read ext2/3/4 or other *nix filesystems.  A driver has to be installed, presumably MS or some 3rd party has such driver, but I'm clueless as to where you'd get it from.  Seems like some people occasionally format a /media partition as FAT 32 when installing, so that they have a place to exchange data "between dimensions/universes" as it were.

That is true if you are trying to read your Linux partitions from windows. IN that case you can try the windows driver - fsdriver:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Obviously ,most web servers are *nix , and you can read the files over http =)

In this case, however, we are talking a network share, in this case Samba.

To set up a samba share see this :

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

If you run into problems, are you running a firewall on either the Windows box or Ubuntu server ?

---

### Post by exup1000 on 2009-12-27
Hi

I quickly followed the guide in your link and shared out a folder (on an NTFS partitioned drive) on the ubuntu server. Simply shared it out by right clicking in nautilus and sharing seting it to "share this folder" and "allow others to create and delete files in this folder" - I didnt check the guest access as I have created an account for the user on the ubuntu server. I then let it set permissions.

On the windows machine I can now see the shared folder but get a log in prompt to access the files. I set the credentials to be the ubuntu server name and / the user name "TESTW100/username" and the password. But it keeps prompting me for the password.

EDIT# I then went back and enabled guest access in the sharing gui, but no change in gaining access.

Secondly I am unable to see the printer, even though I have shared that out via the printer configuration gui and set it to server settings "publish" and "allow printing from the internet" I do not have firwall on either machine "sudo ufw disable"

Cheers.

---

### Post by exup1000 on 2009-12-27
Hi again,

not sure why but I tried the manual method in the linked article, and it appears that even though I have shared out the drive using the graphical method, it is not appearing in the smb.conf file. Also I saw in the printing section a reference to browsable = no so changed that to yes and can see and connect to the ubunutu printer.

Is this mismatch by design or am I missing something here, I would assume the gui method of sharing files and printers would update this smb.conf file?

Cheers

---

### Post by bodhi.zazen on 2009-12-27
Standard linux permissions apply to samba shares. I suggest you start with your ubuntu log in name. 

Not sure why you do not see changes in smb.conf =)

What directory are you trying to share and what are the permissions on the share ?

If it is your home directory, are you using encryption ?

What are your settings for guests ?

After editing smb.conf, you need to restart samba.

If you are using the manual method, did you create a samba user ?

After setting the share in the GUI, did you log off and back on ?

---

### Post by Morbius1 on 2009-12-27
First, you're mixing and matching two completely different methods of sharing folders. If you're right clicking and selecting "Sharing Option" your share definitions will not show up in smb.conf. 

If your needs are simple you don't have to spend a lot of time in smb.conf ( if any ). I have a feeling that at this point your using both methods to share the same folder. Please post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type [B]testparm -s
[/B][COLOR=Blue]*That "s" is a small case "S"*[/COLOR]

This will tell us what you are sharing and how you are sharing it.

---

### Post by adam814 on 2009-12-27
As I understand it shares through the right-click option in Nautilus fall under the "usershares" option meaning if you're not logged in it isn't shared and those defined in smb.conf are shared at boot.

I can't say I've extensively used the system-config-samba GUI, but at least the ones it shows are the ones defined in smb.conf so it just might update it.

Yes, it's just another package (i.e. sudo apt-get install system-config-samba and you have it).

---

### Post by Morbius1 on 2009-12-27
> **adam814 said:**
> As I understand it shares through the right-click option in Nautilus fall under the "usershares" option meaning if you're not logged in it isn't shared and those defined in smb.conf are shared at boot.

Nautilus-share follows the same rules as classic samba as far as access is concerned. If I boot up a system and before I login as a user the shares are accessible . If I login as user 1, the shares defined by user2 are accessible. The only difference is where the shares are defined:

/var/lib/samba/usershares vs smb.conf

---

### Post by exup1000 on 2009-12-27
Hi
quite a few questions posted, so many thanks for all your help on this.

Firstly thanks **Morbius1**for confirming the GUI and Manual methods do not link up. From here on then I will use the manual methods. (Editing smb.conf)

Results from your questions
net usershare info
[INDENT][documents]
path=/home/au009900/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=n

[my downloads]
path=/media/DATA3_MYDOWNL/My Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=n
[/INDENT]

sudo net usershare info
*nothing is returned - blank*

testparm -s
[INDENT]Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = TESTING
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
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
[/INDENT]

Not sure why there are two entries for browseable printers and why they are set to no as my smb.conf shows the following
[INDENT][printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no[/INDENT]

And for **bodhi.zazen**


What directory are you trying to share and what are the permissions on the share ? **two shares, on my home drive, Documents on ubuntu drive and a subfolder on an ex NTFS drive (physical) My Downloads permissions where set via the gui method as "allow others to create and delete files in this folder"**

If it is your home directory, are you using encryption ? **No**

What are your settings for guests ?**sorry not sure what you mean**

After editing smb.conf, you need to restart samba.**did that **

If you are using the manual method, did you create a samba user ? **the only manual thing I did was set printers to browseable = yes**

After setting the share in the GUI, did you log off and back on ? **no**

cheers.

---

### Post by exup1000 on 2009-12-27
I have restarted the machine, and I am still not able to access the shares. I can see them still, get prompted to provide credentials but not able to get into them, access denied.
Either logged in or not on the server.

I also lost the share to the ex ntfs partition, it would seem that I need to make this a permanenet mounted drive. Will search the forums on how to do this.

---

### Post by adam814 on 2009-12-27
Hmm...maybe the credentials aren't what you think they are?  You're using "unix password sync" so they should be the same credentials to log in to the desktop.  You might try running smbpasswd to change the password so you know for sure.

---

### Post by exup1000 on 2009-12-28
Hi,
yes good tip, missed that little bit in the guide so run smbpasswd -a username.

I can now see the folders ok and log into them, one is private the other public. As per the guide except I did make the public read only = no

As a test I can access the public folder (with out requiring credentials) and I can access the private by using credentials that are on the server.

But I am not able to edit anything, neither create or save documents. I can open and read them though.

Any advice?
Note I am only using the manual method now for creating shares. I removed all references to the net usershare.
I also managed to auto mount the partition ex windows NTFS partition using fstab.

---

### Post by Morbius1 on 2009-12-28
[COLOR=Red]EDIT: It looks like - true to your word - you're using classic samba. Sorry for the intrusion - please ignore this post.
[/COLOR]
From what you've posted so far you do not have any classic samba shares ( smb.conf ) only nautilus-shares:

From net usershare info:
> [documents]
path=/home/au009900/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=n

[my downloads]
path=/media/DATA3_MYDOWNL/My Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=nI would like to make a recommendation:

(1) Go back to nautilus and set "guest access" to allow,  just for the time being so we can eliminate authentication as a source of the problem.

(2) The real solution might not be a samba problem but a linux permissions problem especially if some of the folders you are sharing are mount points to fat32 or ntfs partitions. We could spend a lot of time trying to find out what those partitions are , who owns them, and what permissions are set on them. Or, since your using nautilus-share, try this:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following line to the **[COLOR=Blue][global][/COLOR]** section of that file:

**force user = your_linux_user_name**
[COLOR=Blue][I]For example force user = morbius1. Note: you don't have to create a samba user for youreself - no smbpasswd -a required. force user refers to the login name.

[/I][COLOR=Black]Save the file and exit gedit
Back in the terminal type: [B]sudo service samba restart

[/B]Wait a few minutes ( really - minutes - not kidding ) and then see if you can access those shares. If you can we can talk about setting up samba users and passwords if you still want to go that route.
[/COLOR][/COLOR]

---

### Post by exup1000 on 2009-12-28
Here is the testparm -s

Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[private]"
Processing section "[public]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = TESTING
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
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[private]
	comment = private share
	path = /media/windows1/My Downloads/1_Archived
	read only = No

[public]
	comment = public share
	path = /media/windows1/My Downloads/xmas tapes
	read only = No
	guest only = Yes
	guest ok = Yes

---

### Post by Morbius1 on 2009-12-28
Change this:

> [private]
    comment = private share
    path = /media/windows1/My Downloads/1_Archived
    read only = No

[public]
    comment = public share
    path = /media/windows1/My Downloads/xmas tapes
    read only = No
    guest only = Yes
    guest ok = YesTo this

> [private]
     comment = private share
     path = /media/windows1/My Downloads/1_Archived
[COLOR=Blue]force user = morbius1[/COLOR]
     read only = No
 
 [public]
     comment = public share
     path = /media/windows1/My Downloads/xmas tapes
     read only = No
[COLOR=Blue]force user = morbius1[/COLOR]
     guest ok = YesChange morbius1 to your own login user name.

Restart samba and give it a go

---

### Post by exup1000 on 2009-12-28
Hi

sorry still new to Linux, so probably throwing myself in the deep end here, but i think we are getting there.

Turns out that the drive as a whole does not have permissions set whilst on the server, when ever I mounted the drive I did so as su, and therefore could read and write to it, I did not twig that normal users could not write to it. So the permissions are currently only root can do anything.

So in theory all I now need to do is set permissions on that drive.
What is the best way to do this (preferably via editing fstab or smb.conf directly)

Cheers

[COLOR="Red"]Edit I will wait 30mins till posting as we are double posting ;0)[/COLOR]

---

### Post by Morbius1 on 2009-12-28
force user will eliminate the need to alter fstab. If you can access the partitions as yourself on your machine then force user will work. 

Note on** force use**r: If you allow guest everyone will have access. If you require authentication then only users that have password will have access. If you only allow read access then only read access will be permitted, but once they're into the share they will appear to be you.

Can you access the partitions as yourself on your PC?

---

### Post by exup1000 on 2009-12-28
added the force user but no change

I can access the partition but do not read write access.
Since auto mounting the partition in fstab it looks like only root has access.

---

### Post by Morbius1 on 2009-12-28
Open **Terminal **
Type [B]cat /etc/fstab
[/B]
Post the output please

---

### Post by exup1000 on 2009-12-28
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sde1 during installation
UUID=fd34a9ca-0b98-4718-bba2-9c98aa0952b9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde5 during installation
UUID=cf64f2fa-facb-4b09-8424-b9cf6aa23179 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1       /media/windows1 ntfs-3g    ro,auto,user,fmask=0111,dmask=0000 0       0

---

### Post by Morbius1 on 2009-12-28
I personally would change this:

>  /dev/sdc1       /media/windows1 ntfs-3g    ro,auto,user,fmask=0111,dmask=0000 0       0     To this:

/dev/sdc1       /media/windows1 ntfs-3g defaults,umask=000,uid=1000,gid=46 0 0

To make sure that you are uid=1000 type **id** in a terminal

Now in a Terminal:

Type **sudo umount /media/windows1**
Type **sudo mount -a**

---

### Post by exup1000 on 2009-12-28
Yes, it works, permission are now set so that I can edit files on the server and remotely.

Should I remove the force user = from the smb.conf file? So in theory any user thats created on the box can have access?

Can I ask what the switches mean, or you can point me in the direction to look them up.

Cheers!

---

### Post by Morbius1 on 2009-12-28
First, PRAISE BE !!!

Second, I would leave the force user in there and here's why. If you allow guest access and a remote user adds a file it will have ownership of user:group = nobody:nogroup. That will make it impossible for you, the login user from from editing that file. With force user, that file will come across with you as owner.

Third, the switches:

uid = user id. It tells fstab to make you ( uid=1000 ) the owner of the mount point. Only works for fat32 or ntfs partitions not linux filesystems.

gid =group id. 46 is the Ububntu default plugdev group. All users on your box are part of that group so it will allows other users ( assuming you have any others on that box ) certain privileges. 

umask. This is hard to explain coherently. It represents the permissions you do NOT want given by default.

0 - read/write/execute allowed
1 - truns off execute
2 - turns off write
4 - turns off read

They're additive, so it you wanted to disable any kind of access the value would be 7 ( 1+2+4 ).

Each digit represents who you are giving those permissions to:
user,group,others. So umask=000 will give read/write/execute permissions to everyone. 

In this particular case, since your using force user, it was a little overkill to set it as 000 but I figured you were getting frustrated by all this and I didn't want to take any chances :wink:

You could have made it umask=077 and it would still work as long as you were the only login user on that box.

---

### Post by adam814 on 2009-12-28
You just need to use chmod.  If you add your user to the sambashare group you can just do something like this:
```
sudo chmod -R 775 <share location>
```You want something with group write permissions.  Whether you need to set anything executable depends on what you're sharing.  You might get away with permissions as 664 if not, but setting it 775 would rule out a filesystem permissions issue preventing access.

---

### Post by Morbius1 on 2009-12-28
It's an NTFS partition, I'm fairly certain a chmod won't work

---

### Post by adam814 on 2009-12-28
Ah, you're right...It doesn't actually set the security bits on NTFS.  Now that you mention it I tried a couple of years ago to share files on an NTFS drive through Ubuntu with no luck, but everything worked perfectly on a native Linux filesystem (I was using reiserfs at the time).

You could convert it to a native Linux filesystem (since you describe it as ex-windows anyway).

If you have enough free space to play around with it you could adapt [http://en.gentoo-wiki.com/wiki/Custom_Stage4](http://en.gentoo-wiki.com/wiki/Custom_Stage4) to make a .tar.bz2 with all your files on it (perhaps set your excludes to /Windows and /System Volume Information on the drive you're backing up).  You wouldn't have to worry about the boot directory, just make sure you're in the top-level directory of your NTFS drive (i.e. /media/windows1 when you tar and when you extract so as to not overwrite your root).

Maybe that guide will help, maybe not.  The main thing to get is a backup and I found it useful when I converted from reiserfs to ext4.

Then with a backup you could reformat the volume to a Linux filesystem of your choice (ext2/3/4, reiserfs, xfs, jfs, etc.).  I personally like ext4 because for me it gives better throughput and keeps fragmentation very low using extents(under 1% for me).

---

### Post by exup1000 on 2009-12-28
Hi

yes praise indeed! all is working, so I now have a drive shared out with my windows machines. I probably wont convert the file system just yet as its early days with Linux and so still leaving the option to dual boot back into windows in case I need to do something I have yet to learn in Linux.

Eventually though I will probably convert all the drives over to native Linux so thanks for the tip.

Also I will continue to tinker with the permissions, I dont like public or guest usage, so will lock it down to only users created on the server. (Theres only four users to manage).

Many thanks for all the help and extra info, very informative, especially Morbius1.

Cheers once again.

---

### Post by exup1000 on 2010-01-02
Hmm, seems to have broken for some reason.

I did not get a chance to tinker with the permissions, left everything as it was,(excpet removed force user = username and tested it still worked) the only thing I have done is reboot the server. I noticed that when I shut down the server, it prompts for my root password, stating a service requires permission to terminate? Does not say what.

I found that when I went back to my windows boxes (that have not rebooted) they could see the share, but not navigate it.

I have tried to reset the smbppasswed which fix printing for one user. But I am stumped where to look to fix the problem, as I have not changed anything (or at least dont think I have)

I tried adding back force user = "my login"
restarted samba " sudo service samba restart"
nothing has fixed it. Any ideas?
Is there something I need to do when restarting the server or shutting it down?

Below is a print out of testparm -s

[INDENT]Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[My Downloads]"
Processing section "[Podcasts]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = TESTING
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
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[My Downloads]
	comment = My Downloads
	path = /media/windows1/My Downloads
	force user = au009900
	read only = No

[Podcasts]
	comment = Podcast
	path = /media/windows3/Redirected Folders/My Music/Podcasts
	read only = No

[/INDENT]

and my fstab

[INDENT]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sde1 during installation
UUID=fd34a9ca-0b98-4718-bba2-9c98aa0952b9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde5 during installation
UUID=cf64f2fa-facb-4b09-8424-b9cf6aa23179 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1       /media/windows1 ntfs-3g    defaults,umask=000,uid=1000,gid=46 0       0
/dev/sdd1       /media/windows2 ntfs-3g    defaults,umask=000,uid=1000,gid=46 0       0
/dev/sdb1       /media/windows3 ntfs-3g    defaults,umask=000,uid=1000,gid=46 0       0[/INDENT]

---

### Post by Morbius1 on 2010-01-02
> I found that when I went back to my windows boxes (that have not rebooted) they could see the share, but not navigate it.On one of the windows boxes, post the output of the following commands:

Open **Commnad Prompt** ( not the Run command but Command Prompt )
Type **net view**
Type **net view \\ubuntu_machine_name**

On the Ubuntu box:

Open **Terminal**
Type **smbtree**
Type [B]findsmb
[/B]Type[B] nmap -sT 192.168.0.100/22
[/B][COLOR=Blue]*Change 192.168.0.100 to the ip address of the Ubuntu machine*[/COLOR]

---

### Post by exup1000 on 2010-01-02
Hi

Ok, the results are as follows, from windows machine named SYDL9617

[INDENT]net view
System error 6118 has occured

The list of server for this workgroup is not currently available[/INDENT]

(Potentially because this windows machine is not a member of the workgroup at home, it a member of a domain from my work, but was working ok before and I had no problem connecting it to my home workgroup before in windows by providing workgroup credentials

net view \\TESTW100
[INDENT]share resources at \\testw100

Testw100 server (samba, Ubuntu)

Share name
My Downloads                         Disk        My Downloads
Peters_Officejet_fax                 Print       Peters_Officejet_Fax
Peters_Officejet_Printer             Print       Peters_Officejet_Printer
Podcasts                             Disk        Podcast[/INDENT]

Back on the server

smbtree
[INDENT]TESTING
	\\TESTW100       		TESTW100 server (Samba, Ubuntu)
		\\TESTW100\Peters_Officejet_fax	Peters_Officejet_fax
		\\TESTW100\Peters_Officejet_Printer	Peters_Officejet_Printer
		\\TESTW100\print$         	Printer Drivers
		\\TESTW100\My Downloads   	My Downloads
		\\TESTW100\Podcasts       	Podcast
		\\TESTW100\IPC$           	IPC Service (TESTW100 server (Samba, Ubuntu))
	\\TESTMCE01      		[/INDENT]

findsmb
[INDENT]                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.2     TESTW100      +[TESTING] [Unix] [Samba 3.4.0]
192.168.0.8     SYDL9617       [	PHARMA        ]
[/INDENT]

nmap -sT 192.168.0.2/22 (had to install nmap!) for this to run
[INDENT]                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.2     TESTW100      +[TESTING] [Unix] [Samba 3.4.0]
192.168.0.8     SYDL9617       [	PHARMA        ]
[/INDENT]

Interesting point is that its not showing up the other machine that is or was mapped to the server, TESTMCE01, it only makes one reference to it. That machine is in the same workgroup.

Cheers

---

### Post by Morbius1 on 2010-01-02
There's a Samba Myth that states that all workgroup names have to match. Let's see if we can use this thread to kill it off once and for all. I have 4 workgroups on my lan and there is no problem access shares or printers. Besides you said it did work before.

Based  on my notes of error 6118 it's usually caused by the windows firewall blocking smb ports. Try to disable not only the Windows firewall but also any anti-virus you have on windows. Just long enough to see if sharing returns.

---

### Post by Morbius1 on 2010-01-02
Sorry just noticed this which would have told us about the firewall indirectly. This is not the output of the nmap command:

> nmap -sT 192.168.0.2/22 (had to install nmap!) for this to run                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.2     TESTW100      +[TESTING] [Unix] [Samba 3.4.0]
192.168.0.8     SYDL9617       [    PHARMA        ]Please run it again.

---

### Post by exup1000 on 2010-01-02
Hi

yes sorry you are correct, bad copying and pasting.

try again.

~$ nmap -sT 192.168.0.2/22

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-01-03 09:30 EST
All 1000 scanned ports on 192.168.0.1 are filtered

Interesting ports on 192.168.0.2:
Not shown: 996 closed ports
PORT     STATE SERVICE
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
6881/tcp open  bittorrent-tracker

Interesting ports on 192.168.0.40:
Not shown: 998 closed ports
PORT   STATE SERVICE
23/tcp open  telnet
80/tcp open  http

Nmap done: 1024 IP addresses (3 hosts up) scanned in 103.45 seconds

---

### Post by Morbius1 on 2010-01-03
The output from nmap , if I'm reading it correctly, confirms my interpretation of the net view output.

> net view
System error 6118 has occured
This suggests a Windows firewall or Anti-Virus is in the way of smb or samba.

nmap can't see 192.168.0.8. Since nmap is independent of samba, and can basically ferret out anything, I think it points to a firewall issue.

[COLOR=Blue]EDIT: I missed this in the nmap output:[/COLOR]
> All 1000 scanned ports on 192.168.0.1 are filtered
I'm assuming that's your router. Have you made any changes to the router between when this all worked and now?

---

### Post by adam814 on 2010-01-03
I'd assume (even though it's an odd choice of IP for one) that 192.168.0.40 is a router as every one I've had had a web interface and a telnet interface you could open somehow and it would be unusual to run a telnet server on a normal machine (why not ssh?).

I'd also bet the one with 1000 filtered ports is a Windows machine.  If you're sharing anything from that machine ports 135/tcp, 139/tcp, and 445/tcp should probably be open, but if it's only a "client" it's normal not to have ports open.

Have you tried accessing the shares by IP instead of name?  You might be having WINS issues.  See if from your Windows machine you can connect to \\192.168.0.2\Podcasts rather than \\TESTW100\Podcasts.

---

### Post by exup1000 on 2010-01-04
Ahem, sorry for creating work for you, but I did make a change of all things to the BIOS of the server.

Long story but I built the ex-Windows on RAID enabled hardware albeit without using RAID (if you know what I mean, no redundancy). I then built Ubuntu with out RAID hardware enabled to be on the safe side. When dual booting early on I found I Windows would not completely boot unless I re-enabled RAID in the BIOS, interestingly Unbuntu did not mind if it was enabled or not it would still boot.

So all the configuration sharing out the drives was done with RAID (hardware only remember) off. I then had to jump into VISTA the other day and therefore re-enabled it, jumped back into Ubuntu, then all the connections would not work. I did not twig the changes at the BIOS level I had made, especially as I could see the drives still just not access them?  Also on the server, they were still viewable and editable:confused:.

Anyway, I have just tested it if RAID in the BIOS is on shares will not work. Which in a way is strange as a drive is a drive in the OS regardless of its hardware, as it could be USB, CDROM, SCSI, PCMICIA, etc etc.

One for the memory. Is there a solution to this? Would I need to enable RAID, delete the drives and then share them out again? 
I post fdisk for RAID on and off.

Below is RAID off.

[INDENT]
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x998c3452

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       59483   477797166   83  Linux
/dev/sda2           59484       60801    10586835    5  Extended
/dev/sda5           59484       60801    10586803+  82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff629c6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74973860

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff629c69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff629c6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312568832    7  HPFS/NTFS
[/INDENT]

---

### Post by exup1000 on 2010-01-04
And with RAID enable in the BIOS no changes that I can see. So perhaps I am looking in the wrong place.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x998c3452

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       59483   477797166   83  Linux
/dev/sda2           59484       60801    10586835    5  Extended
/dev/sda5           59484       60801    10586803+  82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff629c6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff629c6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff629c69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74973860

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       38914   312568832    7  HPFS/NTFS

---

### Post by exup1000 on 2010-01-04
Also I see that either this is a bug or by design but when I now log off the machine, it prompts me to enter in my password for root, "System policy prevents restarting the machine"  "Console kit system restart multiple users", there is refrence to a bug here [https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/486626](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/486626) but it may be by design, now that potentially I could have a remote user accessing a share?

Anyway its minor.

Cheers

Once again many thanks for all your great and intuitive posts.

---

