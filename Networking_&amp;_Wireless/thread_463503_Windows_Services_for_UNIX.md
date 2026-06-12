---
title: "Windows Services for UNIX"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by YodaJones on 2007-06-03
Has anyone here any experience using Windows Services for UNIX?

[http://technet.microsoft.com/en-us/interopmigration/bb380242.aspx](http://technet.microsoft.com/en-us/interopmigration/bb380242.aspx)

I am currently using SMB to attach to Windows 2003 Small Business Server shares from Ubuntu.  The problem is that on the Windows SBS server is a Media share containing a WMA audio library.  When trying to play these files with MPlayer it gives a error "could not play...." No plug in to handle the location of the file.  MPlayer can play these files if I copy them locally.

I was wondering if installing Windows Services for Unix I could play the remote WMA's via NFS instead of SMB.

Any ideas?

---

### Post by dmizer on 2007-06-04
i don't know a thing about windows services for unix, but i think i can address your smbfs problem.  how are you mounting the windows shares with samba?

you will get the no plugin error if you mount the windows shares via nautilus (places > connect to server).

if you want to play the files directly from your server (rather than copying them across to your ubuntu machine), take a look at the second link in my sig.

if you're already using fstab to mount your shares, please post the fstab line for the windows server.

---

### Post by YodaJones on 2007-06-04
Awesome!

Excellent tip!  I connected to the Windows Server share as per your second link in your sig and I can now play the files directly off the server.

Thanks for saving me copying all the files to my local drive.

Someday, as I get more familiar with Ubuntu/Linux, I need to eliminate that Windows Small Business Server entirely!
I think if I could find a Microsoft Exchange substitute that runs on Ubuntu server that day may come!

I appreciate your time in helping me.

Thank you again!

---

