---
title: "Can Mount Network Drive GUI but Not via Commanline Mount"
date: 2019-03-19
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2019-03-19
I am trying to set up a raspberry pi as a file server. I have everything working except for one small thing. I can mount the network file system through the gui - clicking on the filesystem in nemo - but when I try to mount this through the commandline mount, it gives me [mount: special device //raspberrypi/multimedia/ does not exist]. I have tried mounting with

* smb://raspberrypi/multimedia
* //raspberrypi/multimedia
* //192.168.1.15/multimedia
* smb://192.168.1.15/multimedia

and it keeps giving me that error. I need this to be able to mount though mount so that I can auto mount this share through fstab or autofs. Can someone please tell me what I am doing wrong?

---

### Post by TheFu on 2019-03-19
Samba or NFS?  NFS is a little faster and provides native file permissions, unlike samba.

Please show the exact, full, mount command being used.

Raspberry Pi's have terrible network and disk performance, BTW. Both share the same USB2 bus.  For a tiny bit more $$, a Pine64 or Odroid single-board-computer (also ARM) have SATA and GigE networking which actually provide the expected storage and network performance.

---

### Post by rebeltaz on 2019-03-19
Well, the harddrive is a USB drive anyway, but as long as this thing can handle serving video files to kodi, I'll be happy. I got a Libre Computer the other day to play with as a web server, if you know anything about those?

Anyway... the filesystem is samba because I have to have it accessible to windows systems as well. The mount command I am using is:

```
sudo mount -t ext4 smb://192.168.1.15/multimedia /mnt/multimedia
```

---

### Post by TheFu on 2019-03-19
Ok, I see some confusion here.  The general form of a mount is this:
```
mount [-fnrsvw] [-t fstype] [-o options] device dir
```


There are 2 mounts necessary.

The mount on the raspberry pi and the mount on the remote systems which will be accessed using SMB/CIFS.

_==== On the Raspberry Pi ====_

On the raspberry pi, a normal mount is needed, so something like
```
sudo mount -t ext4 /dev/sda1   /mnt
```
I like to put mounts into the fstab, so they happen automatically, unless they are external devices.  The "dir" must preexist before mounting. In my example, that would be /mnt.  If you want /mnt/multimedia to be the *mount point*, then **sudo mkdir /mnt/multimedia** is mandatory.  For many reasons, I prefer not to leave permanent mounts under either /mnt/ or /media/, but it is your machine.  The file system standards say those areas for for other purposes.

The device, /dev/sda1, is just my guess at the name. You'd need to run **sudo fdisk -l **to see the correct name.

The file system type, ext4, is a guess, but assumes that you actually formatted the 1st partition on the USB drive to be ext4.  By default, these come from the vendor formatted with NTFS almost always - like over 99% of the time they are NTFS.  I think it is possible to use NTFS and share it, but that brings other complexities. 

Still on the Pi, now we need to tell Samba to share the specific directory.  Samba must be installed first, then the /etc/samba/smb.conf needs to be modified to share it.  Not hard.  Ubuntu 18.xx changed some things and I don't have any experience with those changes, but on earlier versions, the smb.conf  (use **sudoedit** to edit the smb.conf file) stanza should look something like this:

```
[Media]
  comment = Pi Media
  hosts allow = 127.0.0.1 172.22.22.0/24 192.168.1.0/24
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S
```

In the [Global] part, be certain this line exists:
```
    security = user
```

This doesn't allow guests, so before you can access the "Media" share, a userid and password have to be setup for samba.  sudo **smbpasswd -u thefu** is how to accomplish that.  Going forward, I think it picks up normal password changes, but the userid has to be added.

After that's all done, restart the samba service - **sudo service samba restart** - and the share will be accessible to the subnets listed.
If you get an error with "masked", then
```
sudo systemctl unmask samba
sudo systemctl enable samba
sudo systemctl restart samba
``` is the fix.  Freakin' systemd sucks.

_==== On the Linux Computer ====_

Assuming it is in the allowed subnet, you just need to create the mount point, and either run the mount or modify the fstab to handle mounting.
This is where it gets hard from a security standpoint and why NFS is better.  Samba permissions are set at mount time and are sorta global, per mount. No fine-grained permissions possible without going full out with complex setups.

A little script to make mounting easier:
```
#!/bin/bash

MNT_PNT=/mnt/Media
USER=thefu
 sudo mount -t cifs //romulus/Media $MNT_PNT  \
     -o rw,credentials=/home/thefu/smb-media.pass,soft,iocharset=utf8,username=${USER}
```

I keep the username and password in a credentials file with 600 permissions.  This is better for security.
Or you can add a line to the /etc/fstab ... I don't mount CIFS through the fstab, I use autofs, so I don't have a nice proven example to share. Sorry.  But here's my best guess:
```
//romulus/Media  /mnt/Media cifs rw,credentials=/home/thefu/smb-media.pass,soft,iocharset=utf8 0 2
```

Don't forget that /mnt/Media must already exist.
Don't forget that "romulus" has to be 'ping-able' from any client.  Or just use the IP address for that machine.  If the IP isn't static, I'd make it static.
Options cannot have spaces between them or inside - not exactly true, but ... don't use spaces.

Anyways, hope this is helpful and not confusing.  Usually after I post something like this, someone else will come along with a more concise answer.

---

### Post by rebeltaz on 2019-03-19
You give answers like I ask questions, lol... 

I do have the USB drive set up to automount on the Pi in fstab:

```

UUID=df479888-2010-485f-a620-0fab6516fab6	/mnt/multimedia	ext4	defaults,nofail,noatime	0	0

```

I formatted the drive as ext4. Not sure why now, it was years ago and I have trouble remembering what I ate for breakfast.

I prefer the UUID because I was having issues where the computer I had this on to begin with kept changing it's mind about where in the /dev family it wanted the drive to live. I also have the /mnt/multimedia mount point pre-created on the pi (as well as on the computer) with the owner:group set to derek:derek. lol... every time I need help with something on a mount point, everyone tells me I shouldn't use /mnt... just because it's not standard... lol.. I guess I'm just a rebel :)

So I do have samba set up like you said on the Pi:

```

[multimedia]
   comment = multimedia server
   path = /mnt/multimedia
   browsable = yes
   writeable = yes
   guest ok = yes
   read only = no
   create mask = 0770
   directory mask = 0770
   force user = derek

```

Now I took this from the setup I had (that was working) on the original computer server for this filesystem. I notice in yours that you have a 'hosts allow' parameter. I never needed that before. Should that be needed now?  

I do have the **security = user** line and I did do the **smbpasswd -u derek** command. 

The IP of the Pi is static and I prefer to use that than the hostname when possible. 

I do want to have the multimedia automounted on the computer at boot, either by fstab or autofs, but I figured I need to figure out how to phrase the mounting with mount and get that working before I tried adding it to boot up.

I don't know if this helps any, but this is the output of smbclient on the computer:

```

Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.2.14-Debian]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	multimedia      Disk      multimedia server
	IPC$            IPC       IPC Service (Samba 4.2.14-Debian)
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.2.14-Debian]

	Server               Comment
	---------            -------
	RASPBERRYPI          Samba 4.2.14-Debian
	SHOP                 shop server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            SHOP

```

Further developments... I found that I didn't have cifs-utils installed, so I installed that and tried ```
sudo mount -t cifs //192.168.1.15/multimedia /mnt/multimedia -o username=derek,password=pass
``` again. This time, it didn't give me any errors, but the filesystem still isn't being mounted.


OK FINAL UPDATE:
I went and got my laptop. It automounts the multimedia share with no problem, so... the PI is sharing. The problem is on the computer side not wanting to mount via commandline. Hopefully this will be enough information to get this straightened out....

---

### Post by TheFu on 2019-03-19
After you attempt a mount, be certain to **umount** it.

What you are doing all seems reasonable, except I think you need some of the options I included.
The allow/deny is just best practices.  I always lean towards more security, not less. Same for using the credentials file, some passwords, the good ones, can't be included on the mount command line. The UTF8 part was necessary a few years ago.

UUID excellent. I didn't want to make things _too_ complex. ;)

What is the difference between the laptop samba and the ubuntu samba? 
What do the samba log files show? They are in /var/log/samba/
What does **testparm** show on the pi?

The stuff I'm showing now works with a 16.04 Samba server and a Win7 client.  I had to do some registry modifications because Win7 has a huge bug and would drop the connection until reboot.  I don't remember those regedit settings, but they were from microsoft support website.  I don't have any newer version of Windows available and don't have any plans to load anything newer.

Samba on the server here is 2:4.3.11+dfsg-0ubuntu0.16.04.18, another has 2:4.3.11+dfsg-0ubuntu0.14.04.19, but it will be wiped and hardware retired soon.

I don't use samba to/from my raspberry pi systems.  Those are all NFS clients and have never had any issues ... er ... ever.

---

### Post by rebeltaz on 2019-03-19
I finally got it!

I don't know what I did, unless an old fstab entry that I forgot to disable was conflicting, but i finally just added this to fstab

```

//192.168.1.15/multimedia	/mnt/multimedia	cifs	defaults,nofail,username=derek,password=pass,gid=1000,uid=1000	0	0


```

and rebooted the computer. Sure enough, multimedia automounted and with the correct permissions. **Thank you so much for your help!**

I will go add those security parameters to smb. I agree more security is better! Thanks again.

---

### Post by rebeltaz on 2019-03-19
> **TheFu said:**
> 
I don't use samba to/from my raspberry pi systems.  Those are all NFS clients and have never had any issues ... er ... ever.

Just pout of curiosity, now that I have this working, **if** I decided to try and switch to nfs from samba, how hard would that be? What would I have to do to do that?

---

