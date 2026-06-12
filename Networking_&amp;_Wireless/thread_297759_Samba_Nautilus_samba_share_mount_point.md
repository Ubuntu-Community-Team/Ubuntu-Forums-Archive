---
title: "Samba: Nautilus samba share mount point??"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by emkamau on 2006-11-11
Hi

Does anybody know where samba shares get mounted when you access them via "main menu => places => network servers"? 

I want to open some music files on my samab server with xmms on a client laptop, but I don't know where to go in directory tree once i'm in the Xmms file open dialog.

thanks

emk

P.S both computers are running Dapper Drake and I have no problem connecting to the  samba server through Nautilus.

---

### Post by bernied on 2006-11-11
Try the mount command in a terminal, while you've got the share opened. Mount, without any parameters, gives a list of mounted filesystems. Does this work?

---

### Post by emkamau on 2006-11-12
Thanks for the reply. I had to take off for awhile.

Output of mount is:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

I know that somewhere in that is what I need but its not very helpful. The question perhaps is is there a way I can configure Nautilus to mount the samba shares at a specific and consisten mount point? Is this something for udev?

thanks

emk

---

### Post by dannyboy79 on 2006-11-12
when you say connect to server thru places, it should've added a icon on your desktop, then you can click on that and it'll go to that location within nautilus. otherwise you can create your own mount point within /media or /home (/media/samba-music) and use smbfs to mount your share to that folder you created. do sudo aptitude install smbfs first just in case. i don't know of the exact website but there is a great thread within this forum for mounting samba shares. just use the search feature within the forums.

---

### Post by emkamau on 2006-11-12
I decided to do this through /etc/fstab. Its not ideal since I'm not always at home and using the samba server but I added a line to /etc/fstab and so mount -a will now mount the share to a directory under /media.

My problem was that nothing was showing up on the desktop or anywhere in the filesystem tree to let me know where nautilus was putting the samba share.

here is the fstab line:

//server/mntpt /media/mntpnt smbfs  username=emk,password=pass,umask=022 0 0 

thanks
emk

---

### Post by emkamau on 2006-11-12
I found this thread which explained things to me:

[http://ubuntuforums.org/showthread.php?p=1748025#post1748025](http://ubuntuforums.org/showthread.php?p=1748025#post1748025)

Nautilus does not mount samba shares to the filesystem! so the solution to my problem is for Nautilus developers to fix nautilus, such that it actually mount shares to some point preferably under /media. 

If enough people raise a clamour it may get done!

emk

---

### Post by dannyboy79 on 2006-11-12
i am not at home so I can't be sure of this, but something doesn't sound right abouit what you're saying? if there is a folder within media, and you mounted the mount point so it is mounted than the folder should contain the stuff that's in the folder that you're mounting, isn't that correct?  i mean what would be the point of mounting a folder from a network share if you can;'t access the files??? so i am mayube not understanding what you mean when you say that it is not mounting them to the filesystem. it sounds like waht you want is for tyhe files to be there 0on the drive??? that would only happen if you copied all the files and folders onto a folder that was mounted with a parititon locally, right?? maybe i am misunderstanding? anyway, I can say for sure that I have a smbfs entry in my fstab and the folder which is in my /home/username/folder, I can look within it in nautilus and my files ARE THERE, so maybe I just don;'t understand what you want? anyway, good luck with whatever you want, maybe you can explain it better and i'll complain with you but right now I don't agree.

---

### Post by emkamau on 2006-11-12
What I mean is that if you go to menu =>places=>network servers and access a samba share that way, it is not mounted to a specific location on the file system e.g /media/sambashare.

If you mount the share manually or via /etc/fstab you can specify a mountpoint. So there is a mountpoint for applications to go to to access the files on the share. 

This does not appear to be the case when you go via nautilus i.e thru the main menu to network servers route. At least for me, maybe I'm missing something despite having smbfs installed

Check out the thread I linked to above.

emk

---

### Post by bernied on 2006-11-13
I agree with the rant on the other thread - it seems a bit un-linux (dare I say windowsish) the way that nautilus works. Not very open. But I'm not going to take it personally because I don't use gnome. I'm pretty sure that Konqueror (the KDE equivalent) does it the way we'd like - mounts in /media - but not certain as am at work using something even more windowsish.

---

