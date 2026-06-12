---
title: "NAS Drive (smb share) not automounting after reboot"
date: 2020-12-05
forum: Networking &amp; Wireless
---

### Post by mmeir0las on 2020-12-05
hello guys

my 12TB NAS Drive is also my smb share. it works fine and i can access it on all devices, but after restart it shows like this:
[http://ibb.co/H4N3Hm2](http://ibb.co/H4N3Hm2)

i have to enter "MMSERVERDELLT40" and open the folder "MMEIROLAS" in order for it to mount it like this:
[http://ibb.co/v4KNx8B](http://ibb.co/v4KNx8B)

only once this is done i can access on all devices. problem is if i am away and suddenly power is cut, i will not be able to acess he server.
my samba config i set up like this:
[http://ibb.co/g3CPr6q](http://ibb.co/g3CPr6q)


one thing i don't understand:

in the permission properties of "/media/mmserverdellt40/wd" i can't change permission to "mmeirolas" or "sambashare" like it is set up in the samba config.
i did: 

'''
sudo chmod 777 /media/mmserverdellt40/wd
sudo chown mmeirolas:sambashare /media/mmserverdellt40/wd
sudo chmod 2770 /media/mmserverdellt40/wd
'''

didn't work either.

the sharing options for "/media/mmserverdellt40/wd" don't show as shared either:
[http://ibb.co/wQFQcS8](http://ibb.co/wQFQcS8)


could someone tell me how to fix this? changing disc options for the drive to automount at start doesn«t work since i lose complete access.

thx a lot

---

### Post by TheFu on 2020-12-05
Get a UPS, so there aren't any power outages.
Samba mounted storage doesn't support chown/chmod.  If you want that, use NFS, not CIFS/samba.  I don't know if that specific devce supports NFS or not. NFS is the native network storage protocol for all Unix. It provides native permissions.

I think that mounting really needs to happen using the /etc/fstab, never through a GUI. With the fstab, we have finer control over the mount options. Whether that is worth it to you is something only you can answer.  These forums have lots of examples for both nfs and cifs mount lines in the fstab.

---

