---
title: "Mount Network folder permanently"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by longtom on 2009-02-23
Hi,

since we got it going to have a NFTS drive mounted permanently,  we now proceed to share a windows network folder permanently.

If you try This:[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

and you get the following error message:

```

mount: wrong fs type, bad option, bad superblock on //CHEETAH/Cheetah,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

ask the forum...

We also want to set the permissions in those folders in such a way, that we can create folders and rename files and do all those things we daily need to do in any folder.

Now - how we are giong to do this...anybody?:D

regards

longtom

---

### Post by longtom on 2009-02-23
Update:

It seems I had the samba tools not installed correctly - or not at all.  No the error Message reads:

```

mount error: could not find target server. TCP name CHEETAH/Cheetah not found
No ip address specified and hostname not found

```

I took name and folder name as shown in Nautilus.  Where do I get the correct TCP name?

regards

longtom

---

### Post by Mark Phelps on 2009-02-23
Please post the details of the "mount" command you're using.

---

### Post by longtom on 2009-02-23
> **Mark Phelps said:**
> Please post the details of the "mount" command you're using.

Thanks for answering;

Here you are:

```
#permanent mounts of shard folders :
//Cheetah/Cheetah  /media/cheetah  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```

regards

longtom

Edit:  changed it slightly from above (lowercase/uppercase) as it looks in Windows.  Didn't help so.

---

### Post by longtom on 2009-02-24
bump

---

### Post by blueridgedog on 2009-02-24
What is the results of trying your command with the IP address of the box called Cheetah?

Such as:

```
//192.168.1.12/Cheetah  /media/cheetah  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```

Change the IP to match the IP assigned.

Also, the Cheetah box is sharing a folder and the share is called Cheetah?

Can you post the output of:

```
smbtee //Cheetah (or the ip address)
```

---

### Post by albinootje on 2009-02-24
> **longtom said:**
> 
```

mount error: could not find target server. TCP name CHEETAH/Cheetah not found
No ip address specified and hostname not found

```

Can you try your mount command with the ip-address instead of the name Cheetah, and report back ?

---

### Post by longtom on 2009-02-24
> **blueridgedog said:**
> What is the results of trying your command with the IP address of the box called Cheetah?

Such as:

```
//192.168.1.12/Cheetah  /media/cheetah  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```

Change the IP to match the IP assigned.

Also, the Cheetah box is sharing a folder and the share is called Cheetah?

Can you post the output of:

```
smbtee //Cheetah (or the ip address)
```

Ip address changes every morning once the PC gets started.  Otherwise I would have gone that route.

```
smbtee //Cheetah (or the ip address)
```

answer

```
bash: smbtee: command not found
```

anything I need to install first?

> Can you try your mount command with the ip-address instead of the name Cheetah, and report back ? 

See my remarks about the changing ip address


Is there a way I can see the correct name of the networked WinXP PC in order to make sure I use the correct name as well as upper- and lowercase?

longtom

---

### Post by blueridgedog on 2009-02-24
Sorry...my typo, it should be smbtree...I left out an R

---

### Post by albinootje on 2009-02-24
> **longtom said:**
> Ip address changes every morning once the PC gets started.  Otherwise I would have gone that route.

Can you please give all of your machines a static ip address ?
That will make things much easier to troubleshoot, and also makes  it easier to work with "real" hostnames.

For the rest, you should realize that using MS-Windows with other non MS-Windows machines can be confusing because of the differences  between NetBIOS names and hostnames.
See here : [http://en.wikipedia.org/wiki/NetBIOS](http://en.wikipedia.org/wiki/NetBIOS)
> 
A Windows machine's NetBIOS name is not to be confused with the computer's host name. Generally a computer running TCP/IP (whether it's a Windows machine or not) has a host name (also sometimes called a machine name or a DNS name).


---

### Post by DerHesse on 2009-02-24
For name resolution it is necessary to have either a functioning DNS (routers mostly do) or an entrance in your /etc/hosts.
If you do not provide an IP, you're off.

If you say the adress changes every morning and you do not have a DHCP-Server, you probably receive an APIPA-Adress. That's bad.
 
You cannot run cars if you don't have roads.  My advice build a road first.

---

### Post by TalioGladius on 2009-02-24
you do have smbfs installed, right?



edit:  I *think* that might be part of the problem.  sudo apt-get install smbfs

---

### Post by DerHesse on 2009-02-24
> **TalioGladius said:**
> you do have smbfs installed, right?
 
 
 
edit: I *think* that might be part of the problem. sudo apt-get install smbfs
 
 
There is no broadcast for mounting shares. Netbios resolution or DNS are prerequisite.
longtom, you understand German, do you? Have a look for cifs e.g. here: [http://wiki.ubuntuusers.de/Samba_Client_cifs](http://wiki.ubuntuusers.de/Samba_Client_cifs)  (smbfs = cifs since 8.04 :  [http://wiki.ubuntuusers.de/Samba_Client_smbfs](http://wiki.ubuntuusers.de/Samba_Client_smbfs)).

---

### Post by longtom on 2009-02-25
@der Hesse

thanks for the links.  One of those you read everything 3 times...and than start over.

Not your fault at all - au contraire - its just me being a bit slow....

But I'll get there *Schweiss abwisch....

 @TalioGladius

my sharp roman friend.  Thanks for the tip but somehow I managed to install that before...

@albinootje

Giving all machines (a lot) fixed ip addresses is unfortunately not an option right now.  I need to find a way around that.

@ blueridgedog

here you are.

It showed the whole network - but here is what it sees as far as Cheetah is concerned:
```

smbtree //cheetah
Password: 
WORKGROUP

\\CHEETAH        		
		\\CHEETAH\Canon3         	Canon 3
		\\CHEETAH\C$             	Default share
		\\CHEETAH\ADMIN$         	Remote Admin
		\\CHEETAH\Canon4         	Canon 4
		\\CHEETAH\Cheetah        	
		\\CHEETAH\C              	
		\\CHEETAH\print$         	Printer Drivers
		\\CHEETAH\IPC$           	Remote IPC

```

Hope that helps

regards

longtom

---

### Post by blueridgedog on 2009-02-25
> **longtom said:**
> 
```

smbtree //cheetah
		\\CHEETAH\Cheetah        	



Well the share exists.  Were you able to mount it by hand prior to trying to put it in fstab?

Can you try and post the output of a hand mounting via:

[CODE]sudo mkdir /mnt/Cheetah
sudo mount.cifs //CHEETAH/Cheetah /mnt/Cheetah -o user=YOURUSER,password=YOURPASSWORD
```

---

### Post by longtom on 2009-02-26
> **blueridgedog said:**
> Well the share exists.  Were you able to mount it by hand prior to trying to put it in fstab?

Can you try and post the output of a hand mounting via:

```
sudo mkdir /mnt/Cheetah
sudo mount.cifs //CHEETAH/Cheetah /mnt/Cheetah -o user=YOURUSER,password=YOURPASSWORD
```


Got that:

```

sudo mount.cifs //CHEETAH/Cheetah /mnt/Cheetah -o user=xxxx, password=xxxxxxxx
mount error: could not find target server. TCP name CHEETAH/Cheetah not found
No ip address specified and hostname not found

```

In place of the x's I put the relevant data.

Strange...

longtom

---

### Post by Ms_Angel_D on 2009-02-26
I just wanted to point you in the direction of [THIS POST]("http://ubuntuforums.org/showthread.php?t=288534"). It was a lifesaver for me on figuring out how to permently mount my windows shares.

---

### Post by longtom on 2009-02-26
> **MetalHellsAngel said:**
> I just wanted to point you in the direction of [THIS POST]("http://ubuntuforums.org/showthread.php?t=288534"). It was a lifesaver for me on figuring out how to permently mount my windows shares.

You beauty,

that is exactly what I was looking for!  And - it works.

Thank you very much.

Thank you also to everyone trying their best to get me going.

regards

longtom

---

### Post by Ms_Angel_D on 2009-02-26
Ohh gosh Now I'm blusing.....lol. Seriously though Glad it helped ;)

---

