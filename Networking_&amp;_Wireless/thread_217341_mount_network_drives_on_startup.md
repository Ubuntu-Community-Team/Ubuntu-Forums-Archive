---
title: "mount network drives on startup"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by mayamaniac on 2006-07-17
hi, I'm using this command to mount a network drive:

smbmount //Server/ShareName /mnt/ShareName -o username=xxxxxx password=xxxxxx

where do I put this command so that it mounts the newtwork drive automatically on bootup? I tried putting in System > Preferences > Sessions > Startup, but its not mounting on startup. Is there a startup file somewhere on /etc? I tried putting it in /etc/rc.local, but thats not working either. Help please.

---

### Post by gerbman on 2006-07-17
> **mayamaniac said:**
> hi, I'm using this command to mount a network drive:

smbmount //Server/ShareName /mnt/ShareName -o username=xxxxxx password=xxxxxx

where do I put this command so that it mounts the newtwork drive automatically on bootup? I tried putting in System > Preferences > Sessions > Startup, but its not mounting on startup. Is there a startup file somewhere on /etc? I tried putting it in /etc/rc.local, but thats not working either. Help please.The file you need to change is /etc/fstab. First, make sure you have the "smbfs" package installed. Next, add a line something like this to your /etc/fstab file:```
\\Server\ShareName     /mnt/ShareName     smbfs     defaults,uid=<username>,username=xxxxxx,password=xxxxxx     0     0
```The first column is the device/partition/share to mount, the second is where to mount it, the third is the filesystem type, the fourth is the option list, and the last two don't really matter. <username> is the name of your account on your PC. username=xxxxxx and password=xxxxxx are the username and password required by the remote server. After adding the line, do```
sudo mount /mnt/ShareName
```to mount the network share.

EDIT: The share will be mounted automatically on startup.

---

### Post by bforbes on 2006-07-17
That should probably be:
```

//Server/ShareName     /mnt/ShareName     smbfs     defaults,uid=<username>,username=xxxxxx,password=xxxxxx     0     0

```

---

### Post by gerbman on 2006-07-17
> **bforbes said:**
> That should probably be:
```

//Server/ShareName     /mnt/ShareName     smbfs     defaults,uid=<username>,username=xxxxxx,password=xxxxxx     0     0

```Either way...doesn't matter.

---

### Post by mayamaniac on 2006-07-18
That work quite well. You guys are awesome. Now I can access all my music files sitting on the PC server immediately after bootup. I didn't know that you can mount it in fstab, but then I'm a newbie at this. Thanks gerbman and bforbes.

EDit:

Spoke too soon, I'm not able to write to these network drives, only read is possible. How do I get write permission? I can write to these drives if go to Places > Connect to Server > Windows Share. But thats not the same as mounting it as a volume because they are not accessible with any of the ubuntu media players. What do I do to get write permissions on the smbfs drives?

---

### Post by gerbman on 2006-07-18
> **mayamaniac said:**
> Spoke too soon, I'm not able to write to these network drives, only read is possible. How do I get write permission? I can write to these drives if go to Places > Connect to Server > Windows Share. But thats not the same as mounting it as a volume because they are not accessible with any of the ubuntu media players. What do I do to get write permissions on the smbfs drives?Please post your smb.conf and fstab files.

---

### Post by Liam on 2006-07-18
Here's a slightly more secure method:

```

echo "username=xxxxxx" >> ~/.smbpasswd

echo "password=xxxxxx" >> ~/.smbpasswd

chmod 600 ~/.smbpasswd

sudo mkdir /mnt/ShareName

sudo chmod -R 777 /mnt/ShareName

```

Put the following line in /etc/fstab:

```

//Server/ShareName /mnt/ShareName smbfs user,defaults,credentials=/home/<UbuntuUsername>/.smbpasswd,uid=<UbuntuUsername>,gid=<UbuntuUsername> 0 0

```

The difference is that you're putting your Windows ID and PW in a file in your home directory that should only be readable by you and root, rather than anybody on the system. You've also added gid= option to the mount line, which is probably why you can't execute files on it.

---

### Post by mayamaniac on 2006-07-19
thank you liam, 

your method seems to work great so far, I have write privilege now. And thanks for the explanation also.

---

