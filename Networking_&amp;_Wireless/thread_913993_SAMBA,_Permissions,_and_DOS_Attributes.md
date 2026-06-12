---
title: "SAMBA, Permissions, and DOS Attributes"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by trashjunkid on 2008-09-08
Hello all-

I don't know how to clear up the following problem.

I have set up a samba server in accordance with the guidelines set out here:
[HOWTO: Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605").

I have two external harddrives mounted in the /home/samba/ directory. One works without any further instructions once mounted. The other was troublesome- in order to gain most of the permissions needed I had to use the "sudo mount -o umask=0000 /dev/whatever /home/samba/whatever" to get it working. I am now able to delete, rename or move most files there now. However, if one of the dos attribute flags is set, like archive, read-only or hidden, I am unable to do a thing with the file or folder. I am denied permission to do anything other than open the said files or folder.

I am connecting from a windows machine to the samba share. The external harddrive in question is fat32.

So, short of reformatting, how do I get that harddrive to give me permission to edit/move/delete those files and folders with thos dos attributes set? (I am able to edit/move/delete such flagged files on the other external hard drive which has been mounted using a simple sudo mount command).

Thanks for any help you might offer,
Trashjunkid

---

### Post by trashjunkid on 2008-09-10
Is there some sort of mounting option that would take care of those attributes? Can someone tell me how to approach this or point me to a resource that addresses this issue?

I appreciate any help that can be given,
Trashjunkid

---

### Post by Iowan on 2008-09-11
Have you tried **dmizer**'s CIFS [How-To]("http://ubuntuforums.org/showthread.php?t=288534")?

---

### Post by trashjunkid on 2008-09-11
Iowan-

Thanks for replying. I have looked at that link and I am unsure as to how it applies to my situation. I guess I have gathered that Samba is supposed to be the easiest/best way to share storage/devices between windows and linux machines. I'm really new to all of this and I find it frustrating to navigate the intricacies of getting this share setup. 

So, cifs is a file system like ntfs, or vfat or ext3? If my drive is vfat, how can I apply the information on cifs, short of formatting the drive?

Thanks for your suggestions and tips- you are singlehandedly helping me limp through this process,

Trashjunkid

---

### Post by dmizer on 2008-09-12
Did you configure a line in fstab specifically for mounting the external usb drive? The drive needs to be shared from a mapped directory.

In other words, you can share /dev/whatever but you'll run into permission problems. However, if you create a hard mount (in fstab with all the correct permissions) for /dev/whatever in /media/whatever first, then you can share /media/whatever from smb.conf

edit:
cifs is needed when accessing Windows shares from Ubuntu, not for accessing Ubuntu samba shares from Windows.

---

### Post by trashjunkid on 2008-09-12
dmizer-

I have created a shared directory /home/samba/ .

At that location I have created two directories, one for each hard drive. I plug in both hard drives. At first they automount, so I then umount them. 

The first drive I mount using a standard ```
sudo mount /dev/sdb1 /home/samba/worksgreat/ 
```. Everything works without further ado, no permisssions problems, I can create/move/delete anything everything from windows machine.

The second drive, which is vfat, I mounted normally and then had tons of permission problems to do anything but view the files/folders (could not move, rename, delete anything).

So now I have gotten rid of most of the permission problems by using the following mount command: ```
sudo mount -o umask=0000 /dev/sdc1 /home/samba/permission_troubles
``` . 

Doing so gives me permission to do most everything to the files/folders on the drive. However, any file or folder marked archive or read only I am denied permission to move/rename/or delete.

Would using the fstab to automount the drive make a difference? I am willing to try, but shouldn't a manual mount command with full permissions be possible?

Thanks for your help,
Trashjunkid

---

### Post by dmizer on 2008-09-12
Let's try something manual, and then try to work from there.

First of all, are the permissions on the /home/samba/permission_troubles directory owned by you, and in your group? When the drives are not mounted, 'ls -l /home/samba' should show something like this:
```
$ ls -l /home/samba
total 12076
drwxrwxrwx  6 you you     4096 2008-08-11 23:08 permission_troubles
drwxrwxrwx 28 you you     4096 2008-08-14 21:16 worksgreat
```
If not, you should change them with this command:
```
sudo chown -R you:you /home/samba
```
the "-R" option makes this command recursive so it happens to all sub directories.

For further discussion, it would also be helpful if you posted your smb.conf

---

### Post by trashjunkid on 2008-09-14
Here's the ls-l info you were looking for, unmounted and then mounted:```
paul@ubserver:/home/samba$ ls -l
total 8
drwxrwxrwx 2 root root 4096 2008-09-04 08:54 oldexternal
drwxrwxrwx 2 root root 4096 2008-09-04 08:54 wdpassport
paul@ubserver:/home/samba$ sudo mount /dev/sdb1 /home/samba/oldexternal
sudo: unable to resolve host ubserver
paul@ubserver:/home/samba$ sudo mount -o umask=0000 /dev/sdc1 /home/samba/wdpassport
sudo: unable to resolve host ubserver
paul@ubserver:/home/samba$ ls -l
total 40
drwxrwxrwx  1 root root  8192 2008-09-08 09:10 oldexternal
drwxrwxrwx 17 root root 32768 1969-12-31 18:00 wdpassport
paul@ubserver:/home/samba$ 

```

The wdpassport drive is the troublesome one.

I previously tried the chown command and got a lot of "operation not permitted" errors". I just tried again and got the same.

Here's my smb.conf file:
```
[global]
    ; General server settings
    netbios name = UBSERVER
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = paul
    force group = paul
```

---

### Post by dmizer on 2008-09-14
If you got "opperation not permitted" when using sudo, then you have larger issues than just samba shares.

Try:
```
sudo su
```
see if you can get a root prompt that way. Then try chmod again. If that doesn't work, you'll have to solve your sudoers problem first.

---

### Post by trashjunkid on 2008-09-15
The sudo su command works fine.

I should have clarified: the chown command caused errors when the drive is mounted. With the drive unmounted, the chown command proceeds without incident. Only when the drive with the permission problems is mounted are there errors.

Thanks,
Trashjunkid

---

### Post by trashjunkid on 2008-09-27
Does anyone have any further suggestions?

-Trashjunkid

---

