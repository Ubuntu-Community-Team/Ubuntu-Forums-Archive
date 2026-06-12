---
title: "Network newbie"
date: 2005-06-18
forum: Networking &amp; Wireless
---

### Post by Gotou on 2005-06-18
Howdy!  I'm trying to network my laptop to my desktop but I don't know anything about networking.

After several futile hours of reading through forum threads and poking around in both cpu's I'm frustrated.  Simple explanations are what I'm looking for now.

Both cpu's are running Ubuntu Hoary Hedgehog 5.04.
The cpu's are connected to a firewall router by ethernet cables.
The router is connected to the modem for internet access.
Both cpu's can access the internet.

Are there any Ubuntu guru's who can tell me which buttons to push?

Thank you!

---

### Post by cwaldbieser on 2005-06-19
When you say:

> I'm trying to network my laptop to my desktop

it is somewhat ambiguous.  It could mean you want to do file sharing with NFS, or you want to ssh from on computer to the other any one of a number of things.  If you explain what exactly it is you are trying to accomplish, it will likely assist someone in helping you out.

That said, can you ping either computer from the other?

If you don't know what that means, open a terminal on each computer and enter:

```
$ ifconfig
```

Some text will spit out that describes each of the network cards in your computer.  An ethernet card is usually eth0.  A wireless card might be wlan0.  There will be an IP address given for each of these interfaces.  A typical home network address might be something like 192.168.0.2.

Fin out the IP address for each computer on your home network.  Then at the terminal on one:

```
$ ping ip-address-of-other-computer
```

If successful, some lines will come back like:

```
64 bytes from 192.168.0.2: icmp_seq=1 ttl=64 time=0.045 ms
64 bytes from 192.168.0.2: icmp_seq=2 ttl=64 time=0.044 ms
64 bytes from 192.168.0.2: icmp_seq=3 ttl=64 time=0.042 ms
64 bytes from 192.168.0.2: icmp_seq=4 ttl=64 time=0.043 ms
```

That means your computer is aware of the other's presence on the network.

If unsuccessful, it will probably say something like "Host Unreachable".  This means your computer doesn't know how to send a message to the other.

---

### Post by Gotou on 2005-06-19
Ok, pinged both cpu's successfully.  Now what's the next step?

Yup, I want to share files between both linux cpu's.  Then of course I'd like to be able to synchronise some of those files.  I've heard of unison but getting the two cpu's to share files needs to be done first.

While poking around I found icons for Windows Network, then mshome.  Eventually I would like to access the WinXP hard drive but why doesn't Ubuntu have some sort of wizard program to setup the connection between two cpu's?  Especially if both cpu's were running Ubuntu.  That would seem to be a necessity these days.

What is NFS and ssh?

Thanks!

---

### Post by cwaldbieser on 2005-06-19
What you want to do to enable file sharing between your computers is to use Synaptic (or apt-get) to get a suite of programs called "samba".  There is also a package called "samba-doc" that explains all the gory details of how those programs work.  What samba attempts to do is to share files the same way that Windows based computers do:

[http://www.ubuntuguide.org/#sharefolderstheeasyway](http://www.ubuntuguide.org/#sharefolderstheeasyway)

This link should help you out.  The rest of that guide also has a lot of useful info in it for new users.

NFS is the Network File System protocol.  If your network is all UNIX-like machines, you could use this protocol to share files.  Some UNIX networks (mostly in business environments) use this.

ssh stands for Secure SHell.  It is very similar to telnet, if you know what that is.  If not, the basic idea is that it is like typing at the console, but on a remote computer.  ssh has some security features built in so that other people on the network can't easily snoop on what you are doing.

In the early days of the Internet, there were two very common programs called ftp and telnet.  FTP (file transfer protocol) lets you upload and download files from a remote computer.  The telnet program let you run an interactive concole session on a remote computer.  Neither had much in the way of security features.

In UNIX environments these days, with all the concerns about security, ssh has pretty much replaced telnet, and scp (Secure Copy), has replaced ftp.  The older protocols are still around, and they are very useful if you just want to move files around in an environment where security isn't such a big deal (like on your home network).

---

### Post by Gotou on 2005-06-21
Installed nfs common, swat, smbfs, samba, samba common and samba doc but I ain't dancing a samba just yet. :-P 

Both cpu's showed up in "places-network servers".  I made a couple test folders, right clicked, selected "share folder", smb, allow folder browsing, ok.  (a lot of guessing and hoping here).

I tried a few folders with some capital letters and spaces.  Those never showed up.  I also noticed that it took several minutes for the shared folders to show up on the other computer.  After rebooting and immediately going back to the menu "places-network servers" both cpu's were gone.  A few minutes later they showed up.  Why does it take so long and what folder and file name character limits?

I tried to look up info in samba doc but I can't find the file. ](*,)   Synaptic says it's installed.  How and where do I find it?

I've looked through [www.ubuntuguide.org](www.ubuntuguide.org) but I'm still getting confused by all the command line stuff.  Much of Linux lingo is still unfamiliar to me.

Thanks!

---

### Post by bunced on 2005-06-22
[QUOTE=Gotou]Installed nfs common, swat, smbfs, samba, samba common and samba doc but I ain't dancing a samba just yet. :-P 

Both cpu's showed up in "places-network servers".  I made a couple test folders, right clicked, selected "share folder", smb, allow folder browsing, ok.  (a lot of guessing and hoping here).

I tried a few folders with some capital letters and spaces.  Those never showed up.  I also noticed that it took several minutes for the shared folders to show up on the other computer.  After rebooting and immediately going back to the menu "places-network servers" both cpu's were gone.  A few minutes later they showed up.  Why does it take so long and what folder and file name character limits?

I tried to look up info in samba doc but I can't find the file. ](*,)   Synaptic says it's installed.  How and where do I find it?

I've looked through [www.ubuntuguide.org](www.ubuntuguide.org) but I'm still getting confused by all the command line stuff.  Much of Linux lingo is still unfamiliar to me.

Thanks![/QUOTE]
 It takes so long because a computer has to register itself on the network and then query other computers as to their PC.

[http://home.arcor.de/36bit/samba.html](http://home.arcor.de/36bit/samba.html) might be useful instead of Samba-doc. To see where samba-doc has been installed, do a right-click on the file in Synaptic, select Properties. Look for a little tab labelled 'installed files'. That will give you the information needed.

Regards,
David

---

### Post by Gotou on 2005-06-22
I deleted my test folders from the home directory on my laptop.  Those folders are still showing up in the desktop's network.  Even after re-booting.  The laptop's "system > administration > shared folders" is locking up without displaying anything.  I'm guessing I should have removed the folder in the "shared folders" part before actually deleting them.  Is there a file somewhere that is still holding onto these deleted folders' pathes?  I also emptied the trash can before discovering this little problem so there is no restoring those test folders.

Any ideas?

Thanks!


**************
Update:

I found and edited the smb.conf file by starting the terminal, then: "sudo gedit /etc/samba/smb.conf"

Deleted the entries that referred to my test folders.

"System > Administration > Shared Folders" still locks up. Why?

---

### Post by Gotou on 2005-06-23
I re-installed Ubuntu on my laptop to fix the "Shared Folders" lock-up.  I'm looking forward to the day when I can actually use my laptop. :roll: 

Anyway...

Thanks David for the info about why it takes so long for the computers to find each other.

Cwaldbieser, thanks for your help too.  I understand more than I did a few days ago.

I'm still working on this subject and still have questions.  Last night I created a shared folder on the desktop cpu and threw in 101 text files to play with.  I tried to copy those files from the desktop to my laptop.  The copy process started but was very slow.  At 10 files copied the progress bar estimated it would take over 11 hours to copy the files! I waited several minutes to see if this was just an error.  After 10 minutes I canceled out and copied the files through the sneaker net.  They copied in less than a minute.

What do I need to do now?

Thanks!

---

