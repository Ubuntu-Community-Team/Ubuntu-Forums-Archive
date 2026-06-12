---
title: "Linkstation NAS"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by gpeck157 on 2007-02-12
Hi All,

I have a Buffalo Linkstation external hard drive. It is attached to my Linksys router (WRT54G) via cat 5. I have put my mp3s on the drive under the folder "dad/Music" and would like to access my mp3s in Amarok. To play the files in Amarok the folder on the Linkstation must be mounted to my Dapper machine (wireless laptop). I created a folder on my laptop "media/mp3". I used the command "sudo mount //mediumls/dad/Music /media/mp3". (Mediumls is the sharename for the linkstation). I get a request for a password and since there is none for the linkstation I hit enter. I then get this result: "5867: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed"

Where am I going wrong?

Thanks,
Glen

---

### Post by casaschi on 2007-02-12
I have the linkstation setup as well, a bit slow, but works fine.

I think the issue is that:

1) you need to make sure that the samba names on the linkstation is copied correctly in the mount command. The "smbtree" command will show you the valid share names in your network. The sharename is usually a single name, not the full path.

2) you might need to specify that you mount a samba share, eventually with username and passowrd if you did set one.
So your fstab line should look like:

//mediumis/sharename /media/mp3 smbfs  _netdev,username=xxx,passowrd=yyy 0 0 

or something like that...

-- Paolo

---

### Post by gpeck157 on 2007-02-13
Hi Paolo,

Here are the results of the smbtree command.

FREEBIRD
     
        \\MEDIUMLS                      LinkStation
                \\MEDIUMLS\christina            christina
                \\MEDIUMLS\mom                  mom
                \\MEDIUMLS\pat                  pat
                \\MEDIUMLS\dad                  dad
                \\MEDIUMLS\info                 LinkStation information
                \\MEDIUMLS\lp                   Network Printer for Windows
        \\DAD                           Dad server (Samba, Ubuntu)
                \\DAD\psc_2500          psc_2500
                \\DAD\psc_2500_fax      psc_2500_fax
                \\DAD\ADMIN$            IPC Service (Dad server (Samba, Ubuntu))                        \\DAD\IPC$              IPC Service (Dad server (Samba, Ubuntu))               
     \\DAD\Pictures
                \\DAD\Music
                \\DAD\Documents
                \\DAD\print$            Printer Drivers

Here is my fstab file: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser,data=writeback 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hda1 	/windows 	ntfs 	nls=utf8,umask=0222 	0 	0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Are you saying I should write this to my fstab file?

//mediumls/dad/Music /media/mp3 smbfs _netdev,username=xxx,passowrd=yyy 0 0 

Thanks in advance, I appreciate the help.

Glen

---

### Post by gpeck157 on 2007-02-14
> **casaschi said:**
> I have the linkstation setup as well, a bit slow, but works fine.

I think the issue is that:

1) you need to make sure that the samba names on the linkstation is copied correctly in the mount command. The "smbtree" command will show you the valid share names in your network. The sharename is usually a single name, not the full path.

2) you might need to specify that you mount a samba share, eventually with username and passowrd if you did set one.
So your fstab line should look like:

//mediumis/sharename /media/mp3 smbfs  _netdev,username=xxx,passowrd=yyy 0 0 

or something like that...

-- Paolo

Hey Paolo, I found a good reference for this, and I was able to mount the share on the Linkstation NAS with no problem and it's now working great. The link is [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

Now the only"problem" (and it's not really a problem but more of an annoyance) the link for the share automatically shows up on my desktop. Any ideas there?

Thanks,

Glen

---

### Post by casaschi on 2007-02-19
If you changed your fstab, the filesystem should be mounted automatically at boot whenever a network connection is available.
If you like, you could just create a symbolic link to /media/mp3 on your Desktop...

---

### Post by dbmnk on 2007-04-25
doh! please disregard this message (I carnt read, apparently)

---

