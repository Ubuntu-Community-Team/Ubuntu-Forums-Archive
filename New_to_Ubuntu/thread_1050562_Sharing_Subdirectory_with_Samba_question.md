---
title: "Sharing Subdirectory with Samba question"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by AndyInNYC on 2009-01-25
I have a directory shared with SAMBA.  this directory is mounted in fstab

/media/RAID and is shared as [Data]

No problem on any machine.

I would like to give my family access to a subdirectory off of RAID.  Do I need to mount this drive and in order to share it?

Example:
in my smb.conf I have 

[data]
path = /media/RAID
available = yes
browsable = yes
public = yes
writable = yes
comment = Data on Server

I'd like to do:

[datastore]
path = /media/RAID/DataCenter
available = yes
browsable = yes
public = yes
writable = yes
comment = Group Shared

the DataCenter is a subdirectory off of RAID.  It seems that since /media/RAID is already mounted, I shouldn't have to mount a subdirectory, but what do I know?

So, what's my solution?

Thanks all.

Andrew

---

### Post by blueridgedog on 2009-01-26
> **AndyInNYC said:**
> I have a directory shared with SAMBA.  this directory is mounted in fstab

/media/RAID and is shared as [Data]

No problem on any machine.

I would like to give my family access to a subdirectory off of RAID.  Do I need to mount this drive and in order to share it?



If they mount your share by going to \\yourserver\Data, then they should be able to get to all subdirectories of /media/RAID

> 
[data]
path = /media/RAID
available = yes
browsable = yes
public = yes
writable = yes
comment = Data on Server

I'd like to do:

[datastore]
path = /media/RAID/DataCenter
available = yes
browsable = yes
public = yes
writable = yes
comment = Group Shared

the DataCenter is a subdirectory off of RAID.  It seems that since /media/RAID is already mounted, I shouldn't have to mount a subdirectory, but what do I know?


If you want your users to be able to mount directly to /media/RAID/DataCenter as a mount point or as a mapped drive letter in the case of windows, then yes, you will need to reshare it.  If you are content to have them mount/mamp your first share, then navigate down into the DataCenter directory, then your current setup is great.

---

### Post by AndyInNYC on 2009-01-26
What I want is for the X: drive to map directly to the /media/RAID/datacenter (ie they don't get to see subdirectories hanging directly off RAID other than datacenter.

So, if I understand, for 'me' I map to /media/RAID and create a new fstab mount point of /media/RAID/datacenter for 'lesser' users to map to directly and then my share will have a

[EveryoneElse]
path = /media/RAID/DataCenter
available = yes
browsable = yes
public = yes
writable = yes
comment = A family share which segregates work data

and then all my users will only see the branch, but not the root of the shared RAID 'master' share.  This would allow me to create lots of sub shares off RAID for other users (pictures only, video only, etc.) to make the locations 'cleaner' for a user and for backups.

Thanks

Andrew

---

### Post by blueridgedog on 2009-01-26
You have it right, but the fstab comment throws me a bit.  You will create the share much like you describe and remote users will mount it (possibly through mount entries in fstab, or through other means).  They either will mount the upper share by connecting to \\yourserver\data which locally connects to /media/RAID or they will coneect to \\yourserver\datastore (you called it \\yourserver\everyonElse above) which locally connects to /media/RAID/DataCenter.  Like I said, I think you have it.

---

### Post by AndyInNYC on 2009-01-26
OK, let me simplify

I have a 3 TB RAID array on the equivalent of sda1

I did the following:

mkdir /media/RAID
and then in my fstab I have
/dev/sda1    /media/RAID ext3 auto 0 0
or whatever the correct syntax of the above is

in my smb.conf I have a section
[data]
path = /media/RAID
...



So lets assume that data refers to the root of the 3TB drive
I can now connect through windows to the root level of this drive using the above.

I now want to restrict users to a branch of this 3 TB drive.  Specifically the subdirectory DataCenter which is 1 level off the root.  I don't want the kids having access directly to the bottom level since that would give them access to all the work files (and the potential to accidently hit the delete key).

So, to rephrase, do I need to do the following:

mkdir /media/MountPoint

then edit fstab
/dev/sda1/Share /media/MountPoint .......

and then in smb.conf
[EveryoneElse]
path = /media/MountPoint

?

I'm still really confused.

---

### Post by Hobgoblin on 2009-01-26
The share points in samba have nothing to do with the ones in fstab.  You can create a samba share for any pathname on your system.

Just put the full path you want them to root to against "Path ="

But unless you put some restrictions on who can mount your /media/RAID then everyone will be able to mount it.

---

### Post by blueridgedog on 2009-01-26
samba and fstab are unrelated (as the above posted stated).  If your /dev/sda1 drive is mounted at /media/RAID then you can share paths in samba from /media/RAID on down the directory tree.

---

### Post by AndyInNYC on 2009-01-27
OK,

I've fixed my issue.  I had a typo in the path = section.
I can now attach and everyone *should* be happy.

Now that I've set up the array and copied all my data, is there a way to go back and add either full or partial encryption without losing the data on the 'new server'?

I'd like to store tax returns, etc. on the array, in a privileged area with a disk wide encryption (or a folder wide).

I know nothing about TruCrypt, but that seems to the most likely candidate.

Any thoughts?  I'm happy to make this into a new thread if that's my best option for getting the thoughts of the talent on this site.


Andrew

---

