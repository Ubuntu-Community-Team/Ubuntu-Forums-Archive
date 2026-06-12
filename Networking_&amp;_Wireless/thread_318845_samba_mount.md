---
title: "samba mount"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by mudlark on 2006-12-14
My nachine wont allow amount command. I'm running dapper 192.168.0.109 is a network disc that has previously worked well


An error occurred while enabling /media/share.
The system reported: timeout connecting to 192.168.0.109:445
timeout connecting to 192.168.0.109:139
Error connecting to 192.168.0.109 (Operation already in progress)
5221: Connection to 192.168.0.109 failed
SMB connection failed

Any ideas please?
Ta,
Mike.

---

### Post by wieman01 on 2006-12-14
Have you got IP Tables up? Possibly through "firestarter"?

---

### Post by mudlark on 2006-12-14
you'll have to lead me through that.
Mike.

---

### Post by mudlark on 2006-12-14
Ok I have firestarter installed 
any help...
M.

---

### Post by wieman01 on 2006-12-14
No, the point was whether you have it running. If yes, please uninstall it. It will block all traffic. I just wanted to make sure you had turned it off. 

Are both SAMBA server & client Ubuntu machines?

---

### Post by mudlark on 2006-12-15
firestarter gone!

---

### Post by mudlark on 2006-12-15
samba is on kubuntu. the other box is a linkstation which runs a webbased managemnt programme which is largely inaccessible. The system has run well for a while and nothing was changed in the linkstation. it can only be wiring on the lan or software on the kubuntu box. The linkstation is accessible from my windows machine.
thanks in  hope. M.

---

### Post by mudlark on 2006-12-15
I've just found this entry in Fstab this has been created by a progarmme that i have started by mistake.

\134\134//192.168.0.109/share /media/share smbfs defaults,uid=1000,gid=1000,auto,rw,users,credentials=/etc/fstab_smb_credentials_1 0 0

Any igeas how I've done this?
as before, help.
M

---

### Post by Iowan on 2006-12-15
I've no idea how it occurred, but it would appear that **/etc/fstab** needs to have that line edited to get rid of the **\134\134**.

---

### Post by mudlark on 2006-12-15
I've done that, and still no nearer undersstanding things

---

### Post by mudlark on 2006-12-15
i give up ... i've booted from my ubuntu disc and I can browse the files on the remote drive. ??

---

### Post by wieman01 on 2006-12-15
Ok, first of all, please five us the IP address of the computer that is running the server, and the one that is trying to access the SAMBA server.

Then have you enabled folder sharing on the server? Have you used a GUI for that or edited SAMBA by command line?

Try to access the server this way using NAUTILUS:
> smb://192.168.0.109/
This is the SAMBA URL and you should be able to see the shared folders now. Any success?

_**EDIT:**_
Please make sure your firewall is down... i.e. Firestarter uninstalled.

---

### Post by mudlark on 2006-12-16
thanks folks, but i think i have sorted the problem at some cost. But by god I've learnt alot. Right, here is the tale. I recently upgraded and many files appeared, it was after this that problems occurred. I reinstalled kubuntu and it worked. The browser Konquerer works. Upgraded and it stopped working. Reinstalled and then I looked carefully at the Adept headings the FULL UPGRADE button was active. I used this button rather than upgrade and the browser still works. My previous upgrade must ahve broken something or other. I haven't tried using Nautilus, but as the remote machines all now appear in the mshome workgroup all should be well. I've only got to remount the remote files and I'll be up and running again after putting in slimserver etc.

Thanks for the support. If I find my diagnosis is wrong I'll post my findings. Perhaps this experience might also help other dopes!!
Cheers,
Mike.

---

### Post by mudlark on 2006-12-16
Ok Folks,
I'm still having numpty issues i get the following:-

mike@mike-desktop:~$ sudo mount -t smbfs //192.168.0.109/share /media/share -o username=mike
Password:
mount: wrong fs type, bad option, bad superblock on //192.168.0.109/share,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Can someone tell me what i am doing wrong.
Cheers,
Mike.

---

### Post by mudlark on 2006-12-16
OK I have now sorted this.
I ran
sudo apt-get install smbfs
and it all works.

please have a luaugh at my expense.
regards to all
M.

---

### Post by mudlark on 2006-12-17
I'm not sure that my problems were due to a broken upgrade. Currently everything working. but I don't know why....

sorry folks,
M.

---

### Post by Iowan on 2006-12-19
> **mudlark said:**
> Currently everything working. but I don't know why....

Working is a ***good*** thing - no apologies necessary...

---

### Post by cthippo on 2006-12-19
I've got a simlar issue to Mudlark's

  Here's the short version...

  ```
cthippo@cthippo-POCV:~$ sudo apt-get install smbfs
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  smbfs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 448kB of archives.
After unpacking 1085kB of additional disk space will be used.
Get:1 http://security.ubuntu.com dapper-security/main smbfs 3.0.22-1ubuntu3.1 [448kB]
Fetched 448kB in 2s (204kB/s)
Selecting previously deselected package smbfs.
(Reading database ... 79749 files and directories currently installed.)
Unpacking smbfs (from .../smbfs_3.0.22-1ubuntu3.1_amd64.deb) ...
Setting up smbfs (3.0.22-1ubuntu3.1) ...
cthippo@cthippo-POCV:~$ sudo mount -t smbfs //fileserver/D/ /mnt/I/
2587: Connection to fileserver failed
SMB connection failed
cthippo@cthippo-POCV:~$
```

  The folder is accessable by entereing smb://fileserv/D/

  Now what?

---

### Post by eoinmadden on 2007-01-18
> **mudlark said:**
> OK I have now sorted this.
I ran
sudo apt-get install smbfs
and it all works.

please have a luaugh at my expense.
regards to all
You won't find me laughing.. I had the same problem!

---

