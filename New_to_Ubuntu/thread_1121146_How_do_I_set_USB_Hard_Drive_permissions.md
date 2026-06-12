---
title: "How do I set USB Hard Drive permissions"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by sfd609 on 2009-04-09
hello all:
I've just setup sftp on my Ubumtu 8.04 and now I'd like to grant access to an account with read only permissions to my USB Hard Drive.  I've created and account, logged into the account which created the home directory, but when I try to access the USB Drive I canncesot read or display the contents. I'd like to setup read and file scan permissions on selected drives.  So far the only way I was able to get access to the USB Drive was to log on to the my computer with my guest account, plug in the USB Drive which then was granted read/write permissions and then I could access it from the public internet.  Any help would be greatly appreciated.  Here is the ls -l on the folder I'm trying to share:
drwx------  2 mmiller root   32768 2009-04-09 15:10 SharedData

---

### Post by accooper on 2009-04-09
Here's how I got my six hard drives to auto mount on start up:

Go to Add/Remove search for disk manager.

Install it.

Run it.

make sure All boxes are checked if you want everything to auto mount.

I have six hard drives 4 external usb 250 gb Western Digital, and I never thought I would be able to get them to auto mount in Ubuntu 8.10.  But this program will do it.

Hope this Helps

:guitar:

Andrew

---

### Post by sfd609 on 2009-04-09
Thanks Andrew, were you then able to access your drives from the internet?  I'm using filezilla and I can see the drives, but I cannot do a file listing.  Also, when I attempt to connect the folder by using the command cd /media/MMWD250, it replies with "Directory /media/MMWD250 permission denied", Could not retrieve directory listing.

---

### Post by accooper on 2009-04-09
Yes but not with filezilla.  They have to be shared through a network, and that is beyond my knowledge of Ubuntu.

What I did was give permissions to my home network.  But I think what you are trying to do may be dangerous. easy to hack I think.

:guitar:

Andrew

---

### Post by FrankT-Qc on 2009-04-09
If you're using sftp, you should have exactly the same acess right as when you log in directly with the same account... 

A few hints :

You need the right to access the files AND the right to read and travers through all the directory tree i.e. if your share is into /media/usb/share,
you need "rx" on /media, /media/usb, /media/usb/share ...

If not, filezilla, while using sftp, uses pretty much the same system as a normal SSH session... try to ssh in as the same user and getting to your files... whatever stands is your way should become clearer this way since you're going to have explicit error messages when trying to "cd" to your share.

---

### Post by sfd609 on 2009-04-09
That is what works.  What I am trying to do is have a guest user which I've granted access to my computer have sftp access and download files from my SharedData folder.  When I log in with my credentials, I have the access, but when I log in with my guest credentials, the directory listing is denied.

---

