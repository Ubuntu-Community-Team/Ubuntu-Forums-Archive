---
title: "Questions about NFS"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by jackn on 2007-07-24
I've followed two good, helpful how-to's about nfs-mediated filesharing, by [Hartz]("http://ubuntuforums.org/showthread.php?t=444691&highlight=add+%2Fetc%2Fhosts+network") and by [malco2001]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto").

I can now share files between two boxes running Feisty, a pleasure.

Questions:
1. In general, I can browse any files or directories within a shared directory:

```
$ ls /mnt/midbar/root/
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old
```

I can go further down into almost any directory:

```
$ ls /mnt/midbar/root/media/
cdrom  cdrom0  fedora  fedora_home  sda1  sda2
```
 
The /home directory in the above shared (root) directory, however, is located on a partition of its own. In that case, and in contrast to the case with the /media directory, I cannot browse any further:

```
$ ls /mnt/midbar/root/home/
$ 
```

This can be taken care of by exporting and mounting /home separately:

```
exprtfs client:/home 
```on the server side, and
```
mount -t nfs server:/home client_mouint_point/home
```
on the client side.

Once I do that, I can freely browse this directory, too:
```
$ ls /mnt/midbar/home
jacknn  lost+found  padavoine
$ 
```

In short, recursive browsing works only within a partition. If a directoy within the shared directory is on a separate partition, it won't be accessible, unless exported and mounted independently.

Is it posible to allow access to all partitions with a single mount?

This was also observed by [jabb]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto") and george_apan in one of the above threads.

2. How can I use nfs filesharing to allow network printing? I haven't been able to set it up through IPP and CUPS, and until I can, this could be a handy workaround.

3. Some remarks [by dgermann]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto&page=3") and in this thoroughgoing nfs [how-to]("http://nfs.sourceforge.net/nfs-howto/ar01s07.html") suggest that the user or the user ID needs to be the same on the two boxes. When I set up my user on my second box, I chose a different username than the first. Is that wrong? Are there purposes for which this is an obstacle? Can I have the same username and is it in some sense better?

Thanks, 
Jackn

---

### Post by Mr. C. on 2007-07-24
1) See

```
man 5 exports
```

Search for the **nohide** and **crossmnt** options.

2) Unless your printer speaks the NFS protocol, no dice.  NFS != Windows File and Print sharing

3) The username in the password file is irrelevant.  The UIDs must be the same.  Explaining why this is the case requires understanding the Unix permissions model for processes and files, **inodes** and how NFS is implemented atop of the file system layer, in a layer called VFS (virtual file system).  Since file permissions are stored in the inode, and user/group permissions stored in a process's space, it is more natural to simply uses Unix's permission model on both ends.  When the platforms are the same, permissions, owners, and users are the same.  It was much easier to manage UIDs across multiple platforms (via the invented YP, now called NIS), than it is to create an entirely new security mapping protocol (consider how difficult it is in samba to map windows <-> Unix permission and user models).

MrC

---

### Post by jackn on 2007-07-25
I'm grateful for this informed and prompt reply, MrC, and I shall be sure to study man exports (5).

I don't know enough, I'm afraid, to follow answer 3, but the bottom line I come away with is that UID's must be the same.
What does that mean?
Does it mean that I can only browse box 2 if the logged on user has the same UID, be it my own user or another? I'm a bit surprised here. 
I think that by chance, my user ID's on my different boxes are the same, though my user names aren't. But if my son, another user, were logged on to box 2, then I wouldn't be able to browse it, given that his UID is different?

Finally, I would like some input, if you would, on whether I should have set up my user on box 2 with the same username as on box 1 for some reason.

Thank you very much again, Mr.C.

Jackn

---

### Post by Mr. C. on 2007-07-25
Jackn,

Consider two machines, an NFS file server named "server", and and NFS client name "client" (I'm so original).

If a file *somefile* on server is owned by UID 1000, GID 100, and the password entry in /etc/passwd looks like (we'll ignore the /etc/group file for now):

```
jackn:...:1000:100...
```

then and ls -l command from server would show the user name and group, which are taken directly out of the passwd and group file:

```
$ hostname
server
$ ls -l somefile
-rw-r----- 1 **jackn  users** 956 Jul 24 07:36 somefile
```

More revealing is when we suppress ls' UID/GID name translation:
```

$ ls -ln somefile
-rw-r----- 1 **1000  100**  956 Jul 24 07:36 somefile
```

Now, lets assume you've mounted server's filesytem onto client, and you perform the same operation.  However, on client, let's suppose two passwd entries look like:

```
fred:...:1000:100...
jackn:...:2000:200...

```

The same commands run on server, now run on client reveal:

```
$ hostname
client
$ ls -l somefile
-rw-r----- 1 **fred  others**  956 Jul 24 07:36 somefile
```

But of course when we suppress ls' UID/GID name translation again, we see the UID/GID are the same.
```

$ ls -ln somefile
-rw-r----- 1 **1000  100**  956 Jul 24 07:36 somefile
```

So, which user, fred or jackn, can actually can write the file on client ?  It turns out, it will be fred, because fred has UID 1000.  Internally, Unix/Linux *always* uses UID/GIDs.  Names are a convenience for users and are not used by the kernel.

The lesson here - only share NFS file systems on machines for which you control the passwd and group entries, and make them the same on all machines.  This is done typically by (manually or automated) file copy or entry synchronization. or by using a lookup service such as NIS, NIS+, or LDAP. 

For a little more detail on file permissions, etc., see week 2's notes and homework: [http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/), for file systems: week 4 File systems: [http://cis68c1.mikecappella.com/](http://cis68c1.mikecappella.com/), and for NFS, week 4 coursework and labs: [http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)


MrC

---

### Post by jackn on 2007-07-25
OK, the point about UID's and user names is now crystal clear to me. 

What does it mean in practice? I understand the recommendation to only nfs share when having full control of the machine, in particulr over UID's and GID's. If I have it right, then, I should be able to mount no problem whatever the user logged on on the server is - the config files (/etc/exports and /etc/fstab) are system-wide, and only refer to the boxes, not any individual users. I may, however, run into permission issues if the UID's (what I think of as my own user's, on the two different boxes, or simply my own on the client and some other user's on the server) are different. In a nutshell, once an fs is shared, it is in principle no different than any part of your local fs - your access is determined by the owner's UID and by permissions.

Below, I post a brief discussion of the nohide option you mentioned.

Mr.C, I'm grateful for this instruction and for the reference to the course on Unix. The course contains lectures and assignments with answer keys. I do hope to use it in my learning of *nix systems.

Thank you.

Jackn

---

### Post by jackn on 2007-07-25
Here's the lowdown on the nohide option. This is one of the options available to you when exporting a file with nfs filesharing. You edit your entry in /etc/exports to add or remove options.

Here's a slightly edited and commented version of what man 5 exports has to say about it: 
> 
[COLOR="Red"] nohide 
             Normally, if a server exports two filesystems one  of
              which  is  mounted  on  the  other, then the client will have to
              mount both filesystems explicitly to get access to them.  If  it
              just  mounts  the  parent, it will see an empty directory at the
              place where the other filesystem is mounted.  That filesystem is
              "hidden".[/COLOR]

This is a confirmation of the observations in question 1 which started this post. In general, a typical home user may run into this situation if she has parts of her fs, say /home, mounted on a partition other than the root parition. This is often recommended.

  > [COLOR="Red"]           Setting  the  nohide  option on a filesystem causes it not to be
              hidden, and an appropriately authorised client will be  able  to
              move  from  the  parent  to that filesystem without noticing the
              change.

              However, some NFS clients do not cope well with  this  situation
              as,  for  instance, it is then possible for two files in the one
              apparent filesystem to have the same inode number.[/COLOR]
              
So, in principle, the nohide option allows you to easily set up recursive browsing even though a subdirectory might be mounted separately. 
The caveat on inode (user, group and mode) numbers, however, is not clear to me. 
Why does freely browsing the apparently unified filesystem make it more likely to have identical inode numbers? What am I missing?
In any case, I'm going to tentatively experiment with nohide, and hope for the best...

Here are other caveats to bear in mind:
> [COLOR="Red"] The nohide option is currently only  effective  on  single  host
              exports.   It  does  not work reliably with netgroup, subnet, or
              wildcard exports.

              This option can be very useful in some situations, but it should
              be used with due care, and only after confirming that the client
              system copes with the situation effectively.[/COLOR]

Finally, 
              > [COLOR="Red"]The option can be explicitly disabled with hide.[/COLOR]

I will be sure to report further if anything of interest happens with nohide.

I enjoy roaming the net and the forums, but more and more I realize that I should first read those grey, spare manual pages. 

The info above was garnered thanks to Mr.C's reference.

---

### Post by sgbotsford on 2007-07-31
NFS and NIS go together.  Users must have the same UID on all machines. Using NIS is the easiest way to do this.  As an alternative, you can write a bunch of scripts that copy information back and forth, but if you have more than 3-4 computers this gets out of hand in a hurry.

Organizing your exports on the server is a critical step.  The use of the nohide option I think will bite you.  In general you don't want to have nested NFS mounts.  They tend to be slow.
(Anything on the second mount requires more network reads to find it.)

Also:  Avoid cross mounting if you can.  (machine A mounts B:/home on /home.  Machine B mounts A:/usr/local on /usr local)  If you do this, then make sure that at least one of them is set to run the mount in background (usually the /home one.) Else getting everything going after a power outage can be interesting, as each one waits for the other one to come up.

NFS depends on the network.  Most of the time network speeds are slower than disk speeds.  So access tends to be slower.  Exception:  If I have a honking big server with oodles of ram, and lots of users it may be faster to get a file from that server than it is from my local disk. The server may have that file in memory already (because someone else just used it.) and it probably has high performance disks.

One of the down sides of NFS is that if the server goes down, any process on the client that tries to access an NFS file will hang until the server comes back up.  I made the mistake once of changing an export on a server, and not notifying all the users of client computers.  I had to manually go around and reboot some 150 computers.  My users were not happy with me.

There are various ways around this.  None of them are foolproof (fools are way too clever)
Some versions of NFS have a mount option intr for interuptable.  This allows you to stop hung processes, but you will lose any data they were trying to save.  If you use automount, then file systems are mounted on demand, and unmounted when inactive for a period of time.  This decreases the window of vulerability, but is only useful if your users actually log off now and then.

I've seen notes suggesting that using CIFS (Samba) may work in a more robust fashion.

NFS made sense when disks were very expensive, and networks were fast compared to disks, and computers were used by many people each.

Now a days I think that most users have their own machine that they use 95% of the time.  
Disk space is cheap.  It makes more sense to store your data locally, and use a program such as rsync to periodically syncronize your local data with that of the server.

OR 

Run diskless clients.  All the programs run on the server,  the client only runs an interface for the user.

---

### Post by jackn on 2007-08-02
I wasn't able to answer right away, sgbotsford.

This is very enlightening to me, and I really appreciate it. I find sys admin very interesting, and I only have the experience of a personal user.

First, I understand that nfs can be used in a central, always-on server and networked clients situation, what we are all used to seeing at the workplace. I was wondering about that, as I didn't know how this was done. I don't have an always-on server. Rather, I have two networked boxes, and I wanted to be able to browse either one from either one when both are on. And to play with Linux and learn.

So, how is a central server situation set up? My understanding from your message is that all the users' data is permanently stored on the sever, and when they log in, their data is exported to them. Is that right? Where is their data mounted on their fs? In other words, how is it made invisible to them? What about login management? nfs doesn't seem to take care of that...

I believe I understand your discussion of whether nfs is the right solution for a many-user situation.
Basically, because of speed considerations and server crashes, you recommend storing things locally with regular backups to a server or using thin clients.

In light of your discussion of nfs crashes, I've studied the intr option. Indeed, at the time of setting up nfs, I basically ignored this option, as I didn't understand it. I feel I do undestand it now. Importantly, it is the default...

Finally, not knowing any better, I've already set up different usernames on my two boxes. Worst is, for some reason, I thought I *had to*, although it felt more convenient to keep the same username... I mean to set this straight, but I need to study how to change usernames...

Thank you very much, sgbotsford, for sharing.

---

### Post by sgbotsford on 2007-08-07
> 
First, I understand that nfs can be used in a central, always-on server and networked clients situation, what we are all used to seeing at the workplace. I was wondering about that, as I didn't know how this was done. I don't have an always-on server. Rather, I have two networked boxes, and I wanted to be able to browse either one from either one when both are on. And to play with Linux and learn.

****
The normal situation is that the server runs 365/24/7.  Since the problem will occur on the client, you need to set the client up to do some things manually.
E.g.  While the otherbox's nfs exported file systems can appear in localbox's fstab, they should have the flag noauto.  This means that when localbox boots, it won't try to mount file systems from otherbox.

Suppose that you export /usr from otherbox.  The entry in localbox's fstab would look 
somthing like this:
otherbox:/usr  /other/usr nfs bg,noauto 0 0

When you wanted it, you would type:
mount /other/usr

> So, how is a central server situation set up? My understanding from your message is that all the users' data is permanently stored on the sever, and when they log in, their data is exported to them. Is that right? Where is their data mounted on their fs? In other words, how is it made invisible to them? What about login management? nfs doesn't seem to take care of that...


If you are just playing, don't keep your home directory on another server.  This system was created for the situation where on Tuesday you log in to the 3rd machine in the 4th row in lab 22, and on Wednesday you log in to a different machine somewhere else.  

> I believe I understand your discussion of whether nfs is the right solution for a many-user situation.
Basically, because of speed considerations and server crashes, you recommend storing things locally with regular backups to a server or using thin clients.


It's the right solution when people are moving around a lot.  Local storage with copy back is better when you use one machine nearly all the time.  Thin clients make administration easier because the clients almost never change.  You essentially trade administering 30 individual computers for adminstering one honker in a server room.

If you are big enough to require multiple servers, then there is another whole set of tradeoffs for speed (everything is on a local disk, with updates moving back and forth) versus simplicity (everything stored once, but slower)  For really large institutions, AFS (Andrew file system) has a lot of merit.  It is truly a network file system with chunks living at various levels, and caching  happening at the local machine, and intermediate server, or your main server.  I think that it can be set up so that if you login several times through a server that is not 'near' your home server, it will migrate your files to the local server.  I looked at tit once.  It's non-trivial to set up, but has huge advantages if you are talking about a university campus with everyone logging in everywhere.

> In light of your discussion of nfs crashes, I've studied the intr option. Indeed, at the time of setting up nfs, I basically ignored this option, as I didn't understand it. I feel I do undestand it now. Importantly, it is the default...

Interuptable mounts are a kludge solution.  A better solution would be to have a system where you can go offline, and copy back when the server comes back.  This situation will become more critical as more and mroe people have an intermittent wireless connection.


> Finally, not knowing any better, I've already set up different usernames on my two boxes. Worst is, for some reason, I thought I *had to*, although it felt more convenient to keep the same username... I mean to set this straight, but I need to study how to change usernames...


To change usernames: 
You will have to be root to do these changes;

1.  Manually change the name of the home directory to match your new name. (By convention, your login name is also the name of your home directory.  It doesn't have to be, but it saves lots of grief if you keep to this convention.)
2.  Edit /etc/passwd and change the username to the new name.  This name occurs in two places, as the first field in the line, and as the home directory.
3.  Edit /etc/shadow and change the username to the new name.
4.  If you have a different UID on this machine, then when you do steps 2 and 3, change the UID and GID to match when editing /etc/passwd.
5.  Check that the changes worked by typing id mynewname in a terminal window on that machine.
6.  If you had a different UID or GID, type the command
chown -R UID.GID ~mynewname
where UID and GID are the new user ID and Group ID of your user.

Hope this hleps.

---

### Post by jackn on 2007-08-07
This helps a great deal, sgbotsford.

I appreciate your time, and the detail and clarity of the instructions.

jackn

---

### Post by clblanchard on 2007-08-16
[QUOTE=jackn;3074953]
I can go further down into almost any directory:

```
$ ls /mnt/midbar/root/media/
cdrom  cdrom0  fedora  fedora_home  sda1  sda2
```
 
The /home directory in the above shared (root) directory, however, is located on a partition of its own. In that case, and in contrast to the case with the /media directory, I cannot browse any further:

```
$ ls /mnt/midbar/root/home/
$ 
```

As I was reading this thread I just started to wonder if you could use a symbolic link to the home dir?  As I understand them they can "see" into other partitions right?  Just a thought.

---

