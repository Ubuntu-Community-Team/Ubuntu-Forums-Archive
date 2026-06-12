---
title: "Unable to access Lubuntu shares from Windows or Android"
date: 2017-02-17
forum: Networking &amp; Wireless
---

### Post by ianmanning on 2017-02-17
I've installed Lubuntu 16.10 for use as a file server in a SoHo setup. I've installed Samba, and defined each share in /etc/samba/samba.conf like this:

[DriveA2Tb]
comment = DriveA2Tb
path = /media/myusername/DriveA2Tb
browseable = yes
read only = no
guest ok = yes
force user = myusername

My mounts are defined in /etc/fstab in this way:
#device        mountpoint             fstype    options  dump   fsck
/dev/sdb1    /media/myusername/DriveA2Tb ext4    defaults    0    1


When I attempt to access the Lubuntu server using Windows Explorer in Windows 10 or Windows 2008 Server, or ES File Explorer on Android, using the correct login credentials for myusername, the login credentials are rejected. 

Any ideas?

---

### Post by ianmanning on 2017-02-17
Just to add further info - if I try accessing the share from a Windows 10 command line this is the response:

net use p: \\192.168.1.251\[COLOR=#000000]DriveA2Tb[/COLOR] /USER:[COLOR=#000000]myusername[/COLOR]
Enter the password for '[COLOR=#000000]myusername[/COLOR]' to connect to '192.168.1.251':
System error 86 has occurred.


The specified network password is not correct.

---

### Post by Morbius1 on 2017-02-17
> using the correct login credentials for myusername, the login credentials are rejected. 
THe "login credentials" of the Lubuntu user or the samba "login credentials" for the Lubuntu user?

Unlike Windows where one is the same as the other in Linux it is not. So you need to add "[COLOR=#000000]myusername" to the samba password database:
```
sudo smbpasswd -a myusername
```

BTW, You really should have chosen a mount point that does not go under /media/myusername since only one user can get beyond that point and that's myusername. This would have been better: 
[/COLOR]```
 /dev/sdb1    /media/DriveA2Tb ext4    defaults    0    1
```

---

### Post by ianmanning on 2017-02-17
> **Morbius1 said:**
> THe "login credentials" of the Lubuntu user or the samba "login credentials" for the Lubuntu user?

Unlike Windows where one is the same as the other in Linux it is not. So you need to add "[COLOR=#000000]myusername" to the samba password database:
```
sudo smbpasswd -a myusername
```

BTW, You really should have chosen a mount point that does not go under /media/myusername since only one user can get beyond that point and that's myusername. This would have been better: 
[/COLOR]```
 /dev/sdb1    /media/DriveA2Tb ext4    defaults    0    1
```

I was indeed (mis)using the Lubuntu user as the samba login. I've followed your advice and all is well now.
Many thanks

---

