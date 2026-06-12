---
title: "setting up a file server"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by maniacmusician on 2007-02-19
In the next couple of days, I'm going to be setting up a linux-based file server. I'm only using a basic server install and sticking it in the closet near the router to set up a wired connection. 

However, the files on the server have to be accessible using both Windows and Linux. What's the best way to go for this?

I've considered SSH, since it's a breeze to set up for linux-to-linux networking. Would this work with windows too? If I remember correctly, you need a special program on windows to be able to access the Linux share. WinSCP? but is that the only way?

Is there any other alternative for Windows? keep in mind that the server is going to be using an ext3 file system, because I don't feel like messing with any limiting factors, like FAT partitions. 

So basically, is there a better alternative to access a Linux server from a Windows computer than WinSCP? If so, please tell me more about it.

thanks.

---

### Post by gradedcheese on 2007-02-19
For Windows networks, you'll want samba.  

```

sudo apt-get install samba-server

```

You can read [my short howto article]("http://andrey.thedotcommune.com/samba.html") to learn how to set up and add users, but overall its very simple: you create samba shares, create Linux accounts for each user, group users as needed, and then set permissions.  I use Samba to run a 'windows' file server, for example.  Linux PCs can also connect to it.

For Linux-only networking, NFS is a better choice.

---

### Post by maniacmusician on 2007-02-19
I was leaning towards SSH rather than NFS because of the security aspect of it...we have an unsecure wireless network because I can't get WPA to work with my card in Linux (haven't bothered trying WEP. It's so useless it might as well not be there), so I want to at least be as secure as possible within the network. 

But your howto seems to be okay. I have a question though...what is the point of setting up seperate linux accounts/users and groups? I don't understand the dynamics of it. How does Samba identify and correllate that a certain Windows user belongs to a certain linux group?

I just plain don't understand how users and groups translate between windows and linux using Samba.

---

### Post by gradedcheese on 2007-02-19
Basically, samba maintains a list of accounts (which have to be real Linux accounts, hence the need to create them).  When a Windows user (say 'bob') tries to log in to a Samba server, Windows gives him a user name and password dialog box.  If 'bob' is his windows user name, that will get put into the user name field automatically (probably).  He then logs in, and samba authenticates him via the Linux account.

The advantage: one unified (well, pretty much) system of managing users and groups: the built-in Linux system accounts.  I like this a lot better than maintaining some special accounts list elsewhere.  Also now bob can have ssh access as well (if you wish), and anything else that you want to grant to his real Linux account.

ssh is a secure shell, windows users generally do not want to log in to a shell account :)  They could use sftp instead, but that will require extra software (well, an SFTP client) to set up on the Windows side.  Samba just lets them use the native windows "network neighborhood" stuff, for all they know there's a windows server on the other side.

---

### Post by maniacmusician on 2007-02-19
> **gradedcheese said:**
> Basically, samba maintains a list of accounts (which have to be real Linux accounts, hence the need to create them).  When a Windows user (say 'bob') tries to log in to a Samba server, Windows gives him a user name and password dialog box.  If 'bob' is his windows user name, that will get put into the user name field automatically (probably).  He then logs in, and samba authenticates him via the Linux account.
Ah, okay. I understand that.

> **gradedcheese said:**
> The advantage: one unified (well, pretty much) system of managing users and groups: the built-in Linux system accounts.  I like this a lot better than maintaining some special accounts list elsewhere.  Also now bob can have ssh access as well (if you wish), and anything else that you want to grant to his real Linux account.
That pretty much makes it perfect, doesn't it?

> **gradedcheese said:**
> ssh is a secure shell, windows users generally do not want to log in to a shell account :)  They could use sftp instead, but that will require extra software (well, an SFTP client) to set up on the Windows side.  Samba just lets them use the native windows "network neighborhood" stuff, for all they know there's a windows server on the other side.

Well technically, ssh is a secure shell, yeah, but there are curious implementations like sshfs that expand the scope of use for something like ssh. Not to mention the ssh -X protocol which can forward X sessions of certain apps. That's a brilliant function.

But wow, this is a lot easier than I thought it would be. I love Linux. 

Just a couple more questions and I'll be out of your hair.

1. This will work even though the Linux box has an ext3 filesystem and Windows has NTFS?

2. I was thinking about setting up a DNS server on this box as well, to do some hostname resoultion until Zeroconf was fully implemented in Ubuntu. My question is, if I set up the DNS server (which is for hostname resolution among the **linux** boxes), will that affect the Windows PCs that are in the house as well?

Thanks again for your answers. You're answering almost every single thread in this section! A hard worker, you certainly are. Thanks for your time!

---

### Post by gradedcheese on 2007-02-19
1. yes, it will work.  the file system is irrelevant, samba abstracts it all away.
2. yes, a DNS server is a DNS server, regardless of OS.  the windows PCs will happily use it if you set them up to use it.  I don't have much experience with setting up DNS servers, but you'll probably find a good howto article about it as it's a common task in IT.

> 
Thanks again for your answers. You're answering almost every single thread in this section! A hard worker, you certainly are. Thanks for your time!

you're welcome :)

---

### Post by maniacmusician on 2007-02-19
> **gradedcheese said:**
> 1. yes, it will work.  the file system is irrelevant, samba abstracts it all away.
2. yes, a DNS server is a DNS server, regardless of OS.  the windows PCs will happily use it if you set them up to use it.  I don't have much experience with setting up DNS servers, but you'll probably find a good howto article about it as it's a common task in IT.



you're welcome :)
Well I actually kind of want the Windows PCs to ignore the DNS server. Is that possible as well? I want the DNS server only to do hostname resolution for the Linux computers that I have (5 of them).

The rest of the info you've given me seems golden. I'll try this out tomorrow and if it doesn't work, I'll be back to bug ya.

---

### Post by gradedcheese on 2007-02-19
yeah, you can do that.  basically, I think you'd add your DNS server to the Linux PCs' /etc/resolv.conf (but not configure it on the Windows side).  However do read about DNS elsewhere, I probably don't know much about it from the server side.

---

### Post by maniacmusician on 2007-02-20
okay, I'm back! ha, no, not a good thing.

SSH networking for the Linux boxes was stupifyingly easy. Samba; not so much. I'm having a lot of troube with it. 

I compared two boxes; my KDE box, and the file server with just a command line interface. They both have practically identical smb.conf's, but only one of them works...the KDE box. I don't get it. I can access that box from Windows computers.

After fiddling around with the smb.conf of the file server, I got it so that I can access it from Windows (by doing a "\\[hostname]")...but I don't have write access! at least I can't copy and paste into it. I get some access denied error. I dunno about read permissions, there's not much on that machine to read. But, I can browse the folders of the file server from the Windows box, I just can't paste stuff to it!

It's also infuriating because the file server doesn't broadcast its presence on the network. It doesn't show up in "Workgroup" when in Windows, and it doesn't show up in "smb://" in Konqueror. In Windows, when I type "//[hostname]" I can browse folders but I can't write to it. In KDE, I can't even access the samba share with the customary "smb://Workgroup/[hostname]"

WTF is going on? Please help.

---

### Post by gradedcheese on 2007-02-20
I really doubt that the two smb.conf files are as similar as you think :)  Please double-check them.  If needed, copy one PC's to the other (in some location) and then use diff, like this:

diff smb.conf /etc/samba/smb.conf

to see the difference.  Also, remember to restart samba after smb.conf changes.

---

### Post by maniacmusician on 2007-02-20
Well yes, they're not completely identical; I left out a couple of details. The smb.conf in the KDE box doesn't specify a workgroup or a server string under "Global Settings". 

Okay, so I've tried to replicate that behavior in the file server. I commented out the workgroup and server string lines. For a second, I thought I accomplished something, because I could finally see the file server in "workgroup" from both Linux and Windows. However, even with those lines commented out, I still can't write to the file server from windows. If I try to access the file server from Linux (using the SMB protocol), it just times out. 

Other than the workgroup and server string lines, the only difference between the two files was in the shares, because, well, they have different shares

So, like I said, WTF is going on?

If it helps, I noticed something odd; When accessing from Windows, the file server doesn't ask for a password, it just lets the user browse the share...but it doesn't let them write.

any suggestions? would you like me to post the smb.conf's?

---

### Post by gradedcheese on 2007-02-20
Sure, post snippets of the files (just the shares part in the bottom), I assume the global stuff you have set up correctly.  Check the permissions for the shares themselves via "ls -l" and make sure they're reasonable (and compare between the two PCs if needed)

---

### Post by maniacmusician on 2007-02-20
> **gradedcheese said:**
> Sure, post snippets of the files (just the shares part in the bottom), I assume the global stuff you have set up correctly.  Check the permissions for the shares themselves via "ls -l" and make sure they're reasonable (and compare between the two PCs if needed)
share permissions on file server
> 
drwxr-xr-x 3 tulia root      4096 2007-02-19 16:45 fileserver_backup
drwxr-xr-x 3 tulia root      1024 2007-02-19 16:49 fileserver_documents
drwxr-xr-x 4 tulia root      4096 2007-02-20 17:10 fileserver_storage


share permissions on KDE box
> 
drwxr-xr-x 99 maniacmusician maniacmusician       4096 2007-01-11 00:41 Music


I'll just throw in the smb.conf's as I'm really not sure what parts are relevant anymore. Confused out of my f*cking mind.

---

### Post by gradedcheese on 2007-02-20
well, as you can see from your post, on one server the share is owned by:

tulia.root

on the other it's owned by:

maniacmusician.maniacmusician

So, which user is supposed to have access to it?  You can change the ownership like this:

sudo chown -R user_name_here.group_name_here /path/to/share

From your smb.conf files, it looks like the group you want is 'winusers', not 'root' ;)

---

### Post by maniacmusician on 2007-02-20
nice try, but no go (I changed ownership to tulia.winusers) ....but you probably solved a problem that would've come up eventually.

I think I've figured out the logistics of the problem. According to smb.conf, the group winusers has access to those shares....and it would probably be granted access, however.....When accessing Tulia (fileserver) from Windows, the user is not even prompted for a password! Thus, he cannot log in, and cannot be identified as part of the group winusers.

So the problem we have to solve is, why is the windows user not prompted for a password? Is the answer to that in the smb.conf file?

If so, I think it is worth mentioning that Alexis (the KDE box) prompts for a password when accessed from a Windows box. And since the two files are pretty much identical, I'm inclined to think that the answer lies outside of smb.conf?

What's going on?

---

### Post by gradedcheese on 2007-02-20
I can't think straight right now, but try adding this option to the share:

```

guest ok = no

```

If you still don't have this working tonight, I'll log in to my file server and see if there's anything special with how I set it up, I don't think you're doing anything wrong specifically though... however, up in global options, I enable:

```

security = user

```

in your files it's disabled (it has a ';' in front of it, which is a comment)

---

### Post by maniacmusician on 2007-02-20
no that didn't work....

I'm pretty sure the key is figuring out the difference between Alexis (KDE) and Tulia (server). since their smb.conf's are pretty much the same (unless I read it wrong...you can try to use diff on the files as well to see if I missed something), I'm assuming it's some kind of package that Alexis has installed but not Tulia? Certainly it doesn't seem like there is any difference in settings

but yeah, Tulia still not working.


PS: In case you were wondering about the girl names, they're actually the names of my guitars. I....like to name my guitars. People have done weirder things, I suppose

---

### Post by gradedcheese on 2007-02-20
I don't think any other packages are needed.  I also don't see anything particularly wrong with your smb.conf, aside from the difference in users and permissions (and the two things I pointed out above).  Here's what I usually use, in case you find it helpful:

(global)
```

   workgroup = PUT_NAME_HERE
   netbios name = put_server_name_here
   server string = %h server (Samba)

   passdb backend = tdbsam
   security = user
   username map = /etc/samba/smbusers
   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = yes

```
(snip...)
```

[some_share]
   comment = All Users
   path = /share
   valid users = @users
   force group = users
   create mask = 0660
   directory mask = 0771
   writeable = yes
   vfs objects = recycle

```

---

### Post by maniacmusician on 2007-02-21
Well I replicated your Global settings and that didn't make a difference.

Like I said, I'm about 90% sure that I've targeted the logistics of the problem; Samba isn't querying users for a password. For Windows, this means they can't login and get write access, and other linux computers can't even access it using smb; it times out, the reason being, I think, that the samba server doesn't give them a password prompt. Just a theory.

So I have to get it to authenticate users by making them enter a password...

I can't even wrap my head around it anymore. Someone, please help...

---

### Post by maniacmusician on 2007-02-21
I'm convinced that my KDE box isn't seeing samba correctly...what's weird is that every computer on the network interprets the windows network differently. For instance, my KDE box sees 3 computers on the windows network; itself, the windows computer, and the "fileserver" (which it can't access). My Windows box sees 3 computers as well; itself, my KDE box, and the fileserver (which it can see but can't access). My other Linux computer (also KDE) sees only ONE computer on the Windows network; the fileserver (which it can see, and actually connects to, and give me an error)

So this is what it comes down to. I have a new error;
> 
smbmnt must be installed suid root for direct user mounts (1000,1000)
smbmnt failed: 1


I'm assuming this is for smbmnt on the **client**. In which case, how do I get it to work in Windows? I dunno...

---

### Post by dca on 2007-02-21
I'm trying to remember how I solved a similar problem on my file server.  I think I installed webmin,samba-server, and something else on it (webmin because I'm slow at the CLI) that way I can see the settings for all user(s) who are to access it.  On each user set-up on it there was a setting to add regular, encrypted, or whatever p/w to it.  The only other problem I had was opening a port...  Perhaps it was that webmin utlity that helped because I was able to see everything visually...  Sorry not much help....
 
 
by the by, BB King's guitar is named Lucille.

---

