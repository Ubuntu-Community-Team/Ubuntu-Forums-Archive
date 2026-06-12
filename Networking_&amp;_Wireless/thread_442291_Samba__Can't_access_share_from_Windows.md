---
title: "Samba:  Can't access share from Windows"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by oldtappan on 2007-05-13
I'm trying to share out a directory on my home network.   When a Windows XP client accesses \\myubuntuserver from Windows Explorer, the Share1 directory is visible along with the shared printer.  When I click on the Share1 directory to view the files, I get an error:
**\\myubuntuserver\Share1 is not accessible. You might not have permission to use this network resource.  No network provider accepted the given network path**

Here's my smb.conf.  Note that the files mounted at "/storage" are from a TrueCrypt volume residing on an external USB drive.  See [this thread]("http://ubuntuforums.org/showthread.php?t=442259") for more info.

Any idea how I can get this share to be accessible without security for read/write to anyone?

smb.conf: [relevant sections only]
[B]security = share

guest account = nobody
invalid users = root

[Share1]
path = /storage/Backups
available = yes
browsable = yes
public = yes
writable = yes
guest ok = yes
[/B]

---

### Post by cursebg on 2007-05-13
why dont you try to use the IP instead of "myubuntuserver" ?

---

### Post by oldtappan on 2007-05-13
> **cursebg said:**
> why dont you try to use the IP instead of "myubuntuserver" ?

It doesn't make a difference.  I still get the same error.  It's not a name resolution issue.  I probably screwed something up in my smb.conf

---

### Post by luckyaba on 2007-05-13
Type "smbpasswd" into a terminal without the quotes. Then just create a password for you user account. Then when you connect to the share just use your username and password to access it.

---

### Post by oldtappan on 2007-05-13
> **luckyaba said:**
> Type "smbpasswd" into a terminal without the quotes. Then just create a password for you user account. Then when you connect to the share just use your username and password to access it.

Ok, but how do I access the share without using any credentials?  Is that possible?

---

### Post by luckyaba on 2007-05-13
in your samba.conf file add the following

[global]
workgroup = yourworkgroupname
netbios name = yourcomputername
security = share

[Share1]
path = /storage/Backups
available = yes
writable = yes
guest ok = yes
browsable = yes

---

### Post by oldtappan on 2007-05-13
> **luckyaba said:**
> in your samba.conf file add the following

[global]
workgroup = yourworkgroupname
netbios name = yourcomputername
security = share

[Share1]
path = /storage/Backups
available = yes
writable = yes
guest ok = yes
browsable = yes

I replaced my smb.conf with your suggestions and I still get an error message (see first message) on Windows XP and a credentials prompt when accessing Share1 from Vista.

---

### Post by luckyaba on 2007-05-13
can you post your smb.conf?

---

### Post by oldtappan on 2007-05-13
> **luckyaba said:**
> can you post your smb.conf?

I simply replaced my smb.conf with yours, changing only workgroup and netbios name values.

-------------------------------------------------
[global]
workgroup = WORKGROUP
netbios name = myubuntuserver
security = share

[Share1]
path = /storage/Backups
available = yes
writable = yes
guest ok = yes
browsable = yes

---

### Post by b0ng0 on 2007-05-13
I believe this is due to your file/folder permissions. I had this problem on my computer sharing files but if you check the permissions of the things you are trying to share then make sure that other users can access them they should be accessable from Windows.

I'm afraid I don't know exactly what the permissions should be but when I want to do it I just grant the maximum permissions I can since I'm only sharing files on a LAN with 3 other people. Hope that helps.

---

### Post by oldtappan on 2007-05-13
> **b0ng0 said:**
> I believe this is due to your file/folder permissions. I had this problem on my computer sharing files but if you check the permissions of the things you are trying to share then make sure that other users can access them they should be accessable from Windows.

I'm afraid I don't know exactly what the permissions should be but when I want to do it I just grant the maximum permissions I can since I'm only sharing files on a LAN with 3 other people. Hope that helps.

I think you're right.  As I said in my first post, it probably has something to do with my TrueCrypt volume: [http://ubuntuforums.org/showthread.php?t=442259](http://ubuntuforums.org/showthread.php?t=442259).  I'm hoping to get an answer that will help me sort that out.

---

