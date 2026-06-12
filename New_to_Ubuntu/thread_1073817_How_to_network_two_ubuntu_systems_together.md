---
title: "How to network two ubuntu systems together?"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by trooperchix on 2009-02-18
My better half and I have laptops.  I am attempting to connect the two wirelessly so we can share files.  I've been all over trying to figure this out, but I have yet to find anything that makes sense to a noob.  

I run Intrepid, she runs Hardy.

Help!

---

### Post by diablo75 on 2009-02-18
Create a folder that you want to share with the other computer.

Right-click on it and hit "Sharing..."

It will probably prompt you to install something Samba related; install it.

Once that's done, restart the PC.  Then right click on that folder again, hit Sharing... again, and enable sharing and guest access.  You might have to restart one more time before the changes will take effect, but this should work...

---

### Post by wolfen69 on 2009-02-18
[This]("http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Filesharing") may help.

---

### Post by trooperchix on 2009-02-18
*bump*

---

### Post by Gramps on 2009-02-18
Install NFS Server Support
at the terminal type
sudo apt-get install nfs-kernel-server nfs-common portmap
When configuring portmap do =not= bind loopback. If you do you can either edit /etc/default/portmap by hand or run:
sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap restart

Editing /etc/exports
the /etc/exports file is used for creating a share on the NFS server

invoke your favorite text editor or
sudo vi /etc/exports

Here are some quick examples of what you could add to your /etc/exports

For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255

* /files 192.168.1.0/24(rw,no_root_squash,async)


Or for Read Only from a single machine

* /files 192.168.1.2 (ro,async)

save this file and then in a terminal type
sudo /etc/init.d/nfs-kernel-server restart

Also aftter making changes to /etc/exports in a terminal you must type
sudo exportfs -a

Install NFS client support
sudo apt-get install portmap nfs-common

Mounting manually
Example to mount server.mydomain.com:/files to /files. In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server

The mount point /files must first exist on the client machine.
cd /
sudo mkdir files

to mount the share from a terminal type

sudo mount server.mydomain.com:/files /files

Note you may need to restart above services:
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart

Mounting at boot using /etc/fstab
Invoke the text editor using your favorite editor, or
gksudo gedit /etc/fstab

In this example my /etc/fstab was like this:

* server.mydomain.com:/files /files nfs rsize=8192,wsize=8192,timeo=14,intr

You could copy and paste my line, and change “servername.mydomain.com:/files”, and “/files” to match your server name:share name, and the name of the mount point you created.
It is a good idea to test this before a reboot in case a mistake was made.
type
mount /files
in a terminal, and the mount point /files will be mounted from the server.

---

### Post by stchman on 2009-02-18
> **Gramps said:**
> Install NFS Server Support
at the terminal type
sudo apt-get install nfs-kernel-server nfs-common portmap
When configuring portmap do =not= bind loopback. If you do you can either edit /etc/default/portmap by hand or run:
sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap restart

Editing /etc/exports
the /etc/exports file is used for creating a share on the NFS server

invoke your favorite text editor or
sudo vi /etc/exports

Here are some quick examples of what you could add to your /etc/exports

For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255

* /files 192.168.1.0/24(rw,no_root_squash,async)


Or for Read Only from a single machine

* /files 192.168.1.2 (ro,async)

save this file and then in a terminal type
sudo /etc/init.d/nfs-kernel-server restart

Also aftter making changes to /etc/exports in a terminal you must type
sudo exportfs -a

Install NFS client support
sudo apt-get install portmap nfs-common

Mounting manually
Example to mount server.mydomain.com:/files to /files. In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server

The mount point /files must first exist on the client machine.
cd /
sudo mkdir files

to mount the share from a terminal type

sudo mount server.mydomain.com:/files /files

Note you may need to restart above services:
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart

Mounting at boot using /etc/fstab
Invoke the text editor using your favorite editor, or
gksudo gedit /etc/fstab

In this example my /etc/fstab was like this:

* server.mydomain.com:/files /files nfs rsize=8192,wsize=8192,timeo=14,intr

You could copy and paste my line, and change “servername.mydomain.com:/files”, and “/files” to match your server name:share name, and the name of the mount point you created.
It is a good idea to test this before a reboot in case a mistake was made.
type
mount /files
in a terminal, and the mount point /files will be mounted from the server.

Nice post, I have tried the fstab option to network my Ubuntu PCs.

Only problem is that if one of the PCs shuts off the other one still thinks it is connected to the share.  If you click on the share Ubuntu will try forever to connect to that share.  Is there some way to make Ubuntu try for say 10 secs and then give up?

The fstab way works well for a server.

Thanks.

---

### Post by Gramps on 2009-02-18
> **stchman said:**
> Nice post, I have tried the fstab option to network my Ubuntu PCs.

Only problem is that if one of the PCs shuts off the other one still thinks it is connected to the share.  If you click on the share Ubuntu will try forever to connect to that share.  Is there some way to make Ubuntu try for say 10 secs and then give up?

The fstab way works well for a server.

Thanks.

[This might help......]("http://www.faqs.org/docs/linux_network/x-087-2-nfs.mountd.html")

---

### Post by cjv8888 on 2009-02-18
> **trooperchix said:**
> My better half and I have laptops.  I am attempting to connect the two wirelessly so we can share files.  I've been all over trying to figure this out, but I have yet to find anything that makes sense to a noob.  

I run Intrepid, she runs Hardy.

Help!

```
sudo apt-get install openssh-server
```
in both machines

---

### Post by Herman on 2009-02-18
I hope this link will help someone:  [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm")  Linux Home Networking... secure... user friendly... GUI...set up in minutes..!
Regards, Herman :D

---

### Post by jimrz on 2009-02-18
big +1 for open-ssh

---

### Post by stchman on 2009-02-19
> **Gramps said:**
> [This might help......]("http://www.faqs.org/docs/linux_network/x-087-2-nfs.mountd.html")

I used the "soft" option in the fstab mount line and when a network conmection terminates it tries for about 10 seconds and gives up.

---

### Post by Gramps on 2009-02-19
NFS automount is an easy way to mount your NFS drives when you need them without you having to do anything except clicking on the directory you want to access. In a nutshell here is what you need to do

Automount (autofs)
You can use autofs to automaticlly mount your NFS shares when you click om the directory by using autofs.
From terminal on the client sudo apt-get install autofs nothing needs to be done, make sure that you can manually mount the directory before preceeding.


server:/etc/exports
Code:

/files 192.168.0.0/24(rw,async)

client:/etc/auto.master
Code:

/mnt/nfsmount /etc/auto.nfsmnt --ghost

client:/etc/auto.nfsmnt
Code:

files 192.168.0.99:/files

the directory /files in the server is automatically mounted to /mnt/nfsmount/files in the client. /mnt/nfsmount should be existing in the client.

When you click on the directory on the client the NFS directory will be automounted and then when it hasn't been used for 5 minutes (default) it will be umounted til it is accessed again. 

Information taken from [Setting Up NFS How To:]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

