---
title: "Samba Permissions Mystery"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by jaemo on 2008-05-28
Greetings all.

I am hoping this is something I overlooked, but I have tried multiple combinations of my smb.conf with mixed results.

I have a file server (emu) running Ubuntu 8.04 LTS Server Ed. Samba is set up on it and there are 2 500GB drives that I want to share. It's well firewalled and there are only 3 employees in our workspace, so security is not paramount for this machine but would be nice.

I followed the instructions here: [http://www.howtoforge.com/ubuntu-home-fileserver-p3]("http://www.howtoforge.com/ubuntu-home-fileserver-p3"), save that the drives are formatted with ext3 instead of NTFS. 

I've also created a user "pitch" at the system and smbpasswd levels on emu. 

The net effect I am seeing is very strange. I can log in, read/write/delete from Windows clients AND Mac OS. 
However, if I try to log in from ANOTHER ubuntu box (wallaby, 8.04 LTS desktop) I have serious issues. First off I cannot even see the thing from nautilus, even if I plug in the IP address. I can only mount it via terminal, thusly: 
```
sudo mount -t smbfs -o rw,username=pitch,password=########  //emu.domain.com/share  /home/jaemo/remoteshare/emu
```

Once I mount it this way I can then see it in nautilius. Now the REALLY WEIRD stuff happens. I can create directories and files at the root of the share, but I CANNOT create subfolders or files, I get a permission error. 

As this is meant to be a box I am shoving files at via rsync, it is a real problem if I cannot create subfolders.

Here's the snippet of my smb.conf dealing with the share in question:
```

[clientwork]
comment = Pitch Storage 2
path = /media/store2/clients
writeable = yes
available = yes
browseable = yes
valid users = pitch
create mask = 0777
directory mask = 0777

```

Any insight at all would be greatly appreciated. Google has let me down on this one kids...

Thanking you all in advance!

---

### Post by StooJ on 2008-06-03
Don't know if this will help, but you might want to check the owner & group locally on the server.
I ran into a similar problem & discovered that the owner & group was different on the server - I must have moved the folder from another user account without changing the owner.

---

### Post by nanohead on 2008-06-03
I had a similar thing, where nautilus simply would not perform correctly with samba.   I jerked around with it for a several days, and finally got the thing to work.  Same characteristics, where linux browsing out to windowsland would not work, but looking into linux worked.

here is a link to the thread where I tried to document what I did.  Hope it helps.  Sorry about the thread link, I guess I could have cut and paste from the other thread

[http://ubuntuforums.org/showthread.php?p=5105210#post5105210](http://ubuntuforums.org/showthread.php?p=5105210#post5105210)

Short of it is, that there are some bad mismatches between all the network definitions, including workgroup name, domain ID, etc.   smb.conf and base networking are not in sync.   And as usual, the samba documentation doesn't help at all.

---

### Post by jaemo on 2008-06-05
Thanks to both you of for your replies. 

Either a recent update has resolved it or a restart (both client box and server have since been restarted) solved it. I get the sense that it might have been something out of synch between the unix user and the samba users. 

...Of course there exists the very real possibility that it's only working now because I stopped effing around with it ;-)

thanks again!

---

