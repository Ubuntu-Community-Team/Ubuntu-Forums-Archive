---
title: "If I use fstab to mount a different path to /home, where does the original /home go?"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by diablo75 on 2010-12-13
I am in the middle of revising a guide for how to migrate a Home folder from the default location on the / partition on to a separate partition that will be dedicated to /home and nothing else.  The steps (as of right now) go as follow:

1.  Setup your new partition
2.  Backup and edit your fstab to mount the new partition as /media/home (just for the time being) and reboot.
3.  Use rsync to migrate all data from /home into /media/home.
4.  Edit fstab again so the new partition mounts as /home instead of /media/home but don't reboot yet.
5.  Move /home to /old_home and reboot
6.  Delete old home.

In the unlikely event the computer were to be rebooted in between steps 4 and 5, the result would be that the new partition would mount as /home and the contents of the old home would seem to become invisible.

I tested this out in a VM by creating a folder with a unique name on my desktop, then edited the fstab and rebooted without moving the old home folder out of the way.  This results in the contents of the new home partition taking precedence over the old one, the contents of which are located who knows where...  This is what I'm curious about.  What happens to the original contents of /home?  Where does it go?  How might you access and delete these files if something is being mounted over top of them?  

To further the experiment along I edited fstab a third time and reverted back to have the new partition mount as /media/home and the original /home came back, along with that folder I had created.  So the contents of /home can't be harmed if you use fstab to mount something overtop of it, but they can seemingly be "hidden".

Can someone enlighten me about what's going on here?  I'm really curious about this.

---

### Post by potat on 2010-12-13
You're basically right. Nothing happens to the files, but when you (the user) look for the home directory, the OS shows you the directory that was mounted there no matter what was originally there. As long as it's mounted, I don't think there's a way to access those original files, but they won't be lost either.

See:

[http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.baseadmn/doc/baseadmndita/mountpoint.htm](http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.baseadmn/doc/baseadmndita/mountpoint.htm)

[http://www.mail-archive.com/linux-fsdevel@vger.kernel.org/msg02288.html](http://www.mail-archive.com/linux-fsdevel@vger.kernel.org/msg02288.html)

---

