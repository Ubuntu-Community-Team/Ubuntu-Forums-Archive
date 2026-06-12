---
title: "Samba: Mounting windows share on linux (Ubuntu 12.04 LTS)"
date: 2014-05-19
forum: Networking &amp; Wireless
---

### Post by siddharthdangi on 2014-05-19
Hello there,

I have a Windows 7 machine (IP 192.168.137.1) and a Linux (Ubuntu 12.04 LTS) machine on my private network, and I'm trying to mount a shared folder ("test_folder") that's on my Windows machine, onto my Linux machine using samba.

I'm trying to follow the very simple instructions listed here:
[http://www.howtogeek.com/168115/mount-a-windows-shared-folder-on-linux-with-samba/](http://www.howtogeek.com/168115/mount-a-windows-shared-folder-on-linux-with-samba/)

On my linux machine, when I run smbclient (corresponding to step 2 in the link above -- Testing the Connection), I see the following:
$ smbclient -L 192.168.137.1/test_folder -U James
Enter James's password: 
Domain=[EECS] OS=[Windows 7 Professional 7601 Service Pack 1] Server=[Windows 7 Professional 6.1]

    Sharename       Type      Comment
    ---------       ----      -------
    ADMIN$          Disk      Remote Admin
    test_folder        Disk      
    C$              Disk      Default share
    IPC$            IPC       Remote IPC
    print$          Disk      Printer Drivers
    Q$              Disk      Default share
session request to 192.168.137.1 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

In other words, I do see the folder "test_folder" listed above, but I also see the errors seen above.
 
If I directly just trying mounting the folder with a command like:
$ sudo mount -t smbfs -o username=James,password=mypassword //192.168.137.1/test_folder /storage/test_folder

then I get the following error:
mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

Any idea what I could be down wrong, or how to troubleshoot? Any help is greatly appreciated!

Thanks,
James

---

### Post by bab1 on 2014-05-20
You are asking to list the all shares with smbclient -L.   When using smbclient with the L switch you only need the server name (e.g. smbclient -L 192.168.137.1).  

The line > NetBIOS over TCP disabled -- no workgroup available
 is a indicator of a problem.  Turn on NetBIOS over TCP (NBT) on the Windows host.

The tutorial is a bit old.  Smbfs is deprecated in favor of cifs.  Use cifs instead of smbfs in your mount command.

Not sure if this is all that is wrong but it is a starting point.

---

### Post by siddharthdangi on 2014-06-04
Thanks for the advice.  So I was able to mount the Windows share properly on one Ubuntu machine, but for some reason I can't replicate it on a second Ubuntu machine, and I don't know why. To get things working on the first Ubuntu machine, I had added the following line to the end of the /etc/fstab file:

//192.168.137.1/test_folder /storage/test_folder smbfs user=James,pass=mypassword,uid=1000,gid=1000 0 0

Then (after creating the directory /storage/test_folder), I could do "sudo mount /storage/test_folder" and it would mount the Windows share properly.

However, now when I try doing the exact same thing on another linux machine (also networked to the Windows machine via a switch), I get the following error when I run "sudo mount /storage/test_folder":

$ sudo mount /storage/test_folder
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

I have no idea why it works on the first Ubuntu machine but not the second one.  I can ping the Windows machine from the 2nd Ubuntu machine just fine.  Any ideas on what could be wrong, or how to troubleshoot?

Thanks.

---

### Post by siddharthdangi on 2014-06-04
Okay, I figured it out -- for some reason, in the /etc/fstab file on the second Ubuntu machine, I had to add the option "sec=ntlmssp":

//192.168.137.1/test_folder /storage/test_folder smbfs user=James,pass=mypassword,uid=1000,gid=1000,sec=ntmlssp 0 0

I'm not sure why this was needed on the second Ubuntu machine and not the first (both running 12.04 LTS, with basically identical setups/connections to the Windows machine), but in any case, this is what made it work.

(found this on: [http://ubuntuforums.org/showthread.php?t=1871142](http://ubuntuforums.org/showthread.php?t=1871142))

---

