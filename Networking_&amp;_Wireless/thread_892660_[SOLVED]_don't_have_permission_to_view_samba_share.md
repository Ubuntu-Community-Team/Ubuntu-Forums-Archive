---
title: "[SOLVED] don't have permission to view samba share"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by Tails Prower on 2008-08-17
I read [this guide]("http://www.howtoforge.com/ubuntu-home-fileserver-p3") on setting up a fileserver (it basically guides you through installing ubuntu server and remoting in with ssh to set up samba) I've got the OS installed, I can remote in with ease, and I've mounted an ntfs hard drive to the mount point /media/launch_base/.  I can view the folder (launch_base) by typing smb://death-egg/launch_base (you'll notice many sonic references here...) into firefox's address bar, but there are subdirectories under that folder that I can't view. Furthermore, attempting to browse the folder by following the menu trail of places>network>death-egg>launch_base yields the result:
UNABLE TO MOUNT LOCATION
unable to mount windows share

I'd like to think it's a permission problem, but I've run chmod 777 on the launch_base folder many times...

I'd like to paste some related files in here, but I'm remoting in, so I'm not quite sure how to copy blocks of text (vi is a strange creature...) all the same, here are some slices of file I think could be helpful:

from fstab:
/dev/sdb1     /media/launch_base ntfs defaults 0 0

from smb.conf:
============================================================
[launch_base]
comment = Public Folder
path=media/launch_base
browseable=yes
public=yes
writable=yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = no group

;D
;path
;[sb
;D
;[hda public
===========================================================

I dunno what all that commented out garbage is doing there, but the command /etc/init.d/samba force-reload would consistently fail until i commented that out.

thanks in advance for any help, and if you need any more info, let me know.

---

### Post by Tails Prower on 2008-08-17
Solved the problem by changing

force group = no group
to 
force group = nogroup

and adding the line
guest ok = yes.

---

