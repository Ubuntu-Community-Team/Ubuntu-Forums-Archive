---
title: "Restoring w/rsync and file permissions"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-02-18
Using this line, and NO sudo:

rsync -avz --delete --exclude=".*/" /home/mark/ /media/TV/backup

I bu'd my  /home  to an external usb drive.

I now need the command line argument to restore about 23 gig of files.

Even though there is an --exclude argument with the rsync, on looking for hidden files in the bu I see some files, not folders. These may be temporary files, but as I don't want problems, if I can avoid them, I'm asking, in advance.

Some filenames:

.bash_history
.bash_logout
.bashrc
.bzr.log
.dmrc
.sudo_as_admin_successful

and a few others. I have only given examples.

I looked at the permissions for this drive and see that my username is correct and that I have folder read and write access. The group name is correct, too, but the group owner has no read and write permissions. Also, as some hidden (dot) files were brought over in the bu, do those files need to be made executable, while there are on the external drive?

My last question is, I believe that to restore from the external USB drive to my  /home,  the command line argument is:

rsync -avz /media/TV/backup/ /home/mark/

Can someone confirm that this is [COLOR="Red"]correct?[/COLOR]

the device where the files are to go is:  /dev/sda5  -that is my new, bare-metal,  /home partition.

If you have read this far, please know that I have looked over UbuntuForums and netsearched (that's Googled in bad English) for rsync how-to's. I have read the rsync man pages. The problem is that the forum threads are for individuals, although they speak to generalities. The how-to's don't talk about file permissions that reflect the string or argument I used to begin with. Or there are soooo many that I cannot understand where to start (or stop). I don't need to get a B.S. degree in rsync, I need to restore my files. Thank you, Community, for your time.

---

