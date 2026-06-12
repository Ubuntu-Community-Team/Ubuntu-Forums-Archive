---
title: "How do I make a folder on a remote machine into another Linux drive?"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by PiggiePaul on 2008-02-15
Please forgive my lack of the correct terminology (I'll get there one day!)

Running Ubuntu 7.1 (gutsy) I understand I can browse to a folder on a networked machine and somehow, make this into (what linux things) is another drive on my system

So I then appear to have a new drive and applications can access the drive (and files within) but in reality it's just a folder from a networked (windows in my case) machine.

I guess this is really easy, but as this is new to me, I'm not sure how to go about it.

Thanks.

---

### Post by HermanAB on 2008-02-15
It is really easy with NFS.  If you google for a NFS Howto then you'll quickly find an example.  NFS requires about 2 lines of configuration in /etc/export and /etc/fstab that's all.

Cheers,

H.

---

### Post by Discov3ry on 2008-02-15
Temporary solution:

```
mkdir -p /mnt/local_folder
mount -t cifs //windows_server/remote_share -o username=Myusername,password=Mypassword /mnt/local_folder
cd /mnt/local_folder
```

Permanent solution, edit the /etc/fstab and add (it's one line):
```

\\windows_server\remote_share /mnt/local_folder smbfs user,password=Mypassword,username=Myusername 0 0

```

Then run:

```
mount -a
```

---

### Post by PiggiePaul on 2008-02-15
Thanks to both of you for your advice.

Being a bit new to all this, which of the two methods would (should) cause the less problems?

My exact scenario is that I have a Windows PC on the same network, and on this PC I have a folder called music.

So, I just wish to make a music drive (if you call it that) in Linux.

Would software then know it's coming from a remote location?
I ask this as "Amarok" for some reason won't play files from this remote folder, yet other music player works fine.

---

### Post by Discov3ry on 2008-02-15
> **PiggiePaul said:**
> Thanks to both of you for your advice.

Being a bit new to all this, which of the two methods would (should) cause the less problems?

My exact scenario is that I have a Windows PC on the same network, and on this PC I have a folder called music.

So, I just wish to make a music drive (if you call it that) in Linux.

Would software then know it's coming from a remote location?
I ask this as "Amarok" for some reason won't play files from this remote folder, yet other music player works fine.

Both of those methods are good for a local home network. In both cases any application that will try to access the mounted directory will see it just as transparently as any other directory on a local system.

Try both of them as a learning example and decide which one works for you better.

---

### Post by dmizer on 2008-02-16
you said that the network share you want to access is located on a windows machine.  because of this, nfs will not work, as it is a linux specific protocol for sharing and mounting network drives.

the second method should work better for you.

---

### Post by PiggiePaul on 2008-02-16
> **Discov3ry said:**
> Temporary solution:

```
mkdir -p /mnt/local_folder
mount -t cifs //windows_server/remote_share -o username=Myusername,password=Mypassword /mnt/local_folder
cd /mnt/local_folder
```

Permanent solution, edit the /etc/fstab and add (it's one line):
```

\\windows_server\remote_share /mnt/local_folder smbfs user,password=Mypassword,username=Myusername 0 0

```

Then run:

```
mount -a
```

Thanks for that.
Now I'm probably being a bit thick here!

But, although I can see (understand) in your code above that I need to replace the words Myusername and Mypassword, with my real username and passwords.

What I don't actually understand is how do I point that code to a particular folder on the remote Windows machine?

For example.

Say my usernam was [COLOR="Blue"]pig[/COLOR] and my password was [COLOR="Blue"]banana[/COLOR] and on the remote drive I had a folder called [COLOR="Blue"]music[/COLOR] that I wanted this new (fake?) drive to represent.

The windows machines name would be named [COLOR="Blue"]house[/COLOR] and the 1st folder to get inside would be [COLOR="Blue"]shared files[/COLOR].

this is the current path to get to the music folder:

[COLOR="Blue"]smb://house/shared%20files/Music[/COLOR]

Thanks.

---

### Post by dmizer on 2008-02-17
> **PiggiePaul said:**
> this is the current path to get to the music folder:

[COLOR="Blue"]smb://house/shared%20files/Music[/COLOR]

Thanks.

you have a space in your remote share path "shared files" which is showing up here as "shared%20files".  this is going to cause problems with mounting your share.  i strongly urge you to remove the space, or replace it with a hyphen or underscore:
shared-files
shared_files

then your manual mount command will look like so:
```
mount -t cifs [COLOR="Red"]//house/shared-files/Music[/COLOR] -o username=[COLOR="Blue"]pig[/COLOR],password=[COLOR="Blue"]banana[/COLOR] /mnt/local_folder
```
and your fstab line will look like this (i've changed the fstab line for cifs instead of smbfs):
```
[COLOR="Red"]//house/shared-files/Music[/COLOR] /mnt/local_folder cifs user,password=[COLOR="Blue"]banana[/COLOR],username=[COLOR="Blue"]pig[/COLOR],file_mode=0777,dir_mode=0777 0 0
```

---

### Post by PiggiePaul on 2008-02-19
Thanks.

I'm really not having much luck with this.

Perhaps I need to take a few steps back as I think people here sometimes might assume we know things we don't :)

First problem (when the command line approach) it it says I have to be root.

I added the sudo command in,and still get errors such as:

No ip address specified and hostname not found
Mounting the DFS root for a particular server not implemented yet

This is when I try:

sudo mount -t cifs //NAME OF SHARED FOLDER ON PC -o username=USERNAME,password=PASSWORD /mnt/pc-folder

---

### Post by Discov3ry on 2008-02-19
You're missing the windows server name. 

Try this:

sudo mount -t cifs //WINDOWS_SERVER_NAME/NAME OF SHARED FOLDER ON PC -o username=USERNAME,password=PASSWORD /mnt/pc-folder

---

### Post by PiggiePaul on 2008-02-19
> **Discov3ry said:**
> You're missing the windows server name. 

Try this:

sudo mount -t cifs //WINDOWS_SERVER_NAME/NAME OF SHARED FOLDER ON PC -o username=USERNAME,password=PASSWORD /mnt/pc-folder

Thanks. That was my fault when I edited out my "personal" details... Doh!

Did the line about (with the right names) and got:

mount error: can not change directory into mount target /mnt/pc-folder

---

### Post by dmizer on 2008-02-19
```
sudo mount -t cifs //WINDOWS_SERVER_NAME/NAME OF SHARED FOLDER ON PC -o username=USERNAME,password=PASSWORD [COLOR="Red"]/this-EMPTY-folder-must-exist/on-ubuntu[/COLOR]
```

---

### Post by PiggiePaul on 2008-02-19
Ah, didn't realise that....!  ;)

Ok, corrected, but :(

mount: wrong fs type, bad option, bad superblock on //COMPUTERNAME/FOLDERNAME,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This is NTFS on a Windows 2000 PC.

Odd thing is, if I put the same COMPUTERNAME and FOLDERNAME into the "Connect to server" program on the PLACES menu, it opens it straight up.

---

### Post by dmizer on 2008-02-19
what is the output of this command:
```
sudo aptitude install smbfs
```

---

### Post by PiggiePaul on 2008-02-20
Thanks for the suggestion, I shall try that (and report back) later.

Something odd though.

And I can't be precise with my description as I'm not by my PC now, but late last night I tried a new program.

It was on the same drop down menu as Home, Bookmarks, Network.

Called something like remote computer (probably not!)

But I ran it, and it asked for details of names of machines on your network, folder to share and your username etc.

Next thing I know, it created a mounted drive icon on my ubuntu desktop!

Clicked this and my remote folder popped up perfectly.

I right clicked on on, and it had a "unmount drive" option (which I did not use)

I then rebooted, and yes it survived a reboot.

So, (it seems) I now have a mounted icon on my desktop that leads to my remote folder on my PC.

(will know if it's still there tonight after a cold start/reboot)

The odd thing is, I've no idea where this is in the file system, as I hunted and I could not find this shared (mounted) drive/folder anywhere on my system. Even though it was starting me in the face on my desktop.

---

### Post by PiggiePaul on 2008-02-20
> **dmizer said:**
> what is the output of this command:
```
sudo aptitude install smbfs
```


[sudo] password for USERNAME:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  kcontrol kdebase-data kfind kicker 
The following NEW packages will be installed:
  smbfs 
0 packages upgraded, 1 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B/485kB of archives. After unpacking 32.1MB will be freed.
Do you want to continue? [Y/n/?] 

I answered NO (just in case!)

I'd like to know whats going on exactly before I say yes to it.

---

### Post by dmizer on 2008-02-20
the reason you got this error:
> **PiggiePaul said:**
> mount: wrong fs type, bad option, bad superblock on //COMPUTERNAME/FOLDERNAME,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
was because you did not have this program installed:
> **PiggiePaul said:**
> The following NEW packages will be installed:
  smbfs 
0 packages upgraded, 1 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B/485kB of archives. After unpacking 32.1MB will be freed.
Do you want to continue? [Y/n/?]

I'd like to know whats going on exactly before I say yes to it.

"sudo aptitude install smbfs" does what it says.  it is using the program aptitude (which is sort of like windows add/remove programs) to install the program smbfs.  smbfs is the samba file system metapackage which includes (among others) the necessary programs for mounting smbfs as well as cifs.  if you want, you can do the same thing through the gui by going to administration > synaptic package manager, and searching for smbfs to install it.

you'll notice now that since you created a share on your desktop via the gui, that you will be able to browse the share, but that many programs, like amarok and openoffice, will not be able to see the files on that share.  we have been trying to give you directions for mounting your share via the command line because that is the only way for it to work for all programs.

if you would like to try one more time with cifs, install smbfs, and then post the output of the following command:
```
smbtree
```

---

