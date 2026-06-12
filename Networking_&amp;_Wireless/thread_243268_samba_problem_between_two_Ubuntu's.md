---
title: "samba problem between two Ubuntu's"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by RyanGT on 2006-08-24
I am trying to share files between my laptop running Ubuntu Breezy and my desktop running Dapper.  They are connected via a router.  I am using samba.

When I search for samba folders on the laptop from the desktop I get:
ryan@ubuntu:~$ smbclient -L 192.168.0.101 Password:
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        Ubuntu_mp3      Disk
        thesis          Disk
        IPC$            IPC       IPC Service (ubuntu server (Samba, Ubuntu))
        ADMIN$          IPC       IPC Service (ubuntu server (Samba, Ubuntu))
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Server               Comment
        ---------            -------
        UBUNTU               ubuntu server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        MSHOME


I would like to copy over the contents of the thesis folder, so this looks good so far.  I try to mount the folder using

ryan@ubuntu:~$ sudo mount -t smbfs -o username=ryan //192.168.0.101/thesis remote_thesis/

and this appears to work, but then I can't cd into the folder and when I type ls -al I get

...
-rw-------  1 ryan ryan   3131 2006-08-23 09:49 .recently-used
?---------  ? ?    ?         ?                ? remote_thesis
-rw-r--r--  1 ryan ryan      0 2006-08-02 16:55 .sudo_as_admin_successful
...

What am I doing wrong?

Thanks,

Ryan

---

### Post by GTvulse on 2006-08-25
[quote="RyanGT"]What am I doing wrong?[/quote]

Using samba instead of NFS.

Samba is a ncessary evil when you have a bunch of MS Windows clients to network, but it is complicated and prone to break when you don't know exactly what you are doing (and that happens even more frequently with the vendors propietary implementation). NFS on the other hand is the natural filesharing protocol in the world of POSIX OSs.  (Hint: use nfs-kernel-server, the GNOME netowrking tool will install it for you, or install by hand). Both can co-exist in case yo need it so; they are vey different protocols.

---

### Post by Iowan on 2006-08-25
Mount point?  Knowing just enough to be dangerous, I'm wondering if **remote_thesis/** is adequate.  **./remote_thesis/**???

---

