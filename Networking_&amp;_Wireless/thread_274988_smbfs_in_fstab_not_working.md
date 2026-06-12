---
title: "smbfs in fstab not working"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by Maagus on 2006-10-10
Hello,

I have problem with mounting windows shares on boot. Everything works OK (except r/w rights for normal user, of course) when mounted manually using this command :

```
sudo mount -t smbfs //magus/Filmy /mnt/share/Filmy
```

But when I add it in fstab it is not mounted :-k  My fstab is :

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /media/hda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
//magus/Filmy   /mnt/share/Filmy cifs   dmask=777,fmask=777   0       0

```

I have tried both, smbfs and cifs. Neither of it worked. I have tried also that shell script which adds delay for mounting shares but without success as well.
Browsing shares in nautilus works flawlessly, I can ping that computer with shares as well, I tried uninstalling VMWare player but none of these steps worked.
I will be glad for any idea :-)

---

### Post by Iowan on 2006-10-10
Follow the 3rd link in my signature.

---

### Post by Maagus on 2006-10-11
> **Iowan said:**
> Follow the 3rd link in my signature.

Thank you. I have tried changing permissions for smbmnt, symlinking, wrtiting line to fstab without specifiing r/w permissions but it still doesn't work ](*,) 
I have tried setting the path with IP address instead of hostname but still no sucess.
As I wrote in my previous post, manual mounting works but the same written in fstab doesn't :-k 
My network is set to DHCP but with MAC-based IP assigning so the IPs are still same. I am using network manager on my ubuntu system to manage interfaces. Could this be the cause of the problem ?

---

### Post by Maagus on 2006-10-11
OK, finally I found the solution in one of the threads here on ubuntuforums. 
This is working flawlessly.

```
//192.168.xxx.xxx/Filmy    /mnt/share/Filmy cifs  uid=1000,umask=777,iocharset=utf8  0    0
```

---

### Post by Iowan on 2006-10-11
Since you mention it - I had a similar problem setting up a network printer - it wouldn't work w/ name, but works fine with IP Address.

---

### Post by dannyboy79 on 2006-10-11
> **Maagus said:**
> OK, finally I found the solution in one of the threads here on ubuntuforums. 
This is working flawlessly.

```
//192.168.xxx.xxx/Filmy    /mnt/share/Filmy cifs  uid=1000,umask=777,iocharset=utf8  0    0
```

Thats exactly what I suspected. Many people get samba to work with ip but not by machine name. You really need to add all the ip addresses and the machine names within your /etc/hosts file and make sure that hosts is the first thing on the smb.conf line that says name resolution or something like that. The test before you should have been trying to add network shares to your fstab would have been could you ping by ip AND MACHINE NAME. Obviously you found out tht hard way you couldn't ping by MACHINE NAME which was the reason it wasn't working cause it couldn't find it? Also, it would have told you in either syslog or dmesg what the problem was with it failing mounting. Well I am glad you figured it out but to make it easier and especially if you are using dhcp you will wanna setup name resolution for your lan otherwise you fstab will fail again if you get a different ip from your router.

---

### Post by Maagus on 2006-10-11
> **dannyboy79 said:**
> Thats exactly what I suspected. Many people get samba to work with ip but not by machine name. You really need to add all the ip addresses and the machine names within your /etc/hosts file and make sure that hosts is the first thing on the smb.conf line that says name resolution or something like that. The test before you should have been trying to add network shares to your fstab would have been could you ping by ip AND MACHINE NAME. Obviously you found out tht hard way you couldn't ping by MACHINE NAME which was the reason it wasn't working cause it couldn't find it? Also, it would have told you in either syslog or dmesg what the problem was with it failing mounting. Well I am glad you figured it out but to make it easier and especially if you are using dhcp you will wanna setup name resolution for your lan otherwise you fstab will fail again if you get a different ip from your router.

Thank you for reply.

The problem wasn't in hostname, I have tried it using IP adress earlier. The only difference seems to be the syntax for r/w access for all users in combination with cifs (not smbfs).

Manual command mount -t smbfs..... worked OK but smbmount which I tried today gave me errors about permissions (I can´t recall the exact error message but something like "setuid must *NOT* be set to root" when using smbmount).

I am using MAC-based DHCP so it should be OK.

Strange thing is that when I was looking in dmesg why my previous mount attempts failed there was no log about mounting smbfs :-k

---

### Post by dannyboy79 on 2006-10-12
> **Maagus said:**
> Thank you for reply.

The problem wasn't in hostname, I have tried it using IP adress earlier. The only difference seems to be the syntax for r/w access for all users in combination with cifs (not smbfs).

Manual command mount -t smbfs..... worked OK but smbmount which I tried today gave me errors about permissions (I can´t recall the exact error message but something like "setuid must *NOT* be set to root" when using smbmount).

I am using MAC-based DHCP so it should be OK.

Strange thing is that when I was looking in dmesg why my previous mount attempts failed there was no log about mounting smbfs :-k

i have read that somewhere about smbmount, you can actually solve that by changing it using chmod I think. if you gogle it I am sure you'll find the answer. i found it for ya:

Another problem occurs when a non-root user tries to mount a Windows share using smbmount. To allow them to do it you need to setuid root the smbmnt command. Since smbmnt usually resides in /usr/bin, you can accomplish it with this command as root: 

chmod u+s /usr/bin/smbmnt

This will not work if you setuid the smbmount command. It is specifically written so that it won't execute if it is setuid root. 

To allow non-root users to unmount the shares, you need to setuid the smbumount command. Execute this as root: 

chmod u+s /usr/bin/smbumount

---

