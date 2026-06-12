---
title: "SMB sharing"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by biozit on 2008-06-05
Hi all!

I need to mount a windows sharing and i tryed put in fstab:

//192.168.5.3/c /media/asdf cifs username=qwe,password= 0 3 

but when the macnhie with windows is off when the ubuntu machine is  moutn the devices the share is NEVER mounted...

exist aonther way to do that ?


thanks..

---

### Post by jetsam on 2008-06-07
You can mount this share while running with:
```
sudo mount /media/asdf/
```
and unmount it with:
```
sudo umount /media/asdf/
```

If you have more than one share with the same problem, you can re-run all the automounts in your fstab with:
```
sudo mount -a
```

I think you want to change that final 3 in the fstab line to a 0.  This tells the system not to try to run fsck on your network mount at boot time.

---

