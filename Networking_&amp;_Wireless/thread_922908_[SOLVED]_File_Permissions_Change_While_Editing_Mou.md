---
title: "[SOLVED] File Permissions Change While Editing Mounted Share???"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by flying_fish on 2008-09-17
Have an Ubuntu box mounted to a Server 2003 share.  When a file on the mounted share is edited, it can be saved (written) one time only.  One time only because the file permissions miraculously change.  Does anybody know why the permissions change?  How can I stop this?  Details by example follow.

The file system is mounted with this entry in the fstab:
//192.168.1.251/cnt	/home/tyler/cnt	cifs	credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

The results of an ls -lsrt after mounting the share cnt but before editing the file demo_f1:
0 -rwxrwxrwx 1 root root 0 2008-09-17 17:17 demo_f1
0 -rwxrwxrwx 1 root root 0 2008-09-17 17:17 demo_f2
tyler@tyler-laptop:~/cnt$ 

The results of an ls -lsrt after invoking emacs on on the file demo_f1 and saving once:  
0 -rwxrwxrwx 1 root root 0 2008-09-17 17:17 demo_f2
1 -rw-r--r-- 1 root root 6 2008-09-17 17:21 demo_f1
tyler@tyler-laptop:~/cnt$

Note that the permissions for the file demo_f1 have changed.

Thanks for your time....****

---

### Post by flying_fish on 2008-09-18
I continue to have general permissions issues.

I have a server 2003 smb share mounted to ubuntu.  Even when I copy files to a dir, some files copy take then a dialog boxed indicates there are permission issues.

I've just noticed that if I create a new dir within Nautilus, the owner reported by server 2003 is tsmith; This is correct as user=tsmith was an argument to the mount command.  However, the owner for this new dir reported by Nautilus and ls -ls is root, not the user I am logged in as on the ubuntu box.  Are there permission issues due to permission differences between root and the user I am logged in as?

---

### Post by flying_fish on 2008-09-19
I have found a way to mount a server 2003 share without the previously posted permissions issues.  The method of mount is not so elegant but maybe later....

The end result is a gvfs mount that appears as the following in a terminal window, "tyler@tyler-laptop:~/.gvfs/cnt on trinity$".  Not so elegant is that I get the mount by mousing through Nautilus for which I will break into steps:
1.  Toggle for text based location bar.
2.  Places->Network (Location: network:///)
3.  Places->Network->TRINITY (Location: smb://trinity/)
    O items are listed.  A known bug.
4.  append share name by typing in the location dialog (in my case "cnt<enter>". This results in Location: smb://trinity/cnt.  A dialog box for pc user and password will appear.

Anyway, not so elegant but it works.  Can this gvfs mount be done from the command line?

---

### Post by bab1 on 2008-09-19
The permissions change because you havn't setup the smb.conf file.  The defaults do not preserve ownership or create permissions.  To force the ownership of a file use "force user".  To set the permissions you want use "create mask".

See:[http://samba.org/samba/docs/using_samba/ch06.html]("http://samba.org/samba/docs/using_samba/ch06.html")

The gvfs methods are indeed for the GUI only.  The information is stored at /var/lib/samba.  None of the info shows up in the smb.conf file.

---

### Post by flying_fish on 2008-09-24
Warning...I am one of the newbees](*,)

Bab, thanks for the reply.  I am finding that there are numerous issues with Hardy-Natulis and windows shares.  This centers around Hardy being the first distribution using gnome-vfs.

Does Nautilis or even mount use smb.conf?  Samba does, but I am not running a Samba server, just browsing and mounting windows shares from Hardy-Natilus.

One remaining issue is that Hardy-OpenOffice does not open files on a Hardy-Natilus share.  Have read that OpenOffice does not suport gnome-vfs.  Unfortunately I have not found a way around this except to copy the file local:confused:

One way around these pesky Hardy-Natulis gnome-vfs windows share issues is to run kubuntu which does not use gnome-vfs.  My choice has been to stick with ubuntu and hope for problem solving updates that come sooner than later.

---

### Post by flying_fish on 2008-09-26
There are a multitude of problems accessing MS files shares from Hardy.  This is centered around, the new to Hardy, gnome-vfs.  One way out is to move to kubuntu.  I suppose these issues will be solved over timne but who knows when??

---

