---
title: "Unable to access mounted NAS"
date: 2021-10-15
forum: Networking &amp; Wireless
---

### Post by fckwan on 2021-10-15
In /etc/fstab
//192.168.1.125/home /home/fckwan/MyNAS1 cifs username=fckwan,password=<NAS password>,noperm,dir_mode=0777,file_mode=0777,iocharset=utf8,_netdev 0 0

ls -alg fstab
-rw-rw-rw- 1 root 1144 Oct 13 10:55 fstab
Then I reboot the machine. 
I then try to access the newly mounted /home/fckwan/MyNAS1

But I will see the following error :
mount: /home/fckwan/MyNAS1 : operation permitted for root only.
I log in as fckwan as an administrator.

What should I do to allow fckwan (a admin user) to access the mounted drive. I don't want to log in as root all the time.
As I don't know the root password.

---

### Post by Morbius1 on 2021-10-15
I think what is happening is that during the boot process the instructions in fstab are being executed before the networking stack is fully operational so the cifs mount fails and _netdev isn't enough to fix this.

You have two options:

[1] Change your existing fstab declaration but add 2 more options: noauto,user
```
//192.168.1.125/home /home/fckwan/MyNAS1 cifs  username=fckwan,password=<NAS  password>,noperm,dir_mode=0777,file_mode=0777,ioch arset=utf8,_netdev,noauto,user 0 0

```
**noauto** = will make it so it doesn't try to mount at boot time.
**user** = allows a mount by an ordinary ( non root ) user.

[2] A systemd automount - adding noauto,x-systemd.automount to the list of options.

The problem here is that you will need to change your mount point to something other than your home directory or under /media. So you create a mount point under /mnt for example and fstab would look something like this:
```
//192.168.1.125/home /mnt/MyNAS1 cifs  username=fckwan,password=<NAS  password>,noperm,dir_mode=0777,file_mode=0777,ioch   arset=utf8,_netdev,noauto,x-systemd.automount 0 0

```

Either way you should do the systemd 2-step after editing fstab to make sure your system is happy:
```
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target
```

---

### Post by fckwan on 2021-10-15
Option 1. The error message "mount: /home/fckwan/MyNAS1 : operation permitted for root only." no longer come up.This is some improvement. 
But nothing is in the folder. It is suppost to have a lot of files and directories there.

Option 2, When I try to access the /mnt/usbshare2 ( or other drive) it say " bash: cd: usbshare2: No such device"

The following is the sample line in /etc/fstab
//192.168.1.125/usbshare2 /mnt/usbshare2 cifs username=fckwan,password=<NAS Password>,noperm,dir_mode=0777,file_mode=0777,iocharset=utf8,_netdev,noauto,x-systemd.automount 0 0

I restart the machine after changing the fstab entries.

I attached the related screen shots for your reference.

---

### Post by Morbius1 on 2021-10-17
*** Create a mount point:
```
sudo mkdir /Temp
```
*** Do a temporary mount in verbose mode to see if there are any errors:
```
sudo mount -t cifs -vvv //192.168.1.125/home /Temp -o username=fckwan,password=<NASpassword>,noperm,dir_mode=0777,file_mode=0777
```

Check the permissions of /Temp and it's contents.

---

### Post by TheFu on 2021-10-17
Mounting CIFS or NFS storage underneath a HOME directory is asking for problems.  Mount the storage elsewhere, then use a symbolic link to make access from HOME easier.  Just a few weeks ago, someone else in these forums had all sorts of issues and wasted a few weeks of time trying to solve a problem - that turned out to be caused by mounting storage under his HOME.  Just don't do that and avoid those future issues now.

After you get the cifs mount command working in a temporary area, it is best to have a credentials file to put the CIFS credentials inside, so the entire world cannot see them in the fstab or in the process list.  Also, permissions of 777 are a terrible idea and should be tightened up ASAP. I get they are tempting.

---

### Post by fckwan on 2021-10-17
I changed the command to only -v instead of -vvv:
sudo mount -t cifs -v //192.168.1.125/home /Temp -o username=fckwan,password=<NAS password>,noperm,dir_mode=0777,file_mode=0777
created /Temp and changed permission
drwxrwxrwx   2 root       4096 Oct 17 15:57 Temp
The mount command above results in:
mount: /Temp: cannot mount //192.168.1.125/home read-only.

My Ubuntu is run within Virtual Box. Will it affect the result.
My NAS is just a Synology ds120j attached to the home network.It work in the Windows 10 system that host the virtual box without any problem.

---

### Post by Morbius1 on 2021-10-18
This would be a lot easier if I had your NAS since I've never seen your combination of error messages before.

All the usual suspects would result in a different error message:

I would just go through the checklist while I try to reproduce your errors on a standard Debian server:

** Make sure cifs-utils is installed:
```
sudo apt install cifs-utils
```
** I would replace noperm with nounix:
> sudo mount -t cifs -v //192.168.1.125/home /Temp -o  username=fckwan,password=<NAS  password>,[COLOR=#ff0000]**nounix**[/COLOR],dir_mode=0777,file_mode=0777
** I would make sure DSM on the synoloy had the max server SMB set to SMB3

As far as VirtualBox the default Network Adapter setting is NAT. For this situation that would be fine but it means that your Ubuntu machine can access others on the LAN but they cannot access you. If you want this Ubuntu machine to be a full member of the LAN you should set this to "Bridge Adapter"

---

### Post by fckwan on 2021-10-18
I installed cifs-utils
I ran the following command.
sudo mount -t cifs -v //192.168.1.125/home /Temp -o username=fckwan,password=<NAS Password>,nounix,dir_mode=0777,file_mode=0777
mount.cifs kernel mount options: ip=192.168.1.125,unc=\\192.168.1.125\home,nounix,dir_mode=0777,file_mode=0777,user=fckwan,pass=********
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) and kernel log messages (dmesg)

dmesg log
[  718.245913] FS-Cache: Loaded
[  718.479747] FS-Cache: Netfs 'cifs' registered for caching
[  718.530011] Key type cifs.spnego registered
[  718.530070] Key type cifs.idmap registered
[  718.536526] CIFS: No dialect specified on mount. Default has changed to a more secure dialect, SMB2.1 or later (e.g. SMB3.1.1), from CIFS (SMB1). To use the less secure SMB1 dialect to access old servers which do not support SMB3.1.1 (or even SMB3 or SMB2.1) specify vers=1.0 on mount.
[  718.536535] CIFS: Attempting to mount \\192.168.1.125\home
[  720.115790] CIFS: Status code returned 0xc000006d STATUS_LOGON_FAILURE
[  720.115838] CIFS: VFS: \\192.168.1.125 Send error in SessSetup = -13
[  720.115898] CIFS: VFS: cifs_mount failed w/return code = -13

My NAS Password contains special character . E.g., $, @^&!#%*, number, upper and lower case characters etc. Do I need to enclose the password in "" or ''?

---

### Post by TheFu on 2021-10-18
A command line gets interpreted by the shell. Many "special characters" have special meaning to the shell, so quoting is the minimal you should do. Using a credentials file would be even better for the options. As in :
  ```
credentials=/root/win7lap.credentials
```
Just be certain to place it somewhere that only root has access and no other userids can read.

The format of that file is:
```
username=thefu
password=4sklfg92s,&4,l@!#!!!kldsdf87b,
```
No spaces.  The first '=' is the delimiter between the key and the value for the key.

BTW, appears your NAS is running a very, very, old version of SAMBA.  You need to patch/upgrade it based on this error:
```
[ 718.536526] CIFS: No dialect specified on mount. Default has changed to a more secure dialect, SMB2.1 or later (e.g. SMB3.1.1), from CIFS (SMB1). To use the less secure SMB1 dialect to access old servers which do not support SMB3.1.1 (or even SMB3 or SMB2.1) specify vers=1.0 on mount.
```
Newer CIFS will negotiate reasonable versions.  Any version older than Win7 is considered unreasonable and needs a manual option.  But just update the NAS software and that should go away.  About a year ago, almost all typical HOME NAS devices had some pretty serious remote attack problems, so everyone should have patched then.

So see the specific version of CIFS that your NAS is offering ... 
```
sudo nmap --script smb-protocols 192.168.22.14
```
On my Ubuntu 18.04 CIFS server, I see:
```
....
Host script results:
| smb-protocols: 
|   dialects: 
|     2.10
|     3.00
|     3.02
|_    3.11

```
Morbius1 taught me that nmap command. Quite handy.

---

### Post by Morbius1 on 2021-10-19
If the ultimate goal is to create an fstab declaration the best approach is the credentials file that TheFu suggested. In fstab all these special characters would have to be converted so the system can interpret them correctly.

For example if the password is **my password** the fstab entry would have to be **my\040password**. Each special character has it's own code and it would be a burden to convert them all without making some kind of typo. Here is a list to show you what I mean: [https://www.asciitable.com/](https://www.asciitable.com/) You don't have to convert all of those characters but the special one's like #, $, etc have to be converted. Having it unconverted in the credentials file is easier.

> [  718.536526] CIFS: No dialect specified on mount. Default has changed  to a more secure dialect, SMB2.1 or later (e.g. SMB3.1.1), from CIFS  (SMB1). To use the less secure SMB1 dialect to access old servers which  do not support SMB3.1.1 (or even SMB3 or SMB2.1) specify vers=1.0 on  mount.
If your NAS doesn't support SMB2.1 or above you need to do what the caution suggests by adding to your mount / fstab statement [COLOR=#ff0000]**one**[/COLOR] of the following:

```
vers=1.0

vers=1.0,sec=ntlm

vers=2.0

```

[COLOR=#ff0000]**EDIT**[/COLOR]: Forgot that we are talking about a Synology NAS. Those are fairly sophisticated so unless you haven't updated your software in years I suspect it is already set to a max value of SMB3 but you should check it as I suggested in my previous post. The dmesg message is more a statement of fact rather than an actual error: "We are going to use SMB2.1 through SMB3 unless you specify otherwise...."

---

### Post by fckwan on 2021-10-22
[https://kb.synology.com/en-ca/DSM/tutorial/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS](https://kb.synology.com/en-ca/DSM/tutorial/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS)

I found this document on the web. I will try to follow the procedure mentioned in this document and see what happens.

[COLOR=#000000][I][ 718.536526] CIFS: No dialect specified on mount. Default has changed to a more secure dialect, SMB2.1 or later (e.g. SMB3.1.1), from CIFS (SMB1). To use the less secure SMB1 dialect to access old servers which do not support SMB3.1.1 (or even SMB3 or SMB2.1) specify vers=1.0 on mount.
[/I][/COLOR]The above is just warning. You can remove the warning by using the vers=3 parameter when doing mount.

---

### Post by fckwan on 2021-10-22
I following the instructions at the previous page.
Command:
sudo mount -t nfs 192.168.1.125:/volumeUSB1/usbshare /mnt/usbshare1

Result of df command
192.168.1.125:/volumeUSB1/usbshare 2930253824 2855389440  74864384  98% /mnt/usbshare1

Thank you very much for all of your help.

---

### Post by TheFu on 2021-10-22
There may be some tuning that could make the nfs mount much faster.
**df -Th  /mnt/usbshare1** output will provide hints as to whether those parameters can and should be used.
Whenever posting code or text files, please use 'code tags' ---- [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains.  Basically, it will make the text look like it was in a terminal, where columns line up. We are used to non-proportional fonts, so it makes that sort of text much more readable.


And rather than manually mounting nfs storage, I'd put a line into the /etc/fstab to handle that.

---

### Post by fckwan on 2022-06-16
[https://kb.synology.com/en-ca/DSM/tutorial/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS](https://kb.synology.com/en-ca/DSM/tutorial/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS)

The above is the recommended way to mount a Synoolgy NAS to a network.

---

