---
title: "File Sharing Between Ubuntu Machines: SMB share mounted where?"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by iveand on 2009-03-23
I am new to Ubuntu and have installed on 2 separate machines.  I am trying to set up file sharing between them.

On the "server" I set up a share on my home folder by right-clicking and setting "share options".  It needed to install smb stuff, so I said OK and it did and then rebooted.  I think in there I also added a userid (SMB must have been) and had it the same as the ID on both machines to keep it simple.

The share seems to be fine on the server.

On computer two, "client", I chose "places / connect to server" and put in the info for "server".  It then connected no problem!

So, I am connected, and can see the files.  My only issue is that I can't for the life of me find out where this share is mounted to (in Terminal).

It lists in Nautilus as smb://userid@server/share.

In terminal, when typing "mount" I see nothing related to the share.  So I guess I can access it but it isn't mounted?  I have read some things on smbclient and mounting, but I got lost along the way.

And, since both are Ubuntu, is SMB the right way to share files?  What is this CIFS?

thanks,

iveand

---

### Post by taavikko on 2009-03-23
It is been mounted via gvfs and is located in the user's ~/.gvfs/
Or at least should be...

---

### Post by iveand on 2009-03-23
Thanks, I will check again.

Admittedly I had seen this "gvfs" when I typed in "mount" to display a listing of mounts.  But this was before I then tried a few other hack things that kind of messed the system.

Since the "client" was a clean install with no updates I thought the best would be to reinstall, so I did that.

But, then on this "new install", I didn't see anything in the mount listing that noted GVFS.

So, is GVFS a replacement for (or preferred over) smbfs?  I ended up installing smbfs on the server as well (via apt-get since I didn't see it in synaptic), but maybe that is botching me.

Trying to sort out what is the "preferred way" to share files between 2 ubuntu computers.  Maybe as I am doing with SMB and GVFS is the best?

iveand

---

### Post by 3rdalbum on 2009-03-23
GVFS is a "virtual" filesystem that Gnome uses for various things, including the mounting of real Samba shares in Nautilus. There are so many ways that SMB can be mounted, and GVFS is just one way; but if it's working for you, then why change?

SMBFS is another virtual filesystem anyway :-)

---

### Post by wjp.reg on 2009-03-23
Perhaps this link can help sort out some of the confusion.

[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

cheers

---

### Post by iveand on 2009-03-23
Since I am new I have no problem staying with GVFS.  I'll let the Ubuntu masters decide what are the "default packages" for us new folks.

However, it isn't FULLY working (at least via Terminal).  Again, the situation is that I have the SMB connection established (via "network / Windows Network in this case).  BUT, in Terminal I can't see the share.

When trying to navigate to ~/.gvfs I get a permission denied error.  When then trying "sudo cd .gvfs" from ~ I get a "cd not recognized" error.  Huh?  Just trying to see the share that is supposedly mounted (even if virtually!)


thanks again,

iveand

---

### Post by men28 on 2009-03-23
I have two ubuntu computers too and share files between them using "vsftpd" server. This is just very simple FTP server.

[http://vsftpd.beasts.org/]("http://vsftpd.beasts.org/")

To install it under Ubuntu type in Terminal:
```
sudo apt-get install vsftpd
```

After the installation edit /etc/vsftpd.conf file for configuration.
A description of this file is there:
[http://vsftpd.beasts.org/vsftpd_conf.html]("http://vsftpd.beasts.org/vsftpd_conf.html")

---

### Post by iveand on 2009-03-23
Thanks to the above link I read a bit and gave openssh server a try.  Now I am connecting either via Terminal 'ssh serverIP' or via GUI 'Places / Connect to Server / SSH / server'.

So I guess the SMB share setup is only needed when wanting to share to Windows machines?

There was also mention in the link about using NFS for multiple Ubuntu machines.  I didn't look into that yet.

Are these the 3 options (there is an FTP setup possiblity as well as posted above) so make that the 4 options?  Why choose 1 over the other?  SSH will probably handle my needs for now, but I remain uncertain of why I chose it and would be interested in knowing more about the alternatives.

Thanks to all so far.

iveand

---

