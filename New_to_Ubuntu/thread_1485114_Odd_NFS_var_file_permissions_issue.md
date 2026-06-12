---
title: "Odd NFS/ var file permissions issue"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by kodb on 2010-05-16
I've been setting up a homeserver with the intent to use for both multimedia and data storage. All of my machines are either 9.10 desktop or UNR and the server uses 9.10 server.  All are updated properly.  I have a usb external SATA harddrive on the server and have it mounted to  /media/SATA01
When I have setup nfs with the 2 netbooks I am able to access via /var/zzzzserver no problem.  On my one old aspire 3000 notebook, when I have the same setup it tells me I don't have permission to use but only when logged in as my wife.  When I login under my account no problem.  I tried to use chown :zzzzgroup and then change the permissions with chmod; this tells me the actions are occurring when using the -c option.  But, I still get the error no matter what.  I tried creating a new folder and mount point in my wife's account but it still gives me the same error.  On the server side I created the same groups and users in an effort to make work but that didn't help either.  Again, both netbooks are connecting without difficulty, it is only the 2nd user on the one machine that I can't get to work.  Help!
Thanks,
Bob

---

### Post by kodb on 2010-05-16
Scratch the above, now none of the others work either and I am unable to change permissions successfully from either the CLI or via nautilus using either gksudo or gksu.
I'm going nuts over this one as it doesn't make sense!
Bob

---

### Post by kodb on 2010-08-15
Ok, old thread but I have got it figured out with respect to the permissions: I had to chmod them but had some hangup using numbers instead of letters.  I found that I need to chmod the original shared directories and the nfs pseudofilesystem directories as the examples noted below for working this out from creation:

```
$ sudo mkdir /video
$ sudo mkdir /srv/video
$sudo chmod -R a+rwx /video
$sudo chmod -R a+rwx /srv/video

```This should work to allow everyone to read/write to the nfs4 mounted share /video; assumes that you've got the nfs4 exports and mounts correct. 

Regards,
Bob:popcorn:

---

