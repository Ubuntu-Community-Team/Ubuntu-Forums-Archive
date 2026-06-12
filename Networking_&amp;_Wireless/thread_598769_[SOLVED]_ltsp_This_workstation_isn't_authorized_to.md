---
title: "[SOLVED] ltsp This workstation isn't authorized to connect to server"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by SpiritIsReality on 2007-10-31
howdy
ltsp This workstation isn't authorized to connect to server
----------
[http://www.google.ca/search?hl=en&q=%22This+workstation+isn%27t+authorized+to+connect+to+server%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=%22This+workstation+isn%27t+authorized+to+connect+to+server%22&btnG=Google+Search&meta=)

[https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/144296](https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/144296)
... 
 bazz wrote on 2007-09-24: (permalink)

I forgot....I didnt post that "This workstation isn't authorized to connect to server" as a bug because I dont know as if it would be one. I looks to me as if its a control that would need to be set up.

 Oliver Grawert wrote on 2007-09-24: (permalink)

to get rid of that message, run sudo ltsp-update-sshkeys and sudo ltsp-update-image (in this order) it should be gone then
-----
ran 
sudo ltsp-update-sshkeys
sudo ltsp-update-image

fred@piii:~$ sudo ltsp-update-sshkeys
[sudo] password for fred:
fred@piii:~$ sudo ltsp-update-image
Parallel mksquashfs: Using 1 processor
Creating little endian 3.0 filesystem on /opt/ltsp/images/i386.img.tmp, block size 65536.
[==========================================================  ] 19490/19887  98%
Exportable Little endian filesystem, data block size 65536, compressed data, compressed metadata, compressed fragments, duplicates are removed
Filesystem size 160809.37 Kbytes (157.04 Mbytes)
        42.38% of uncompressed filesystem size (379444.06 Kbytes)
Inode table size 201623 bytes (196.90 Kbytes)
        32.76% of uncompressed inode table size (615367 bytes)
Directory table size 177545 bytes (173.38 Kbytes)
        53.63% of uncompressed directory table size (331055 bytes)
Number of duplicate files found 1117
Number of inodes 18679
Number of files 15609
Number of fragments 1907
Number of symbolic links  996
Number of device nodes 86
Number of fifo nodes 2
Number of socket nodes 0
Number of directories 1986
Number of uids 5
        root (0)
        syslog (101)
        fred (1000)
        news (9)
        klog (102)
Number of gids 15
        video (44)
        audio (29)
        tty (5)
        kmem (15)
        disk (6)
        adm (4)
        shadow (42)
        dhcp (101)
        fuse (106)
        utmp (43)
        staff (50)
        src (40)
        mail (8)
        fred (1000)
        klog (103)
Info: port 2000 is already defined with /opt/ltsp/images/i386.img in inetd.conf
Info: taking no action.
fred@piii:~$ 

user fred
passwd ******
login to server from ltsp client successful.

user user1
passwd ********
passwd fails

possible reason is the user1 was added by
chroot /opt/ltsp/i386 
# adduser user1
_________________

added user2 to server's root

System -> Administration -> Users and Groups 

+Add User

user user2
passwd *******
login to server from ltsp client successful.
________________________________________________________

[http://ubuntuforums.org/showthread.php?t=570292](http://ubuntuforums.org/showthread.php?t=570292)


___________________________________

---

### Post by trainwalker on 2008-03-31
Thank you for that post.  I was able to use that information to get my Thin Clients up and running now.  I just need to lock them down a little bit, any help from anyone would be grateful, I am not new to Linux, but I am used to stand-alone systems, this is my first foray into networking and thin clients.  So far I like it.

Thanks again.

---

### Post by ahmadzainul on 2008-04-27
I do ltsp-update-kernels and ltsp-update-images but Finally finished then booted client (ibm/lenovo x60 tablet) "[ 12.568000] intel_rng: FWH not detected" then it sits for about 5 mins and then it gets to the login... when i enter username and pass it says verifying password then after another 5 mins atleast it goes to a black screen with movable cursor. Been like this for over 10 mins now with no prospect of continuing. Looking at the /var/log/daemon.log it shows that 18 minutes ago it gave me the i386.img file and shows the file's size but nothing since then...

---

### Post by acesabe on 2008-05-06
OK - I'm using a 64bit server with a 32bit ltsp environment (as would most people using a 64bit server OS -I would have thought!)
running ltsp-update-image fails due to lack of /opt/ltsp/amd64/ folder - seems there is no way to specify this to update-image...??

---

### Post by acesabe on 2008-05-07
OK - problem solved - you need the **-a** appendage to specify architecture

$ **sudo ltsp-update-image -a i38**6  in my case

---

