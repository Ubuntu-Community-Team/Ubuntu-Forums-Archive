---
title: "Wired Networking with Samba"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by jrab227 on 2010-05-27
Hey all. I'm attempting to share an external hard drive over my room network and its not working. I used Samba to share the drives but when I try to access them using my Jolicloud netbook, I can't access them. So for starters, how do I create a new network for myself? Should I even be using Samba for this? Another thing, how can I configure it so users who try to view my external drives require a password?

---

### Post by cariboo on 2010-05-28
When you click on the network icon on the panel on the right side do you get a Windows Network icon in the file browser? When you click on that icon do you get a workgroup icon? If the answer is no to either of those questions, you probably haven't got samba configured properly. 

Open a terminal and type:

```
testparm
```

on the system you are sharing drives from, the above command should tell you if you have any errors in your /etc/samba/smb.conf.

If you don't have any errors in the same terminal type:

```
smbtree
```

you should get a listing of all the shared drivers on your network, it should look something like this:

```
smbtree
Enter my password: 
APLUS
	\\WILLY          		willy server (Samba, Ubuntu)
		\\WILLY\print$         	Printer Drivers
		\\WILLY\Movies         	Movies & TV Shows
		\\WILLY\Music          	Music
		\\WILLY\Documents      	Documents
		\\WILLY\Stuff          	Everything Else
		\\WILLY\Iso            	Mounted iso's
		\\WILLY\Images         	iso images
		\\WILLY\IPC$           	IPC Service (willy server (Samba, Ubuntu))
	\\RISKY          		XP Computer
		\\RISKY\C$             	Default share
		\\RISKY\ADMIN$         	Remote Admin
		\\RISKY\EPSONSty       	EPSON Stylus Photo R340 Series
		\\RISKY\All Users      	
		\\RISKY\SharedDocs     	
		\\RISKY\print$         	Printer Drivers
		\\RISKY\IPC$           	Remote IPC
```

You should see your shared drives in the output of the above command.

---

### Post by mapes12 on 2010-05-29
> I'm attempting to share an external hard drive over my room network and its not working.Is this HDD connected to your Ubu box or a MS box? How is it formatted?

---

### Post by jrab227 on 2010-05-29
To cariboo:

I do get that display, but there's still a problem with me viewing the files on other connected pcs.

To mapes:

Fat 32 and the hard drive is connected to the Ubuntu box. Either way, Jolicloud and Ubuntu are both Linux so I'm assuming this shouldn't be a problem.

I guess I should be asking how to remove the current share and create a new one from the ground up that requires a password and username to view the shared directories.

---

### Post by HermanAB on 2010-05-29
Howdy,

There are many ways to share files in Linux.  In order of increasing difficulty:
FTP
SSH
NFS
SMB

So, you picked the most difficult method.  Samba has hundreds of lines of configuration.  NFS has only *one* line of configuration  on the server.  Yes, ONE.

FTP and SSH are more complex than NFS, but they work out of the box - just install and use - they are easier to get to work.  

In contrast, SMB doesn't work out of the box, is complex, slow and basically just a total waste of time in most cases.  It should only be used when there are a large number of Windows client machines. Otherwise, it is less hassle to install Services for UNIX (A free download from MS) on the Windows machines and use NFS.

---

### Post by jrab227 on 2010-05-31
> **HermanAB said:**
> Howdy,

So, you picked the most difficult method.  Samba has hundreds of lines of configuration.  NFS has only *one* line of configuration  on the server.  Yes, ONE.


But isn't this also the most secure since I can specify all the possible users who access my files and permissions? And I figured this is the best commercial application and I might as well learn it the hard way first and take the pain so I can use it later.

---

### Post by cariboo on 2010-05-31
You can't set permissions on a vfat drive, the only thing you can really do is set the mount point permissions for example:

```
sudo chmod -R 777 /media/external
```

I don't really recommend using 777, as it makes the drive world read/writable, if settings the permissions to the above works, you can play with permissions so that every one can still read and write to the files. Have a look at man chmod for more info.

---

