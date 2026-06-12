---
title: "Unable to add Samba User"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by PDD on 2010-05-04
Hi Folks,

I am in the process of trying to setup a Samba share on Ubuntu (9.10) for use by a Mac OS X client. I have followed the following tutorial

[http://www.ghacks.net/2010/03/16/connect-to-a-samba-share-from-os-x/](http://www.ghacks.net/2010/03/16/connect-to-a-samba-share-from-os-x/)

All was fine and well untill I got to the point where I had to add users to the Samba share. Below is what I typed in and the error I got in the console

> davidius@ubuntu:/etc/samba$ sudo smbpasswd -L -a OSXConnect
New SMB password:
Retype new SMB password:
Failed to add entry for user OSXConnect.


From searching on the forum here (and others) it seems that members who had an issue with this command previously was primarily due to them not having the user they are trying to add to Samba already setup as a user on their Ubuntu systems. I created the user OSXConnect just for this purpose but as you can see above it still tells me "Failed to add entry for user OSXConnect".

Unfortunately I am a Linux N00B with very little linux knowledge and no experience in setting up Samba in the past so most likely Im missing something very basic here. Any feedback and help would be greatly appreciated. 

As an aside is Samba the right choice? I really just want to share folders on a home network so I can store all my files on my shinny new linux server with 1TB RAID 1 array. In some of the other forums I've read when researching this problem using NFS was suggested as an alternative. I was under the impression that Samba was the best option as it allowed for printer sharing and lots of other stuff that I probably won't need. 

Also do I have to be logged in as OSConnect user on Mac client if I want to access the Samba share?

Dave

---

