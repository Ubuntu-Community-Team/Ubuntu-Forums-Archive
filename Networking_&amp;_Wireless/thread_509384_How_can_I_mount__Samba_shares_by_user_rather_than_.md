---
title: "How can I mount  Samba shares by user rather than FSTAB?"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by kevindontenville on 2007-07-25
I have a simple LDAP backend SAMBA setup and I want to enable users to mount shares to mount points under their Home directory at login.  

Currently Linux users are mapping Home drives with an NFS export and now I want them to run some kind of script to mount Samba shares that they have rights to. The shares vary by user more than machine so FSTAB becomes a mess.  

Thoughts I had:
1) a file that could be @included in FSTAB with specific mounts for the user based on the home directory.
2) a login script that runs using eg smbmount called on a per user basis.

Either of these might work but so far I cant find examples of them anywhere. Plenty of Windows based logon scripts and instructions on FSTAB with a credentials file etc but these don't seem to apply. Is there a simple way to draw on the environment variables such as USERNAME and PASSWD etc in either FSTAB or a script?

Any pointers would be great, even those already right under my nose!

K

---

### Post by DugieHowsa on 2007-07-27
I had been having trouble mounting a Windows Share. I tried to mount using smbfs. I tried to mount using cifs. In the end, some one showed me this link:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary: "smbfs is unmaintained and known to be severely broken." That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

So here is the man page for mount.cifs that lists all the options:

[http://www.die.net/doc/linux/man/man8/mount.cifs.8.html](http://www.die.net/doc/linux/man/man8/mount.cifs.8.html)

Many people here have also listed many good posts, giving several good examples, on how to properly utilize cifs:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

This post solved the particular problem I was having:

[http://ubuntuforums.org/showthread.php?t=483184](http://ubuntuforums.org/showthread.php?t=483184)

In summary: USE CIFS. DO NOT USE SMBFS.

---

### Post by kevindontenville on 2007-07-31
Thanks for that, I have found a couple of them before but although I found a reference to username%password to set the username/passwd to the environment variables of the current user they dont seem to work. At least if they do I havent fathomed the syntax yet!

What I want is to create a login process that mounts CIFS shares based on username not tied to the machines FSTAB lines. 

In windows the equivalent to this could be done with a netlogon login script with a line like:

net use M: \\servername\share

and it would use the current user and password to 'map' the share to a drive letter. 

If I use nautilus to browse the network the current credentials are passed and I can connect to the shares without entering them directly. If I run a command like:

sudo mount -t cifs //netbiosname/sharename /media/sharename iocharset=utf8,file_mode=0777,dir_mode=0777

I get nowhere, not even a request for password (other than the sudo one).

After I get that type of line to work, then I could produce a script, tie it to the user in LDAP and find a way around the problem of root being required to execute mount commands.... maybe then I'd be happy ;-)

Any more thoughts?

Thanks!

---

### Post by kevindontenville on 2007-08-06
I have been scanning around and looking for solutions from all over, Fedora, Novell, Debs, etc. 

Well so far it seems Linux doesn't really have support for this type of operation, at least not without hacking and weakening security by allowing users full sudo access to mount files systems at least for a timeout period or longer. Other ways are to load all possible mounts in FSTAB and permit on user authentication and samba controls. Doesn't help with common mountpoints pointing to different filesystems or shares. Or may be possible by seriously customizing the client workstation and creating an easily broken environment.

This whole area seems to me to be a major problem in using Linux in the real wider world. In the real world, Linux OS needs to interoperate with Windoze Network environments in a more analogous way than they do at present. Samba is good and technically very interesting and is part of the answer but it is still far from really meeting the needs of supporting or helping manage a mixed network environment.

What's sad is I can't see anyone in the opensource environment doing any of this stuff. My desire was to setup a mixed home network that would show me how it could work and where the limitations are. Sadly, although I can connect to windows shares, offer windows shares and centralise secure authentication, I can't specify by user how to connect to many of those resources without prejudicing security or at least reducing it to Windoze! 

I have found many applications wont 'see'  or browse SMB shares unless they are mounted it kind of reduces their benefit. Under gnome I can simply connect to, eg a share that offers music but none of the main players out there will read the files to a library db! Albeit that it is possible to find a file and open it directly by association! Bookmarks are great for finding the share, but otherwise of limited use within many apps. Why can't I when logging on, properly mount a share for use in my session without manually sudoing.

Have I got all this wildly wrong? Maybe comments to this thread will be scathing and show me the error of my ways, or perhaps there will be none showing that perhaps no one has an answer - yet!

Thanks for reading!

K

---

### Post by netztier on 2007-08-06
> **kevindontenville said:**
> Either of these might work but so far I cant find examples of them anywhere. Plenty of Windows based logon scripts and instructions on FSTAB with a credentials file etc but these don't seem to apply. Is there a simple way to draw on the environment variables such as USERNAME and PASSWD etc in either FSTAB or a script?


Well, since you already have NFS-mounted home directories, what would be wrong by having the machine mount any share that's needed and keep it mounted (regardless if any user is logged on or not),  and then offer the user some symlinks to "his" directories on the mounted shares?

Each user can get a "data" directory within his home - symlinked on a per user basis, for example:
[LIST]
[*]let "userdata" be a share on  \\server, containing each a subdir per user (userA, userB, userC)
[*]mount \\server\userdata to /mnt/userdata
[*]create some symlinks in each user's home directory:
[INDENT]/home/userA/data -> /mnt/userdata/userA
/home/userB/data -> /mnt/userdata/userB
/home/userC/data -> /mnt/userdata/userC
[/INDENT]

[/LIST]


Like this you can achieve the goal that each user sees his ressources under /home/... - which is a sensible thing to do, IMHO. And as a plus, you avoid the trouble of mounting/unmounting network ressources with each login/logoff - they just stay mounted. 

I wouldn't complain too much about a user's inability to mount/unmount network ressources - I can see that there's drawbacks - but even without knowing it myself, I bet there's quite a good reason  to restrict this to root.

The other thing (that apps can't see what you mount via Gnome-VFS, aka "Connect to Server...") must be related to the relatively young age of this feature. As little as I know about it, I believe that applications need to be explicitely made VFS-aware when they are written or at least recompiled. Some actually are - such as Gnome's text editor, OpenOffice or Totem, the movie player. Others aren't (yet), including Firefox, Inkscape or The Gimp.


best regards

Marc

---

### Post by kevindontenville on 2007-08-07
Thanks Marc, I had thought similarly about the further use of NFS and to have someone else lay it out so clearly is very welcome :-)

On the further use of NFS I also started reading about it in a little more detail, and kept coming up with the comments that ordinarily it suffers from poor security and reduced performance when scaled and is only really useful in protected LAN environments when its weaknesses can be more readily managed. Apparently, it is possible to toughen it up and tune it but it is not a modern technology nor has it evolved greatly to manage locking and access controls such as are found in other closed source environments. I don't claim knowledge here just the partial ability to read...

Samba seems to be the most likely common standard to get by on except for this user based scripting thing. Lots of solutions getting part way but none getting there! Perhaps I am asking the wrong questions of the technology or trying to do something in a way that is just not sensible?

One thing that I noticed and followed up on a bit, was OpenAFS which has a number of features that sounded interesting that made it good for distributed wide area networks, resilient to failures and scalable. Seems like a modern take on NFS so may be a solution to incorporate your suggestion and be cross platform. So far I find it in the Ubuntu repositories but havent found anything resembling a Howto or even a note form 'this is what I did' page that shows anything about installing the server. 

I think I will have a go and see what I can do. It says it has Linux, Mac and Windows clients ready now, anyone out there done anything with OpenAFS before? Does it do what is says on the can? 

Thanks for helping Marc - any more information or comments still gratefully received ;-)

---

### Post by spikyjt on 2007-11-12
I'm very glad to see that someone else is trying this. I have been banging my head against this particular brick wall for the last few days! 
It is possible using libpam_mount, however this is not very reliable. It doesn't work for ssh (which I need) and doesn't umount on some protocols.
Any other script will need the user's password to be stored somewhere, which could be a security issue and would be a pain in the butt when the password is changed.
Samba really needs to have the ability to mount shares as a root user and then honour the permissions set by the unix CIFS extensions. Sadly it doesn't. Maybe the CIFS protocols says it shouldn't.
I'd be interested to know if you have got any further with this, or if you had any success with AFS. I have also thought about AFS before but also got put off by the lack of documentation and other user recommendation (its always nice to know that other people are actually using something).

Clearly NFS is not the answer if you are ever going to have a windows box on your network/domain. I have had trouble in the past with directories that where shared out by both NFS and Samba. Samba locks a file but then NFS merrily ignores that and accesses the file anyway. This causes lots of smbd processes to hang - and they never go away, you can't even kill them. Although NFSv4 apparently has locking, will it play nicely with Samba? I tried sshfs also, but this has the same permissions problems as Samba (and may not do any locking - I was going to find out but didn't get that far).

I've tried playing with Xstartup/Xreset scripts but hit the same wall.

I shall start having a bash at AFS unless anyone can suggest anything better...

---

