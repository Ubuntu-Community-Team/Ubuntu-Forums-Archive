---
title: "[SOLVED] How to mount permanent Windows share using Samba"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by sidprak on 2007-05-18
I can view the files using the file manager by:
smb://username@server/share

But, I would like to know how to permanently mount the share.
I have tried these and they were unsuccessful:
http://ubuntuforums.org/showthread.php?t=12306
and adding a new line to the /etc/fstab

---

### Post by n8bounds on 2007-05-18
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

it might have only failed because you have not installed smbfs...

---

### Post by sidprak on 2007-05-19
how do i install it??
thanks

I tried the method in the above link and:
when i used mount -t smbfs ... it displayed usage instructions
when i used smbmount it said "command not found"

---

### Post by n8bounds on 2007-05-19
sudo aptitude install smbfs -y

:)

---

### Post by sidprak on 2007-05-22
Thanks!! It worked!


I also tried sharing files from the Ubuntu computer to my Windows computer
It asks for a password and user name when i try to access the ubuntu computer.
I tried both the users and the root account on my computer, but they dont work.
Can you please tell me what is wrong?

---

### Post by n8bounds on 2007-05-22
sure, do this:

sudo gedit /etc/samba/smb.conf

here's mine:
```


[global]
    ; General server settings
    netbios name = N8ZLAPPY
    server string = 
    workgroup = UBUNTUNET
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

#[print$]
#    path = /var/lib/samba/printers
#    browseable = yes
#    guest ok = yes
#    read only = yes
#    write list = root
#    create mask = 0664
#    directory mask = 0775

#[printers]
#    path = /tmp
#    printable = yes
#    guest ok = yes
#    browseable = no


[sharefolder]
    path = /home/nathan/sharefolder
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = nathan
    force group = nathan


```

the last bit there defines a single share and makes it so everyone has read/write without asking for creds, be careful tho, as this is obviously unsecure

I took samba out of my init scripts and only say

sudo /etc/init.d/samba start

to start it when I need it and then quickly say 

sudo /etc/init.d/samba stop

when I'm done, not secure that way either, but it gets the job done

taylor your file against my example, the sharefolder has to exist, smbd won't make it FOR you

oh yeah, once you have the file like you want it, save it and then say

sudo /etc/init.d/samba restart

that will reload your config file

have fun!

---

