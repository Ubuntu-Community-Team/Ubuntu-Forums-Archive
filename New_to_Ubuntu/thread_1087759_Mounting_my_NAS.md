---
title: "Mounting my NAS"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by RichardCL on 2009-03-05
Hallo Forum,

I'm having a few problems working with my NAS (IB4220B).

I began with Samba which works OK but sometimes needs a few tried to get started. I heard that NFS should be better for using this box.

My NAS is quite restrictive about setting up shares so I end up with a series of directories on the NAS each with NFS share to the IP address of my desktop.

My WLAN router tells me that my IP address on my internal network is 192.168.178.27, while that of the NAS is 192.168.178.21.

What I'm struggling with now is how to automatically mount all of the directories on the NAS at boot such that they appear under the home directory as local disks.

e.g.
NAS/md1/media/     appears as     DESKTOP/sdb/home/user/media/

I'd like to do that on my laptop and desktop.

I've tried a whole stack of commands starting with  sudo mount 192.168.178.21 but keep getting mount.nfs internal error.

What am I doing wrong???


Richard

---

### Post by Jose Catre-Vandis on 2009-03-05
Best to read through this thread:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Here is a typical line in my fstab for automounting of nfs shares from my nfs server

```
192.168.0.20:/media/mymusic /media/music nfs rsize=8192,wsize=8192,timeo=14,intr,bg
```

where 
192.168.0.20 is my nfs server IP
/media/mymusic is the nfs share on the server
/media/music is the mount point on my client

---

### Post by RichardCL on 2009-03-06
@Jose: thanks for the tip. I've been through the post. Some of it goes over my head since I'm not configuring the server


One thing I'm stuck on that didn't seem to be answered in the forum although there was a question on it: How do I know the address of my share?

When I access the NAS through ftp I get a path /md1/media/ where md1 is the hard drive itself. Does my share start with md1 or media? In samba I can simply open the GUI file manager and type \\myNAS\ and enter a user name and password. I then see all the share that have Samba open to that user. Is there a similar command to see the shares open to an NFS user?

Next, the tutorial shows the client making directories and mapping them. I'd like to replace my current home directories under Ubuntu such that /home/user/documents/ points to NAS-IP:/home/documents. I assume that is possible.

Thanks again.

---

### Post by RichardCL on 2009-03-06
Here's what I tried with the outputs

Installed the portmap
```
sudo apt-get install portmap nfs-common
```

returned
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
portmap is already the newest version.
```

Make a directory for the mapping
```
sudo mkdir /home/richard/nas
```

Change fstab
```
sudo nano /etc/fstab
```

added line
```
192.168.178.21:/mnt/md1 /home/richard/nas nfs rsize=8192,wsize=8192,timeo=14,intr,bg
```


Restart
```
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart

```


Tried to mount
```
sudo mount /home/richard/nas

```


Ubuntu says:
```
mount.nfs: internal error

```

added line (media is a specific share in the NAS webinterface)
```
192.168.178.21:/mnt/md1/media /home/richard/nas nfs rsize=8192,wsize=8192,timeo=14,intr,bg
```


Tried to mount
```
sudo mount /home/richard/media

```

Works fine and I can see the directory in Nautilus. I just can't get at the files now. I get error

```
You do not have the permissions necessary to view the contents of "music".
```

I looked at permissions within the folder view and see owner=7003 read and write permission, users read and write, others no access.

Seems that I'm nearly there.

---

### Post by Jose Catre-Vandis on 2009-03-07
The manual mount command for an nfs share is different to the normal mount command:
```
sudo mount 192.168.178.21:/mnt/md1/media    /home/richard/nas
```
you may have to fiddle about with the directories you write, as you have seen.

To mount what is in fstab issue the command:
```
sudo mount -a
```

---

### Post by RichardCL on 2009-03-13
> **Jose Catre-Vandis said:**
> The manual mount command for an nfs share is different to the normal mount command:
```
sudo mount 192.168.178.21:/mnt/md1/media    /home/richard/nas
```
you may have to fiddle about with the directories you write, as you have seen.

To mount what is in fstab issue the command:
```
sudo mount -a
```

Many many thanks, all working right now. It turned out that the server wasn't properly configured! Any combination of fstab settings wouldn't have gotten me the access as I wanted. I had to get my hands even more dirty with the embedded linux verison on the sever.

Even Open office behaves properly now that NFS is working (the smb support in Open office is pretty poor).

One final question:
I've set the exports file on the server with a series of lines like
```
/mnt/md1/music 192.168.178.27(rw,root_squash)
```
I'm assuming that only the computer with that IP address on the internal network can get that data. Thus I'm now free to port-forward port 21 in the router firewall such that ftp from external is possible (and set restrictive and read-only ftp settings). Is that correct?

---

### Post by jaime256 on 2009-03-14
I have finally decided to give this mounting a try again. I just didn't want to bother with all that file configuration, but here's what I have found to work. I would have added this post to the link where I found the information, but that is archived and won't let anyone post anymore.

I'm using samba for the share so here are the steps I took:
1. Make sure smbfs is installed on your machine

2. Add this line to your fstab for each share:
//ipadress/sharename /home/yourusername/directoryyoucreated cifs username=yourusername,password=sharepasswordifany,users,rw 0 0

3. To check that that mount works form the terminal type: sudo mount -a and just keep your open windows small so you can see your desktop and the share will appear on there.

4. Here's where I found this informtion, but I just had to play with mine in order to make sure it worked. Type something different and the mount doesn't work, at least not with this line.

[http://ubuntuforums.org/showthread.php?t=524930](http://ubuntuforums.org/showthread.php?t=524930)

5. Now, does anyone know how I can have the command ask me for the share password instead of putting it on that line before mounting the share?

---

### Post by kellemes on 2009-03-14
> **jaime256 said:**
> 
5. Now, does anyone know how I can have the command ask me for the share password instead of putting it on that line before mounting the share?

Just leave the "password=<password>" out works for me..
At least from cli, like so..
```
mount -t cifs //<IP_TO_NAS> /mnt_point -o username=<name>
```

You can also put your credentials in a separate file..
```
**credentials=filename**
specifies a file that contains a username and/or password.
The format of the file is:
		       username = value
		       password = value
This is preferred over having passwords in plaintext in a shared file, such as /etc/fstab. Be sure to protect any credentials file properly.
```

Taken from.. [mount.cifs]("http://h30097.www3.hp.com/docs/iass/OSIS_63/MAN/MAN8/0122____.HTM")

---

### Post by jaime256 on 2009-03-16
Kellems, thanks that does work, in the terminal as you mentioned which is what I asked for. Now I'm wondering if there's a way for the GUI part to ask you for the password before mounting? Mine doesn't do anything after the boot, but I'll double check this again. Let me restart again. Okay, I check and nothing happens no errors or prompt for the share password. I was playing with the custom application launcher, but that lets me put my local password, then it closes so I can't put in the share password. Any other thoughts to make this more beginner friendly. I'm just playing around with what may work. Thanks.

---

