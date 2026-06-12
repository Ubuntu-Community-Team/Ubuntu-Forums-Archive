---
title: "Trouble mounting cifs shares after upgrade to 17.10"
date: 2017-10-21
forum: Networking &amp; Wireless
---

### Post by alanwalterthomas on 2017-10-21
I had a 17.04 ubuntu desktop with a couple samba shares mounted in fstab
It worked pretty well.
Then I upgraded to 17.10, and it broke.

I eventually figured out what the matter was before posting this question, but had already written most of this so I figured I'd post it anyway in case someone, including my future self, might find it useful.

```

#Alan's mount on U35WF
//192.168.1.101/2TBhdd /mnt/U35WF/alan                   cifs credentials=/home/alan/.smbcredentials,iocharset=utf8,sec=ntlm,uid=1000,gid=1000 0 0
#Bella's mount of U35WF
//192.168.1.101/2TBhdd /mnt/U35WF/bella                   cifs credentials=/home/bella/.smbcredentials,iocharset=utf8,sec=ntlm,uid=1001,gid=1001 0 0

```
At 192.168.1.101 is a Kimax U35WF running a custom OpenWRT firmware.
Its samba version is 3.6.25. Its smb.conf was:
```

[global]
	netbios name = LEDE 
	display charset = UTF-8
	interfaces = 127.0.0.1/8 lo 192.168.1.101/24 br-lan 
	server string = LEDE on U35WF
	unix charset = UTF-8
	workgroup = WORKGROUP
	local master = no
	browseable = yes
	deadtime = 30
	domain master = yes
	encrypt passwords = yes
	enable core files = no
	guest ok = yes
	invalid users = root
	load printers = no
	map to guest = Bad User
	max protocol = SMB2
	min receivefile size = 16384
	null passwords = yes
	passdb backend = smbpasswd
	preferred master = yes
	security = user
	smb passwd file = /etc/samba/smbpasswd
	syslog = 2
	use sendfile = yes
	writeable = yes
	bind interfaces only = yes

[homes]
	comment     = Home Directories
	browsable   = no
	read only   = no
	create mode = 0750

[2TBhdd]
	path = /mnt/2TBhdd
	valid users = alan bella
	read only = no
	guest ok = no
	create mask = 0660
	directory mask = 0750

[Alan]
	path = /mnt/2TBhdd/alan
	valid users = alan
	read only = no
	guest ok = no
	create mask = 0660
	directory mask = 0750

[Bella]
	path = /mnt/2TBhdd/bella
	valid users = bella
	read only = no
	guest ok = no
	create mask = 0660
	directory mask = 0750

```

I tried to mount manually, but got an error message
```

sudo mount //192.168.1.101/2TBhdd /mnt/U35WF/alan -t cifs -o credentials=/home/alan/.smbcredentials,uid=1000,gid=1000
mount error(22): Invalid argument

```

dmesg had this to say:
```

[ 8458.126450] No dialect specified on mount. Default has changed to a more secure dialect, SMB3 (vers=3.0), from CIFS (SMB1). To use the less secure SMB1 dialect to access old servers which do not support SMB3 specify vers=1.0 on mount. For somewhat newer servers such as Windows 7 try vers=2.1.
[ 8458.131309] CIFS VFS: cifs_mount failed w/return code = -22

```
I tried increasing smb verbosity like this, and got one more line:
```

sudo su
echo 7 > /proc/fs/cifs/cifsFYI
dmesg | tail
[ 8509.743356] No dialect specified on mount. Default has changed to a more secure dialect, SMB3 (vers=3.0), from CIFS (SMB1). To use the less secure SMB1 dialect to access old servers which do not support SMB3 specify vers=1.0 on mount. For somewhat newer servers such as Windows 7 try vers=2.1.
[ 8509.747964] Status code returned 0xc000000d STATUS_INVALID_PARAMETER
[ 8509.747991] CIFS VFS: cifs_mount failed w/return code = -22

```
(Note, echo 0 > /proc/fs/cifs/cifsFYI to set verbosity back to normal)
I looked up that status code at [https://msdn.microsoft.com/en-us/library/ee441884.aspx](https://msdn.microsoft.com/en-us/library/ee441884.aspx) but it only says "A parameter supplied with the message is invalid."

Nonetheless I had a hint that the SMB protocol version may be the issue, and decided to try to mount with different versions. Here are my attempts:
```

alan@Desktop: ~ $ sudo mount -t cifs //192.168.1.101/2TBhdd /mnt/U35WF/2TBhdd --verbose -o credentials=/home/alan/.smbcredentials,vers=3.0
mount.cifs kernel mount options: ip=192.168.1.101,unc=\\192.168.1.101\2TBhdd,vers=3.0,user=alan,pass=********
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
FAIL: 32
alan@Desktop: ~ $ sudo mount -t cifs //192.168.1.101/2TBhdd /mnt/U35WF/2TBhdd --verbose -o credentials=/home/alan/.smbcredentials,vers=2.1
mount.cifs kernel mount options: ip=192.168.1.101,unc=\\192.168.1.101\2TBhdd,vers=2.1,user=alan,pass=********
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
FAIL: 32

```
Both of these had the following output from dmesg:
```

Status code returned 0xc000000d STATUS_INVALID_PARAMETER
CIFS VFS: cifs_mount failed w/return code = -22

```
This, however, allowed me to mount the share.
sudo mount -t cifs //192.168.1.101/2TBhdd /mnt/U35WF/2TBhdd --verbose -o credentials=/home/alan/.smbcredentials,vers=2.0

Around this time I discovered that Samba =! SMB and Samba Version =! SMB Protocol Version. [http://www.kossboss.com/?p=2661](http://www.kossboss.com/?p=2661)
I had expected my NAS' 3.6.25 samba to support SMB3, because well, they about the same thing from a noob's point of view, and both versions start with a 3. :S

Anyway, it turns out that before the upgrade, the connection was via SMB1 as it was a universally supported default. That's been depreciated, probably due to the WannaCry hack, which exploited it.
Ubuntu just needed me to add vers=2.0, and 2.1 & 3.0 were never gonna work because the server doesn't support those later versions.
I ended up adding these options to my server's smb.conf.template file:
```

#In [global] section
	min protocol = SMB2
	max protocol = SMB2

```

---

### Post by axe87 on 2017-12-28
I had the same problem today having upgraded to 17.10. However, for some strange reasons setting vers=2.0 didn't work. I kept getting

```
CIFS VFS: cifs_mount failed w/return code = -95
```

However vers=2.1 and vers=3.0 works, which works for me. I'm not sure if this is a client pc (ubuntu) or server (debian) issue. Even though this works I still get the following error:

```
CIFS VFS: ioctl error in smb2_get_dfs_refer rc=-2
```

Despite this all seems to be working.

---

