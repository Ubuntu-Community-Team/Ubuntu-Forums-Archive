---
title: "Samba yet again......"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by FlashOmega on 2007-01-07
Alright... so I am really confused....  I am really bad with samba and dont know really what im doing so bare with me... heres where I am at

both computers have samba installed
one computer is suppose to share 1 directory with many sub directory ... only ONE sub directory should be writable to the remote user and the rest should all be read only

so basically I have a big drive and my roomate wants access to my media directory and in my media directory there is a shares folder he should be able to write to incase he has crap he wants to backup

this all worked great (except only to read... couldnt write)

then I must have messed it up

then I had it working again but if he used sudo on his machine with his sudo password he could write to my directories... or delete anything

and finally now... I have NO idea what ive done for this to happen... but it ALMOST mounts
it mounts BUT .... well I will let the output speak for itself
```
carl@cm-compy:/media$ cd Share
carl@cm-compy:/media/Share$ ls
ls: .: Input/output error

```


so thats all folks... here is my smb.conf file... well the part that I am responsible for at least... as well as the fstab lines from the other computer

smb.conf
```

[Data]
path = /home/sean/Media/
comment = Media
read only = yes 
guest ok = no
public = yes 

[Shares]
path = /home/sean/Media/Shares/
comment = Sharing folder
read only = no
guest ok = no
public = yes

```


fstab
```

//192.168.15.100/Data   /media/Sean    smbfs   username=carl,password=pass
//192.168.15.100/Shares /media/Share    smbfs   username=carl,password=pass

```

so thanks to anyone who has a hint for me.
P.S Its probably a really stupid mistake... dont over think.... im really bad at networking

---

### Post by Zimmer on 2007-01-07
[http://makuchaku.info/amnesty/#installsamba](http://makuchaku.info/amnesty/#installsamba)

I have shared folders in the past using user security[edit the config file], adding a linux user to the machine, then adding a SAMBA user (same name) . 

See post #5, this thread
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)
hope that helps...

---

### Post by tagra123 on 2007-01-07
These should help you get it working.

A decent guide on this page.

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

General How To on the forums.
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Here are a couple of problems I encountered and how they were fixed.

Printer Sharing
[http://ubuntuforums.org/showpost.php?p=1978640&postcount=4](http://ubuntuforums.org/showpost.php?p=1978640&postcount=4)

Nautilus Problem with samba
[http://ubuntuforums.org/showpost.php?p=1960858&postcount=18](http://ubuntuforums.org/showpost.php?p=1960858&postcount=18)

---

### Post by FlashOmega on 2007-01-08
Alright I found my problem... thanks guys... but I have run into another problem

When I boot with the mount info in fstab it does not mount properly

```
lrwxrwxrwx 1 root root    6 2006-12-17 08:02 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2006-12-17 08:02 cdrom0
?--------- ? ?    ?       ?                ? Sean
drwxr-xr-x 2 root root 4096 2006-12-17 08:01 hda2
?--------- ? ?    ?       ?                ? Share
 
```

Notice the two folders who are not mounted properly at all... clear to see which ones.  However if I rem out those two from fstab it boots fine and both folders are there and working... but empty because there is nothing mounted there.  If I then unremark them and mount -a they mount properly without any flaws at all... works great

So here are my thoughts.. could be wrong
1.  fstab is being mounted before samba starts (dont know how to check)
or
2. It hates me and I need to find out how to make root mount them using a script on boot (I have the script written and it works but I dont know how to add it to the boot process)

Any ideas?

---

### Post by tagra123 on 2007-01-08
> **FlashOmega said:**
> Alright I found my problem... thanks guys... but I have run into another problem

When I boot with the mount info in fstab it does not mount properly

```
lrwxrwxrwx 1 root root    6 2006-12-17 08:02 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2006-12-17 08:02 cdrom0
?--------- ? ?    ?       ?                ? Sean
drwxr-xr-x 2 root root 4096 2006-12-17 08:01 hda2
?--------- ? ?    ?       ?                ? Share
 
```

Notice the two folders who are not mounted properly at all... clear to see which ones.  However if I rem out those two from fstab it boots fine and both folders are there and working... but empty because there is nothing mounted there.  If I then unremark them and mount -a they mount properly without any flaws at all... works great

So here are my thoughts.. could be wrong
1.  fstab is being mounted before samba starts (dont know how to check)
or
2. It hates me and I need to find out how to make root mount them using a script on boot (I have the script written and it works but I dont know how to add it to the boot process)

Any ideas?

Are you including windos login info in th fstab entry or a .rc file?

---

### Post by FlashOmega on 2007-01-08
my fstab file entries are at the top... and I have no idea what a .rc file actually is.... also not using any windows machines so just for the record the solution to my problem need not be windows compatible... only linux to linux

---

### Post by tagra123 on 2007-01-08
> **FlashOmega said:**
> my fstab file entries are at the top... and I have no idea what a .rc file actually is.... also not using any windows machines so just for the record the solution to my problem need not be windows compatible... only linux to linux

If its for linux to linux nfs will be much faster (and easier)


on both the machines

```
sudo apt-get install nfs-kernel-server
```


You can exports (shared folders) to either machine


```
mkdir /home/username/nfssharedfolder

sudo gedit /etc/exports
```

Add this or similar line (ip may be different --this is for all lan clients)
--add a line for each shared folder / directory

```
/home/username/nfssharedfolder 192.168.1.0/255.255.255.0(rw)
```

Save and exit

To find Comp1's ipaddress  now type  

```

ifconfig -a  
```

it should be something like 192.168.1.X

we'll assume its 192.168.1.5

```
sudo /etc/init.d/nfs-kernel-server restart
```


+++++++++++++++++++++++++++++++++++++++++++++++++++


On the remote computer to access this share we'
```

sudo apt-get install nfs-kernel-server
```

```
sudo mkdir /media/nfssharefromComp1
sudo chmod 777 /media/nfssharefromComp1
mount -t nfs 192.168.1.5:/home/username/nfssharedfolder /media/nfssharefromComp1
```



The share should be mounted and working on your desktop.

Make it automatically mount upon booting the computer.
```

sudo gedit /etc/fstab
```
#add this line fo fstab
```
192.168.1.5:/home/username/nfssharedfolder /media/nfssharefromComp1   nfs          rw                   0       0
```


hope this helps

---

### Post by FlashOmega on 2007-01-09
I will definitly give that a try... but seeing as my samba stuff is already setup and working except for this minor annoyance I would really like to figure it out.... 

I think my problem has to do with the boot order... because mount -a will do it... but on boot wont... 

Anybody?

---

### Post by Iowan on 2007-01-10
[http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html]("http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html")
Any help here?

---

### Post by tagra123 on 2007-01-12
I meant to say .smbcredentials  but I just called mine smb.rc for less typing.

---

### Post by FlashOmega on 2007-01-12
well I got it working great now... although I still dont understand the problem... so I just wrote a mount script and put it in the runlevel2 launch... so same effect.

Thanks everyone for your help... I will certainly keep an eye on this forum incase anyone knows why I was having that strange issue cause I am still very cusious

---

