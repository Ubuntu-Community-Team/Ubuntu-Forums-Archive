---
title: "HP MEdia Vault"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by noworldorder on 2010-03-31
Ubuntu is excellent.  But I am having trouble figuring out how to access an external hardrive that is connected to my router.  It is a HP MEDIA VAULT.  All of the solutions I read about seem to involve command line stuff (yes I am a newbie) and I can't make them work.

So before I keep going does that road I wonder if there might be an easier way.

Thanks!
Chris

---

### Post by mechro on 2010-03-31
A quote from an HP manual...

> To connect to HP Media Vault using Samba
Samba provides a simple and secure way of connecting a Linux computer to the media vault using the SMB
(Server Message Block) and CIFS (Common Internet File System) protocols. The SMB network protocol is the
native file-sharing protocol for Windows. CIFS defines a standard remote file-system access protocol for use over
a network.
To use Samba, the Linux system must have Samba installed. For information about how to install Samba, see the
documentation or man pages included with the Linux distribution.
Using a Linux graphical interface to connect
Linux distributions have numerous versions and graphical interfaces. Consequently, it is not possible to provide
specific steps when using a graphical interface to connect a Linux system to the media vault. General steps for
connection include using a network browser to find the media vault.
Note: If a firewall is running, turn it off or configure the system to allow Samba to connect to the SMB Shares.
The path to the media vault is as follows:
   1. Domain - default, Windows Network
   2. Workgroup - default, MSHome
   3. Machines - default, HPMediaVault
If any of these default names have changed, use the new name.
Using an IP Address or NetBIOS name to access the HP Media Vault
Connecting to the media vault requires either the media vault's IP address or NetBIOS name. NetBIOS is an
acronym for Network Basic Input/Output System. The advantage of using the NetBIOS name is that even if the
media vault's IP address changes, the Linux system can find the media vault. The following two sections describe
each method.
Obtaining the HP Media Vault's IP address
The IP address for the media vault can be found on the router's configuration screens, usually under DHCP
Client Table or Show Connected Devices.

The manual is available as a PDF from here...

[http://h10032.www1.hp.com/ctg/Manual/c00763627.pdf](http://h10032.www1.hp.com/ctg/Manual/c00763627.pdf)

---

### Post by noworldorder on 2010-03-31
Thanks.  I tried the above without success.  I will give it another shot.

---

### Post by mechro on 2010-04-01
Actually, I think the first step is to check the configuration in your router. If there's no connection to your HP Media Vault then Samba won't work. Do you know how to get to your router's configuration?

---

### Post by noworldorder on 2010-04-11
"Do you know how to get to your router's configuration?"

Yes I do - what should I look for?

Thanks~

---

### Post by noworldorder on 2010-04-11
Well - not knowing what I am doing I tried to mount the 't media vault and this is what happened.  I can't read Matrix code.  Did it work?  And if so now what?  I can't see the Media Vault in 'Places'

Thanks!:


[B]mount: mount point mnt/Backup does not exist
root@chris-laptop:~# mount -t nfs 192.168.1.104:/shares/Volume1/Backup/\0402mnt/Backup
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
root@chris-laptop:~# +^C
root@chris-laptop:~# 
[/B][LEFT]
[/LEFT]

---

### Post by mechro on 2010-04-11
> **noworldorder said:**
> "Do you know how to get to your router's configuration?"

Yes I do - what should I look for?

Thanks~

The HP manual's instructions given above say...

> Obtaining the HP Media Vault's IP address
The IP address for the media vault can be found on the router's configuration screens, usually under DHCP
Client Table or Show Connected Devices.

---

### Post by noworldorder on 2010-04-11
yes I do know the IP address of the media vault. I used it in the terminal command above per the HP manual. Perhaps you can decipher the results for me and tell me what is going on in newbie.

---

### Post by mechro on 2010-04-11
Sorry, I'm not being very helpful, I'm a bit in the dark myself about this HP Media Vault.

It sounds as though your router is configured, so what happens when you go to **Places > Network**? Give it some time to connect and then hopefully a Nautilus file manager window will open showing any network connections you have. If the Media Vault isn't showing then you might need to install **samba** and/or do some more configuration.

---

### Post by noworldorder on 2010-04-13
[SIZE=3]I got it to work with this command:

[/SIZE]   	 	 	 	 	 	  [SIZE=3]mount -t smbfs //192.168.1.104/MediaShare /mnt/MediaShare[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]Yeah! But now I want to make the change permanent by [/SIZE][FONT=Times New Roman][SIZE=3]adding this line to the /etc/fstab file:[/SIZE][/FONT]


   	 	 	 	 	 	  hpmediavault:/shares/Volume1/Backup /mnt/mediavault nfs 



But this is the result I get:


root@chris-laptop:~# hpmediavault:/shares/Volume1/Backup /mnt/mediavault nfs 
bash: hpmediavault:/shares/Volume1/Backup: No such file or directory
root@chris-laptop:~# 

any thoughts?




 
[SIZE=3]
[/SIZE]
[SIZE=3]
[/SIZE]
 [SIZE=3]
[/SIZE]

---

