---
title: "samba frustration"
date: 2016-12-07
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2016-12-07
after 2 days of tweaking samba.conf and windows 10 I can connect to shared files from Windows 10 to xubuntu 16.04. It works from all 4 win 10 to all 3 xubuntu. But I cannot go from ubuntu to ubuntu or ubuntu to windows 10. This needs to be able to connect to shared folders via GUI. I could manage ssh. But the librarians would never be able to, they need point and click and easy. I have folders shared. I have tweaked samba.conf with so many suggestions that it may be an issue but if so it doesn't seem like windows to xubuntu would work. It has to be all rwx and hopefully without filling in a password every connection. This is a small library and I am the only pitiful volunteer tech support. I do desktops pretty well but networking is very difficult. I have really studied and searched this with no luck. I thought the xubuntu to xubuntu would be the easy part! Thank you

---

### Post by TheFu on 2016-12-08
We will need some facts.  The output from **testparm** would be helpful and I always ask about name resolution. Are all the machines able to ping each other by the hostname?

Have you considered NFS for Unix to Unix sharing?  This is the native mode for all Unix systems and faster than CIFS.  File and directory permissions work as expected and there wouldn't be any need for end-users to "mount" the remote file systems. They would already be there after boot.

---

### Post by cmcanulty on 2016-12-08
I could look into NFS, I know nothing about it. The library wants all files kept on their own computers though. We really need the function of Xubuntu to Windows 10. I am appending the testparm output from the 3 relevant xuntu machines. it won't let me attach I guess because it is text. Ping works fine windows to Xub, Xub to Xub, and xub to windows. It may not be relevant but I am doing this remotely over rdp from Florida the library is in Michigan. I am able to go from window 10 to Xubuntu only by typing in the ip from windows explorer. It would be better to see the computer names under network for our very non tech savvy librarians.Thank you


```

librarian@Dell:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[allusers]"
Processing section "[homes]"
Processing section "[Anonymous]"
Loaded services file OK.
Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
	netbios name = UBUNTU
	server string = Samba Server %v
	server role = standalone server
	security = USER
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
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[allusers]
	comment = All Users
	path = /home/shares/allusers
	valid users = @users
	force group = users
	group = users
	read only = No
	create mask = 0660
	directory mask = 0771
	directory mode = 0771


[homes]
	comment = Home Directories
	valid users = %S
	read only = No
	create mask = 0700
	directory mask = 0700
	directory mode = 0700


[Anonymous]
	path = /samba/anonymous
	force user = nobody
	read only = No
	guest ok = Yes
librarian@Dell:~$ 
```



```
librarian@Office:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Anonymous]"
Loaded services file OK.
Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
	netbios name = UBUNTU
	server string = Samba Server %v
	server role = standalone server
	security = USER
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb
	username = librarian


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[Anonymous]
	path = /samba/anonymous
	force user = user
	read only = No
	guest ok = Yes
librarian@Office:~$
```





```


librarian@Gateway:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[allusers]"
Processing section "[homes]"
Processing section "[Anonymous]"
Loaded services file OK.
Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
	netbios name = UBUNTU
	server string = Samba Server %v
	server role = standalone server
	security = USER
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
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb


[printers]
	comment = All Printers
	path = /var/spool/samba
	read only = No
	create mask = 0700
	printable = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = No


[allusers]
	comment = All Users
	path = /home/shares/allusers
	valid users = @users
	force group = users
	group = users
	read only = No
	create mask = 0660
	directory mask = 0771
	directory mode = 0771


[homes]
	comment = Home Directories
	valid users = %S
	read only = No
	create mask = 0700
	directory mask = 0700
	directory mode = 0700


[Anonymous]
	path = /samba/anonymous
	force user = nobody
	read only = No
	guest ok = Yes
librarian@Gateway:~$ 

```

---

### Post by Morbius1 on 2016-12-08
Just passing through ........

You have three machines:
librarian@[COLOR=#0000cd]**Dell**[/COLOR]
librarian@[COLOR=#0000ff]**Office**[/COLOR]
librarian@[COLOR=#0000ff]**Gateway**[/COLOR]

Samba uses the linux host name as the netbios name that is visible on the network.

Yet in the smb.conf file for each of them you overrode the host / netbios name with this line:
> netbios name = UBUNTU

You can't have three machines in your network with the same name.

---

### Post by cmcanulty on 2016-12-08
OK I didn't alter that line for sure but I will change it and see what happens, thanks 

I changed them and rebooted. Same issue I can go windows-ubuntu, but not ubuntu to windows, or ubuntu to ubuntu, maybe I am not using the correct addressing scheme in network. I have tried by ip and by computer name. What is the correct way to type the target computer?

Here are some failed tries

```
librarian@Dell:~$ smb://Gateway/librarian
bash: smb://Gateway/librarian: No such file or directory
librarian@Dell:~$ smb://Gateway/Home/Librarian
bash: smb://Gateway/Home/Librarian: No such file or directory
librarian@Dell:~$ smb://192.168.1.35/home/librarian/Desktop
bash: smb://192.168.1.35/home/librarian/Desktop: No such file or directory
librarian@Dell:~$ 
```

---

### Post by Morbius1 on 2016-12-08
> librarian@Dell:~$ smb://Gateway/librarian
bash: smb://Gateway/librarian: No such file or directory
Bash has no idea what smb:// means. It requires an interpreter.

If you are using Xubuntu:
```
thunar smb://Gateway/librarian
```

---

### Post by SeijiSensei on 2016-12-08
The most transparent solution is to mount the remote SMB shares at startup via /etc/fstab.  Read this for more details: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

That said, the method you're using is going to be difficult to manage in the long-term.  How, for instance, do you back up the various librarians' files each day?  You should really consider having a central server; peer-to-peer networking only makes sense in the simplest of arrangements.  If it's a question of funds, perhaps there's some older desktop lying idle that can be converted to a server.  For your needs the important feature is disk space, not processing power.

---

### Post by cmcanulty on 2016-12-08
Backups aren't an issue everyone keeps their files on their own computer and I back them up weekly onsite and daily to crashplan and every few months to an ext hard drive kept off site

```
thunar smb://Gateway/librarian
```

 just went back to the prompt

---

### Post by Morbius1 on 2016-12-08
I can't help you. I know of no circumstance where running that command sequence would simply return to the prompt without either launching thunar and / or throwing you an error message of some kind.

Didn't have thunar? - you'd get an error message.
Gateway couldn’t be found? - you'd get an error message.
Ran it in a root instance of the terminal? - you'd get an error message.
Ran the command In Windows 10 powershell by mistake? - you'd get an error message.

As they say at the Windows support desk: I cannot reproduce your symptom.

---

### Post by SeijiSensei on 2016-12-08
What if you use //ip.address.of.server/ rather than //Gateway?  Any better?

---

### Post by cmcanulty on 2016-12-08
After 2 reboots it started connecting. Now is there a way to have certain computers automatically mount at boot rather than having to fill out name and password for each connection? What worked was the 

```
thunar smb://ip/share name
```

the thing I find weird is if I try to reach it from thunar it won't work but if I do the thunar ip from terminal it does. Another weird thing is I was trying to do "smb://ip/path to share" and it should be "smb://ip/share name". So I still have some work to do as the librarians aren't going to type things in terminal they want a shortcut from thunar which I have set up but they need reconnecting every time

thank you

---

### Post by TheFu on 2016-12-08
... NFS makes most of these issues go away for Unix-to-Unix sharing ... NFS shares appear and act like local storage (within reason).

It won't help Windows machines without $$$ for an NFS client or some magic to make the Win-Enterprise/Ultimate versions work. It is not included in Pro or less versions.

CIFS shares really aren't supposed to be this hard either.  If all the systems have static IPs, they all know how to resolve the names for all the other systems involved, and the smb.conf file is pretty trivially configured, it sorta "just works", IME.  It starts with basic network management and if that is handled well, other things drop into place.

BTW, the other 2 guys helping a EXTREMELY knowledgeable about this CIFS stuff. I've been lucky and never needed to know very much for it to work as needed.  I still prefer NFS, whenever possible for the reasons listed above.

---

### Post by cmcanulty on 2016-12-09
OK I will start studying NFS. Will it allow access from Linux and Windows 10?

---

### Post by Morbius1 on 2016-12-09
May I ask why you are using Linux? Is it a cost thing?

You have been posting issues with samba for years in this forum yet you seem surprised that running "smb://Gateway/librarian" in a terminal or that "smb://ip/path to share" in thunar doesn't work. 

Converting everything to macOS won't work since Apple now uses a compatible version of samba as the default file sharing mechanism so that's out. 

There is only one operating system that does not use Samba, SMB, netbios names, workgroups, etc.. and that's Windows. It's called a HomeGroup. Your situation does not sound like a home network but with only 7 machines I believe it can be "classified" as one:
> New in Windows 7, HomeGroup makes it easy for novices and systems administrators to network Windows 7 PCs on a LAN without a domain controller (DC) and to share resources such as printers and files. Although intended primarily for consumers, HomeGroup is also useful in small-business situations, in which there might not be ready access to IT support.
> **HomeGroup Protocol**

                                                                                                       The Microsoft HomeGroup protocol is an  open standard that relies on peer-to-peer (P2P) networking and the Web  Services on Devices (WSD) protocol to                                       publish and discover resources on a local subnet, without a  client/server infrastructure. IPv6 P2P graphing, facilitated by the Peer  Name Resolution                                      Protocol (PNRP), allows  computers to locate one another without a DHCP version 6 (DHCPv6)  server. PNRP also replaces the NetBIOS names and master                                       browser that were the mainstays of Windows for Workgroups  (WFW) networking for years.                                  


---

### Post by TheFu on 2016-12-09
> **cmcanulty said:**
> OK I will start studying NFS. Will it allow access from Linux and Windows 10?

That is not the primary purpose.  Windows uses CIFS natively, not NFS.  There are commercial NFS clients and servers for Windows, but they are cumbersome.  However, for Unix-to-Unix sharing, NFS is THE WAY to do it for systems on the same LAN.  NFS is not supposed to be used over the internet without extreme care. Usually a full VPN is needed, but [gatekeeper.dec.com]("http://ftp.labs.hpe.com/what-happened-to-gatekeeper.html") was a well-known read-only NFS server that was available over the internet for sharing Unix, F/LOSS, programs. I've never put an NFS server on the internet. Not once.

Window 10 - don't know much about it. Won't have it in my networks. I would use CIFS for those machines. Both CIFS and NFS can be used and concurrently access the same network storage from different clients.

**Full warning:**
Beware, if you are a causal end-user and not a professional admin. It may appear overly complex.  NFS is system-to-system network files.  It is not controlled by individual users. The mounts happen by the OS on the client-side. The server side controls what access is allowed. Userids and groupids need to match (the numbers) on all the systems sharing storage. If the numbers are swapped, then different usernames will have access to the wrong files. It is strictly the number (as returned by 'id') that matters. For remote storage, mainly only user and group accounts assigned to people need to map, since people will be sharing files.  Local system userids don't usually store files on NFS storage. If that is the intent, then those specific userids/groupids will need to be matched as well.  So if you have a group, librarians (510), that all librarians share files using, then the groupid (500) needs to the same on all systems.

But, if your network has static IPs and all userids are uniquely, but identically, assigned to individuals across all systems, then NFS will be trivial to setup for Unix systems on the same LAN.

I only mention this so you have another option to consider.  Definitely test it out in your lab first to get the feel and understand the limitations.  Make sense?

---

### Post by SeijiSensei on 2016-12-09
I will [once again]("https://ubuntuforums.org/showthread.php?t=2345752&p=13580251&viewfull=1#post13580251") recommend mounting the shares in /etc/fstab.  Is there a reason you don't want to take this route?  Why are you futzing with mounts from a file manager when you can just mount the shares into the filesystem tree and be done with it?

---

### Post by cmcanulty on 2016-12-09
I guess because the only times I have tried to use fstab I have really messed up the system. I though fstab was for drives that were always attached or available. Would you tell me how to list a shared LAN directory in fstab and would it create errors if the systems listed wern't always powered on? We leave on 4 computers but then during library hours I want all the other systems available to the librarians hopefully from a thunar shotcut or bookmark. Sorry I thought I had put thank you in last post. I am responding as soon as I can but I am not an employee and have to do this work as I have time. I seem to have the windows to windows and windows to linux working reliably after every reboot. It never asks for passwords. The issue still seems to be linux to linux and linux to windows. I have read numerous posts and many people seem to have the same issue. I think samba is working as it should except for saving passwords permanently. Every reboot it loses that info. Once I have everything connected it will go from one computer to another quickly but the password box never saves the passwords permanently after reboots even though I check that option. Can I store the linux password somewhere in a file so that linux keeps them? I could also learn NFS but according to post #12 above it only works for linux so then I would have samba and NFS which might get to be a mess. Sorry I thought I had put thank you in last post. Also sorry I am so stupid on networking, it's not for lack of reading and searching. Thank you!

---

### Post by cmcanulty on 2016-12-09
OK I have spent some time trying the fstab method but as usual no luck. I tried to follow the directions from this web article very carefully PS I fixed a missing space in fstab see end of post

[http://www.techrepublic.com/article/how-to-permanently-mount-a-windows-share-on-linux/]("http://www.techrepublic.com/article/how-to-permanently-mount-a-windows-share-on-linux/")

Here is the fstab after I did the directions
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=73fc4182-807f-41e0-a56f-cc239fd0bcd4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=374a88ce-deba-441f-940f-e20e9d840809 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=d521f636-07f9-4ac2-b626-ad4e99472d04 none            swap    sw              0       0
//192.168.1.224/librarian/media/share cifs credentials=/home/librarian/.smbcredentials,iocharset=uft8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0  
```

and here is the terminal output (there was a  typo in the web article that I corrected they had udi instead of uid)


```

librarian@Office:~$ sudo mkdir /media/share
[sudo] password for librarian: 
librarian@Office:~$ sudo apt-get install cifs-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cifs-utils is already the newest version (2:6.4-1ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
librarian@Office:~$ sudo apt-get install libnss-winbind winbind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libpam-winbind
The following NEW packages will be installed:
  libnss-winbind winbind
0 upgraded, 2 newly installed, 0 to remove and 16 not upgraded.
Need to get 423 kB of archives.
After this operation, 1,921 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 winbind amd64 2:4.3.11+dfsg-0ubuntu0.16.04.1 [410 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnss-winbind amd64 2:4.3.11+dfsg-0ubuntu0.16.04.1 [12.3 kB]
Fetched 423 kB in 0s (728 kB/s)           
Selecting previously unselected package winbind.
(Reading database ... 278352 files and directories currently installed.)
Preparing to unpack .../winbind_2%3a4.3.11+dfsg-0ubuntu0.16.04.1_amd64.deb ...
Unpacking winbind (2:4.3.11+dfsg-0ubuntu0.16.04.1) ...
Selecting previously unselected package libnss-winbind:amd64.
Preparing to unpack .../libnss-winbind_2%3a4.3.11+dfsg-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libnss-winbind:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu4) ...
Processing triggers for systemd (229-4ubuntu12) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
Setting up winbind (2:4.3.11+dfsg-0ubuntu0.16.04.1) ...
Setting up libnss-winbind:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu4) ...
librarian@Office:~$ sudo service networking restart
librarian@Office:~$ sudo cp /etc/fstab /etc/fstab.old
librarian@Office:~$ id USER
id: &#8216;USER&#8217;: no such user
librarian@Office:~$ id libratian
id: &#8216;libratian&#8217;: no such user
librarian@Office:~$ id librarian
uid=1000(librarian) gid=1000(librarian) groups=1000(librarian),0(root),1(daemon),2(bin),3(sys),4(adm),5(tty),6(disk),7(lp),20(dialout),24(cdrom),27(sudo),30(dip),46(plugdev),50(staff),100(users),107(crontab),113(lpadmin),114(lightdm),115(nopasswdlogin),116(whoopsie),117(mlocate),122(scanner),127(saned),128(sambashare),130(xrdp),1002(sambamachines)
librarian@Office:~$ sudo mount -a
mount: /etc/fstab: parse error: ignore entry at line 14.
librarian@Office:~$ sudo mount -a
mount: /etc/fstab: parse error: ignore entry at line 14.
librarian@Office:~$ sudo mount -a
mount: /etc/fstab: parse error: ignore entry at line 14.
librarian@Office:~$ sudo mount -a
mount error(79): Can not access a needed shared library
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
librarian@Office:~$ sudo mount -a
mount: mount point cifs does not exist
librarian@Office:~$ sudo apt-get install libpam-winbind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libpam-winbind
0 upgraded, 1 newly installed, 0 to remove and 16 not upgraded.
Need to get 28.3 kB of archives.
After this operation, 178 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpam-winbind amd64 2:4.3.11+dfsg-0ubuntu0.16.04.1 [28.3 kB]
Fetched 28.3 kB in 0s (47.1 kB/s)         
Selecting previously unselected package libpam-winbind:amd64.
(Reading database ... 278398 files and directories currently installed.)
Preparing to unpack .../libpam-winbind_2%3a4.3.11+dfsg-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libpam-winbind:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libpam-winbind:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.1) ...
librarian@Office:~$  sudo mount -a
mount: mount point cifs does not exist
librarian@Office:~$ sudo service networking restart
librarian@Office:~$ sudo mount -a
mount: mount point cifs does not exist
librarian@Office:~$ 
```

I have to be away for a few hours. I am really fstab braindead. Thank you!

PS I just saw a possible error of a missing space and now get a different error

```
librarian@Office:~$ sudo mount -a
mount error(79): Can not access a needed shared library
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
librarian@Office:~$
```

Here is the corrected fstab (I added a space after librarian) Note the user name and password are the same on both computers


```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=73fc4182-807f-41e0-a56f-cc239fd0bcd4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=374a88ce-deba-441f-940f-e20e9d840809 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=d521f636-07f9-4ac2-b626-ad4e99472d04 none            swap    sw              0       0
//192.168.1.224/librarian /media/share cifs credentials=/home/librarian/.smbcredentials,iocharset=uft8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0  
```

---

### Post by Morbius1 on 2016-12-09
Truly just a guess on my part but get rid of the **iocharset=uft8** option so that it looks like this:
```
//192.168.1.224/librarian /media/share cifs credentials=/home/librarian/.smbcredentials,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0
```
If that works just add it to the list of the two ( at least ) other anomalies described in this post.

---

### Post by TheFu on 2016-12-09
iocharset=uft8 is a typo.
**iocharset=utf8** is the correct version.
Gotta watch those details.

---

### Post by cmcanulty on 2016-12-09
OK I edited the fstab so it looks like below and I get a different error, fstab is difficult 


```

librarian@Office:~$ sudo mount -a
[sudo] password for librarian: 
mount: /etc/fstab: parse error: ignore entry at line 1.
librarian@Office:~$ 
```


 here is the fstab
```

ght# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=73fc4182-807f-41e0-a56f-cc239fd0bcd4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=374a88ce-deba-441f-940f-e20e9d840809 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=d521f636-07f9-4ac2-b626-ad4e99472d04 none            swap    sw              0       0
//192.168.1.224/librarian /media/share cifs credentials=/home/librarian/.smbcredentials,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0  
```

---

### Post by cmcanulty on 2016-12-09
Sorry but after the last terminal error it actually mounted! Now I have to rename the share so I can have several different shares. Will it produce an error if the share is powered off? Thank you again I never could have figured that out without help

---

### Post by cmcanulty on 2016-12-09
I got it to mount after the last error message it mounted anyway. I would have never known to remove the iocharset=uft8,

---

### Post by TheFu on 2016-12-09
> **cmcanulty said:**
> I got it to mount after the last error message it mounted anyway. I would have never known to remove the iocharset=uft8,

You didn't need to remove it. It was an incorrect option as it was put into the forums.  2 characters swapped.
Garbage in. Garbage out.  Need to be more careful with typos.

BTW, in the fstab above, the first 3 characters would prevent the fstab working. Again - typos.

---

### Post by cmcanulty on 2016-12-09
I was copying the text from the web site and have no idea what some of the code means. But now I cn go forward as it worked once I removed the  iocharset=uft8 option thanks to everyone!

---

### Post by TheFu on 2016-12-09
There is no uft8!


It is utf8.  [https://en.wikipedia.org/wiki/UTF-8](https://en.wikipedia.org/wiki/UTF-8)

I give up.  Again, it was a typo. Nothing more.  I'm out.

---

