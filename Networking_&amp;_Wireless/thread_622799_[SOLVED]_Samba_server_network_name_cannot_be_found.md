---
title: "[SOLVED] Samba server network name cannot be found problem"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by Tobywaters on 2007-11-25
I am having a few problems with my 7.10 box that I have setup as a Samba Server.

I installed samba and configured it for two users via Webmin and the smb.conf file. The first user is the main user and the second user is one I created for general use(I made sure to add this user via the console).

The main user works fine and can see the shares and read/write them but the other user can only see the main shares but when it tries to connect it gets " \\SERVER\Video is not accessible. You might not have permission to use this resource. Contact the administrator of this server to find out if you have permissions.

The network name cannot be found"

I am the administrator and I am completely out of ideas!

Here is my smb.conf:

[global]
	netbios name = Server
	os level = 20
	
[Music]
	path = /media/sdc1/My Music
	write list = toby
	read list = brynland
	browseable = yes
	valid users = toby, brynland

[Video]
	read list = brynland
	write list = toby
	path = /media/sdc1/My Videos
	browseable = yes
	valid users = toby, brynland
[DUMP]
	writeable = yes
	valid users = toby, brynland
	path = /media/sdc1/DUMP
	browseable = yes


The idea is that toby should have read/write for everything whereas brynland should only be able to read. There will be a mix of Vista and XP Pro boxes connecting to this and have tried it on all of them. They can use "toby" fine but not "brynland".

I am pulling my hair out here I just cant seem to figure it out. Any help would be appreciated!

---

### Post by Tobywaters on 2007-11-25
I hate to bump my own post but does anyone have any ideas about this?

---

### Post by jetsam on 2007-11-25
I think you need to add each user twice.

Once for linux:
```
sudo adduser <username>
```

and once for Samba:
```
sudo smbpasswd -a <username>
``` 

Did you do both?  

I'm a bit unclear on this stuff myself, but I believe both user names need to be identical, passwords can be different or the same, and you use the Samba password for remote access.

---

### Post by Tobywaters on 2007-11-25
Yes I have added both of them and they are identical names and passwords. I have tried the sync utility on webmin to sync my linux and samba users and this has said that they are synced correctly.

---

### Post by jetsam on 2007-11-25
Check the unix permissions on /media/sdc1/My Videos with ls -l.  Most tutorials i've seen chmod share directories and the files under them to 777 or 755 .  I think the important thing is read permissions for others.  You probably want to set:
```
create mask = 0777
directory mask = 0777
```
On the shares.  This sets the default permissions for new directories and files created through Samba.

---

### Post by Tobywaters on 2007-11-25
ls -l shows drwxrwx-- for all the folders. I checked the files using the dolphin browser and it shows 755 as the directory mask. I don't really want to use 777 because that would cause the brynland user to be able to write to the share?

---

### Post by jetsam on 2007-11-25
> ls -l shows drwxrwx-- for all the folders.
That's read write and execute allowed for file owner and group, but not others.
```
chmod o+r -R /media/sdc1/My\ Videos
```
Will add read permissions for others recursively to the My Videos directory and everything underneath it.  

For the masks in the smb.conf, you can make it whatever you think is appropriate.  
```
create mask = 0754
directory mask = 0754
```
Will give read/write/execute to owner, read and execute to group, and read to others.  It's a minor issue for what you want to do, though, so don't worry about it until you get read access to the server working.   

These masks are actually a bit more complicated than simply setting the permissions, but I think the end effect is that directories and files created from Windows get these permissions.  Anything done through linux on the server itself uses normal permissions.

---

### Post by Tobywaters on 2007-11-26
I did the chmod comand as sudo and then did ls-l in the directory and it still appeared to have the same access settings, have I done something wrong here?

 I then used webmin to set  the masks to 754. I still cannot access the shares.

---

### Post by jetsam on 2007-11-26
> I did the chmod comand as sudo and then did ls-l in the directory and it still appeared to have the same access settings, have I done something wrong here?

...possibly.  After running the command successfully, the directories and file permissions should read:
drwxrwxr--

instead of:
drwxrwx---

That final r is what we care about.  It's a very subtle difference, but it's important...  using sudo was a good idea.  I should have put it in there.  

The details of the command matter:  No trailing slash after /media/sdc1/My\ Videos is important, and escaping the space in the name with \ are easy to overlook.

---

### Post by Tobywaters on 2007-11-26
I have just checked  and it is still drwxrwx without the r on the end. 

sudo chmod o+r -R /media/sdc1/My\ Videos

that is the exact command I am running. It does not come up with any errors just goes straight to the next line so it seems to be working ok but the ls -l indicates otherwise

---

### Post by jetsam on 2007-11-26
Now I'm a bit stumped.  How is the drive mounted?  It's not a windows share itself is it?

---

### Post by Tobywaters on 2007-11-26
It is a drive that is NTFS partitioned that is installed into the linux box

---

### Post by jetsam on 2007-11-26
...OK.  I think the second post in this thread might have the relevant fix:

[http://ubuntuforums.org/showthread.php?t=417785&highlight=NTFS+mount]("http://ubuntuforums.org/showthread.php?t=417785&highlight=NTFS+mount")

Samba won't let the brynland user see files owned by root or toby unless the read permissions for others are set on those files.  The big picture is you need to find a way to set those read permissions.

---

### Post by Tobywaters on 2007-11-26
I changed this and managed to then change permissions on the drive. It is all working now! Managed to login as Brynland and they can read files but not write/delete files!

Thankyou very much for your help!

Cheers!

---

### Post by jetsam on 2007-11-26
You're welcome.  I'm glad it worked!

Just for future reference, and to make sure I'm not spreading misinformation on the forums, I was wrong about how "create mask" and "directory mask" function.  They actually set the maximum allowable permissions for files created through Samba.  "force create mode" and "force directory mode" force permissions to be a certain way.  For you, toby, the way you have it set now is just fine so no need to mess with it.   

p.s.  Mark the thread solved if you get the chance.

---

