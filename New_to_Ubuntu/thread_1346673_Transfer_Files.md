---
title: "Transfer Files"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by OwNeD on 2009-12-05
Hello. is it possible to transfer files  such as Movies/music etch from a ubuntu laptop to a windows laptop? the two machines are in the same house. if its possible,how can i do it?




Thanks!

---

### Post by bodhi.zazen on 2009-12-05
You can do this with Samba.

[Setting Up Samba - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by OwNeD on 2009-12-05
to transfer files between computers using samba,do both computers need to have samba?

---

### Post by SuperSonic4 on 2009-12-05
As far as I know only the Linux PC needs it

Personally I would say that it's easier to use external storage as a go-between

---

### Post by bodhi.zazen on 2009-12-05
The windows computer has file sharing installed by default, it is called shared folders.

The Linux computer has the samba client installed by default.

So you should be able to set a folder on the windows box as shared and mount (open it) from Ubuntu.

[http://www.home-network-help.com/simple-file-sharing.html](http://www.home-network-help.com/simple-file-sharing.html)

Then browse network places on Ubuntu and you should be able to mount the share.

---

### Post by lkraemer on 2009-12-05
Another option is to use vsftp.  Here is a very good HOWTO:
[http://ubuntuforums.org/showthread.php?t=518293](http://ubuntuforums.org/showthread.php?t=518293)

Install Filezilla on the Windows machine, and then connect through a 
switch/router with two patch cables, OR use a Crossover Ethernet Cable
connecting both computers.

Since you know both login_names and passwords you can just login and
start the transfers with Filezilla.

For the Ubuntu machine running vsftp (server) use these commands:
```
 
sudo /etc/init.d/vsftpd start
sudo /etc/init.d/vsftpd stop
sudo /etc/init.d/vsftpd restart

```
And remember that after vsftp is installed, it will be started every
boot, but you can disable it (turn off) with
SYSTEM -> ADMINISTRATION -> SERVICES

You will need to set each computer to a static IP address on your LAN
ie. 192.168.1.10  192.168.1.20 with 255.255.255.0
then reset to roaming when finished.

Since you are on a local LAN, without a connection to the internet,
you won't need to setup TLS/SSL/FTPS either.

Works wonderful! 

You can also assign users that are allowed to login, but you won't need
them.

lk

---

### Post by sandyd on 2009-12-05
heres the easiest way i know of.
first, find the workgroup of the windows computer (by default, its "WORKGROUP" (without quotes))
 
then install (in ubuntu) system-config-samba
 
press alt+f2 and in the thingy that pops up, type in 
```

gksudo system-config-samba
```
in the window that pops up, click on prefrences -> server settings. (or something close to that)
set your workgroup.
then go to permissions.
change the type to "share"
set the guest account as your username.
 
press ok.
 
then click on the "+" sign to set shared folders.
 
make sure you check the "visible" box.
and it should be "accessable to everybody"

---

