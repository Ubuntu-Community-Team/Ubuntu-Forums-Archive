---
title: "Easiest file sharing method for Ubuntu to Ubuntu network?"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by Rubicon421 on 2008-11-16
OK, I have read several posts on this and am looking for the simplest solution:
I have 3 computers with Ubuntu 8.10. I only want to be able to access files between each one, I don't need to have write privileges.  I have Samba on each, and have file sharing enabled in the default file sharing app that comes with Ubuntu. Yet, I don't see anything shared in any of them except the printer. I can see the other computers though. 
I would really like to get it to work with the file sharing option in System>Preferences> File Sharing. If not, Samba would be ok since it is installed. Also, a solution that doesn't require changing users would be the best.

---

### Post by Rubicon421 on 2008-11-16
I have tried with the file sharing option in Ubuntu and get a message that reads:
Unable to mount location - Invalid Reply

Also, one of the computers is a laptop and I would like it to work through the wireless router, but if I can get it working only in the 2 wired computers that would be fine for now.

---

### Post by SIGTERMer on 2008-11-16
you have to install samba, and then configure it

sudo apt-get install samba

then add users by typing 
sudo smbpasswd -a username

* make sure that username is also a real user (you can log into your pc with it)

---

### Post by Rubicon421 on 2008-11-16
Like I said, I have Samba installed and have added folders to the share on each. But the only thing that is displayed as shared is the printer.

---

### Post by SIGTERMer on 2008-11-16
sorry i have a twitchy finger and posted the reply before finishing (read the edit :) )

share the folder by right-clicking it, and selecting "sharing options"

hope this helps :)

---

### Post by Rubicon421 on 2008-11-16
That option isn't there when I right click, nor is it in the folder properties menu from one of the computers. The other one has that option though. Is there s user setting on the one that doesn't have the option that will add it?

---

### Post by SIGTERMer on 2008-11-16
try running nautilus with root permission:
sudo nautilus
then try right-clicking it

---

### Post by Rubicon421 on 2008-11-16
Well, we're getting somewhere.... Now the shared folder shows up on the other computer but I still get the same error when I try to open it- unable to mount location - invalid reply.

---

### Post by SIGTERMer on 2008-11-16
sorry man, but i never had that problem before... :(

---

### Post by SIGTERMer on 2008-11-16
just to make sure..
1- have you installed samba on all the computers you intend to share from
2- have you created smb users on each of these pcs
3- have you set sharing options on the folders
-- not smb specific --
4- can you ping the computer you want to connect to
5- don't really know if this will help but.. try stopping all services and then restarting them (sudo init 1) then select start normally..

---

### Post by Iowan on 2008-11-16
Not to add more confusion to the mix, but...
[NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") and [SSHFS]("https://help.ubuntu.com/community/SSHFS") are a couple more options for sharing between Ubuntu machines.

---

### Post by Rubicon421 on 2008-11-16
Well, I'm very new to Linux and would like to stick to the easiest method. How easy are these compared to Samba and the regular file sharing option in Ubuntu?

---

### Post by Iowan on 2008-11-16
Some claim NFS is faster - as it was designed for Unix systems. It is probably closest to "regular file sharing".  SSHFS is more secure.  Either will require adding a "support" package.  I have a Samba system running - although on an older version of Ubuntu.  Samba has a reputation for being harder to set up.

---

### Post by Rubicon421 on 2008-11-16
Where do I get NFS? Couldn't find it in the add/remove and there's a lot of NFS related programs in synaptic.

---

### Post by Iowan on 2008-11-16
The [How-To]("https://help.ubuntu.com/community/SettingUpNFSHowTo") explains it better than I can (especially since I haven't set up NFS). In brief, the server (machine supplying the files) needs "sudo apt-get install portmap nfs-kernel-server", and the client (machine requesting the files) needs "sudo apt-get install portmap nfs-common". The How-To is much more in-depth. You needn't absolutely use **apt-get** - the programs are probably available via Synaptic, too.

If you opt for NFS, [this]("http://ubuntuforums.org/showthread.php?t=875249") thread looks interesting, too.

---

### Post by theDaveTheRave on 2008-11-27
Hi guys,

It seems that this isn't an uncommon problem!

I have succesfully folowed the advice of Stormbringer, in this thread


And been quite happily able to view the folders on a Windows instalation, however when I try to view folders on another Ubutnu Hardy terminal I cannot connect to the folder!

It is most anoying!

I guess I am missing something, but for now I don't know exactly what that is... I need to keep hunting..

I also need to be able to see the same folders from Windows machines for my colleagues at work.

I suppose I could allways set the whole thing up as an <FTP> type situation... ? but would that allow me to do system backups of my colleagues terminals?

thanks for any advice

David

---

### Post by SIGTERMer on 2008-11-27
open nautilus then try writing **smb://*192.168.1.1*** in the address bar. replace 192.168.1.1 with the ip of the computer you are trying to connect to.

---

### Post by theDaveTheRave on 2008-11-28
Dear all...

thanks for the note, but I don't understand why it never seems to work for me, connecting my ubuntu to other shared drives is really simple however, and so long as I get  comms in at least one direction I will be OK.

I'll keep trying with nautilus and stuff to see how things go.

Also, in the team there are 5 of us, with access to over 10 (or more) pc's. From what I've read it seems I need to create a user on every terminal that will match with the user name of my "samba user" on my Ubuntu desktop, I would much prefere being able to set a single username and password (eg; guest anonymouw) - as I also have this user set up on my Ubuntu pc for read / web access only.

Just to add confusion.... I am also setting up a local server that will have the same thing, again I don't want to have to add a user to every terminal, and as it would be read access only I was going to use the same login and password... does this make sense?

Another quick note..

When I "map" the drive from another terminal if I put in the IP address the system will automatically ask me for a username / password for my ubuntu system. It obviously sees the system fine, as it banners back the hostname in the subsequent window.

eg;

connecting to 134.195.157.83

username:  DARTAGNAN\guest
password: ********

but I can't connect after this...

I'm obviously missing something, but I'm not sure what it is!

thanks for the help so far.

David

---

### Post by SIGTERMer on 2008-11-28
David, first of all, you don't need to create a smb user for each person who will be accessing your shared folder. like you said, simply create a system(ubuntu) user named guest and then create a smb user with the same user name, and your set. after you've done that, any one can use that name to access your shared folder (even under windows).

I'm going try to make this as simple as possible:

1- install samba on the server only [NO NEED TO INSTALL SAMBA ON CLIENTS*]
2- create a system user named *guest*
3- create a samba user with the same name
4- modify the folder so that it can be shared through samba (using nautilus, read previous posts in this thread).

and you are set to share.

to access shared folders
ubuntu: type **smb://*ipAddress*** in nautilus
windows: type **\\*ipAddress*** in run

i really hope this helps you out :)


* normal ubuntu installations have an smb client installed by default (you can access a share but not create your own, for that you need to install the samba package)

---

### Post by theDaveTheRave on 2008-12-01
Sigterm,

I'm not entirely sure what I was doing wrong!

but I've just shared the whole of the "guest" folder (don't worry the guest user has almost no priveleges at all outside of their own area!), and whoopie hi hey... it works first time?

I think what I was doing wrong was....

During setup of Samba you create a "Samba" group, and a samba share directory, I was obviously attempting to connect to this folder (ie /home/samba/ ) and that wasn't working? possibly I hadn't shared it correctly (or forgot to restart my system!).

Well as I say I made the "guest" area a shared section, and :guitar: so I'm happy....

Great stuff,

Thanks

Dave

---

### Post by johnjohn2 on 2009-01-14
Dave,

Don't give up try this in terminal > shares-admin and add the folder from there.

If you tried this on intrepid for the love of God make sure that it is a clean install.

Hope this helps

John

:popcorn:

---

