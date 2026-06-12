---
title: "Windows machine cannot copy to share on 2nd HDD"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by fuzzybabybunny on 2006-12-07
First off, I'm a complete Linux noob. If you tell me to do something, more than likely I will have no idea how to do it.

This question pertains to Clark Connect, but the question should be similar enough that the answer is universal.

I have CC currently set up nicely as a router, but I also want it to file serve. The OS is on an 80GB HDD and I have another 160GB drive in there in ext3 format. I want to share the whole entire drive. In the smb.conf file, [shared] is one of the default shares that CC comes with, one that I can edit, copy, paste to, etc in Windows. So I decided to just mimic this with my [2C] share name. (2C is the new 160GB HDD with ext3 that I want to share) 2C pops up in Windows Explorer, but I still can't write to it. I get the message "Access is denied. Make sure the disk is not full or write protected and that the file is not currently in use."

Why the heck doesn't this work? [shared] and [2C] have exactly the same properties, but [2C] doesn't work while [shared] does?

Here's my smb.conf:

    > login as: root
    root@192.168.1.1's password:
    Last login: Thu Dec 7 01:51:39 2006
    [root@gateway ~]# :51:39 2:51:39 2
    [root@gateway ~]# vi /etc/samba/smb.conf
    # PDC
    #----

    add machine script = /usr/sbin/useradd -d /dev/null -g samba-clients -s /bin/false -M %u


    #============================ Share Definitions ==============================

    include = /etc/samba/flexshare.conf

    [printers]
    printing = cups
    path = /tmp
    browseable = yes
    printable = yes
    public = yes
    guest ok = yes

    [homes]
    read only = no
    browseable = no

    [shared]
    comment = Public Shared Folder
    path = /home/shared
    browseable = yes
    guest only = yes
    writable = yes
    public = yes

    [2C]
    comment = 2C Shared Drive
    path = /mnt/2C
    browseable = yes
    guest only = yes
    writable = yes
    public = yes

    [ftpsite]
    comment = Public FTP Server Folder
    path = /var/ftp
    browseable = yes
    guest only = yes
    writable = yes
    public = yes
    Include = /etc/samba/flexshare.conf



In fstab, I mounted my 160GB like the CC tells me to here: [http://ccfaq.valar.co.uk/modules.php?name=News&file=article&sid=12](http://ccfaq.valar.co.uk/modules.php?name=News&file=article&sid=12))

fstab:

    > [root@gateway ~]# vi /etc/fstab
    LABEL=/1 / ext3 defaults 1 1
    LABEL=/boot1 /boot ext3 defaults 1 2
    none /dev/pts devpts gid=5,mode=620 0 0
    none /dev/shm tmpfs defaults 0 0
    none /proc proc defaults 0 0
    none /sys sysfs defaults 0 0
    LABEL=SWAP-hda2 swap swap defaults 0 0
    /dev/hdb /mnt/2C ext3 auto 1 2 

---

### Post by Iowan on 2006-12-08
Can you access the 2C directory from the CC box?

---

