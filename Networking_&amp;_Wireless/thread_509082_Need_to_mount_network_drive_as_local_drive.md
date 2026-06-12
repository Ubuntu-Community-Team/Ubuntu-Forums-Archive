---
title: "Need to mount network drive as local drive"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by maharbA on 2007-07-25
Hi everybody!

I have an external hard drive which is plugged into my desktop computer (running XP -- sorry, I can't change that). Windows calls this "External" or "G:" or both. This drive has files which I would like to have full access to from my laptop when it it running Feisty.

By full access I mean more than just read/write -- I mean being able to upload files which are on that drive through firefox (for example, when I am updating a CraigsList ad and need to add photos which are stored on the "G" drive. (I understand that I can only access anything on this drive when the desktop is on :) )

Right now I can see the desktop and all drives, including G, thanks to Samba. But to upload files via firefox on my laptop I have to copy the files to my laptop and then upload them.

Is there a way to mount this drive as though it were local? or in any way be able to upload from firefox (I tried typing the address -- smb://yadda/yadda/etcetera -- in the Fox's upload page, but I am reprimanded :)

any help is appreciated
rock on

---

### Post by aquavitae on 2007-07-25
Can't you just plug the external straight into your laptop?

I haven't used samba much, so I'm not sure exactly how you do this, but instead of using smb:// you should be able to mount it to a local path, e.g. /mnt/samba.  Try a google search for mounting samba shares, you should get something.  You should also be able to do it through system settings, but once again I'm not sure how.  Once you've mounted it to a local path you can access it as any other local path.

---

### Post by gangolli on 2007-07-25
To get the behavior you want, you can mount the Samba share using smbfs.

The following HOWTO should help you out: [http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

### Post by maharbA on 2007-07-26
Thanks gangolli !

Now I can mount the drive as though it were local.
But this does not happen automatically at startup, I have to open a terminal and type "sudo mount -a" and enter my password.

Any advice?

---

### Post by gangolli on 2007-07-27
I responded on the other thread for you.  But here it is again.
> 
Others (see [this thread]("http://ubuntuforums.org/showthread.php?t=331661")) have reported that using either of the two forms of specifying authentication in /etc/fstab seems to be required in order for the boot-time smbfs mounts to work.


Hope that helps.  Both of the questions were actually answered on the forum already so you might try a bit more searching for even faster responses!

---

### Post by maharbA on 2007-07-27
You rock, gangolli!

Sorry to repost -- I know answering the same questions over and over isn't very fun -- Thanks for your patience.

Incidentally, the thread recommended creating a file called .smbpasswd with:
username=guest
password=

I used my own username (since I had "uid=ganco" in fstab already) and it works just fine.

---

