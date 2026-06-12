---
title: "Fstab"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by PaulClarke on 2008-08-24
Hello,

I thought I submitted this this morning but cannot see it

I am moving from Fedora and have a mixed linux and windows workgroup.  A ubuntu machine has all the shared files on it and I want to mount the shared drive and a selected folder.  The FSTAB from below is from Fedora and works perfectly on F9 but does not on Ubuntu.

UUID=6836ac2d-45c0-4528-b94a-3c308083b8e9 /                       ext3    defaults        1 1
UUID=49b020eb-13c0-4ab0-b4e8-3e4563b6846c /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
//192.168.0.112/fserver/moneydance	/home/paul/moneydance	cifs	rw,uid=000,auto,defaults,password="",workgroup=workgroup	0 0
//192.168.0.112/fserver		/home/paul/server	cifs	rw,uid=000,auto,defaults,password="",workgroup=workgroup	0 0
UUID=85643ab8-4410-44df-9f72-8204c7edbff0 swap                    swap    defaults        0 0

Any ideas?

Paul

---

### Post by PaulClarke on 2008-08-24
oh by the way (and this may assist) when I try to manually try to mount the following occurrs

paul@paul-ubuntu:~$ sudo mount -t cifs //192.168.0.112/fserver /home/paul/server/ cifs -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo: unable to resolve host paul-ubuntu


Paul

---

### Post by Iowan on 2008-08-24
I'm a li'l more brain-dead than usual this morning, but...
What's  in your **/etc/hosts** file?

---

### Post by PaulClarke on 2008-08-24
Thank you for your response,

Here is the host file

127.0.0.1 localhost
127.0.1.1 paul-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I have edited it (after my post) as it had
 
127.0.1.1 paul-ubuntu.workgroup

but neither seem to work and with both the network is available but the fstab will not mount the samba shares.  With the "workgroup" missing the "host" error disappeared but the shares with still no mount either using fstab or a terminal mount command



Thank you again

Paul

---

### Post by Iowan on 2008-08-24
You could have both names in the **hosts** file:```
127.0.1.1 paul-ubuntu.workgroup paul-ubuntu
``` [Here]("http://ubuntuforums.org/showthread.php?t=288534") is a good How-To on mounting CIFS shares.

---

### Post by PaulClarke on 2008-08-25
Hello,

Thank you again for your reply.

I will try it.

Does the fstab file look correct to you?

Regards

Paul

---

### Post by PaulClarke on 2008-08-25
Hello,

Tried that - did not work

Thank you for your efforts

Paul

---

### Post by PaulClarke on 2008-08-26
Hello,

I have done more work on this and the following is the result of using the mount command

sudo: unable to resolve host paul-ubuntu
mount: sysfs already mounted or /sys busy
mount: according to mtab, /sys is already mounted on /sys
mount: special device //192.168.0.112/fserver/moneydance does not exist
mount: special device //192.168.0.112/fserver does not exist


Does this help is solving my problem.

Paul

---

### Post by PaulClarke on 2008-08-28
Hello,

I'm going to give this one more effort and then give up.

I have attempted to mount these shares on an old ubuntu loaded laptop and that was successful.  After the success with Fedora I can conclude that whatever my problem is is with the Ubuntu desktop.

Does anyone have any idea why the FSTAB and mount command cannot see the shares on the other Ubuntu PC when Fedora and the Ubuntu laptop both mount them successfully?

Thank you

Paul

---

### Post by PaulClarke on 2008-08-30
Hello,

If anyone does consider responding to this thread please don't bother.  I have returned to Fedora.  I will reinstall Ubuntu when I have some more time and see if I can figure this out or see if was just that installation

Bye for now

Paul

---

