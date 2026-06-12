---
title: "[SOLVED] Permissions Problem"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by cdmike2k8 on 2008-12-07
I have some external hard drives that mount through fstab at startup, and I want to set myself as the owner so that I can move them, currently, I only have read access.  Here is their entry in fstab.  ```
# Entry for FreeAgent1
UUID=9E5C35DE5C35B1BF /media/FreeAgent1 ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
# Entry for FreeAgent2
UUID=2D5E1CE7072C111E /media/FreeAgent2 ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
# Entry for FreeAgent3
UUID=7E3408A33408608F /media/FreeAgent3 ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
#Entry for IO Magic
UUID=5C9C67879C675B12 /media/IOMagic ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
#Entry for Maxtor 500
UUID=5d260b49-8a16-4df2-9dae-337614a3783e /media/Maxtor500 ext3 auto,users,relatime 0 0
```
What should I change, or is there a different way to go about it?
Thanks, Michael

---

### Post by snova on 2008-12-07
Try chown'ing them to your user. Something like:

```
sudo chown <user>:<user> -R /mount/point
```

Run for each disk.

Careful not to run it on anything else.

---

### Post by cdmike2k8 on 2008-12-07
Thanks, worked great!

---

### Post by drs305 on 2008-12-07
Edit:  Too late, as the issue appears resolved. If not, read on...

In addition to snova's suggestion, for the ntfs partitions, ownership is set at the time of mounting. Unless it is a cut & paste or thread formatting issue, your fmask settings appear have an extra space ( [COLOR="Red"]fmask= 1 37[/COLOR] )

Make sure your ntfs lines look like this:
```

ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,[COLOR="Red"]fmask=137 0 0[/COLOR]

```

---

### Post by cdmike2k8 on 2008-12-07
I did what both of yo said.  I do have the permissions to move files though.  When I restart, I get the error User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users.  I didn't touch the Ubuntu partition with either chown or edit the fstab for the ubuntu parition.

---

### Post by snova on 2008-12-07
I've seen that error before, but I don't recall the solution. But try this anyway, it might be right:

```
sudo chown <user>:<user> ~/.dmrc
chmod 644 ~/.dmrc
```

---

### Post by drs305 on 2008-12-07
If snova's solution doesn't completely solve it, refer to this post. There are a couple of other things you can do and it explains what the error message means:
[http://ubuntuforums.org/showthread.php?t=976610]("http://ubuntuforums.org/showthread.php?t=976610")

---

### Post by cdmike2k8 on 2008-12-07
After correcting the .dmrc file, the problem was not solved.  I followed the instructions in the link provided by drs305 and it solved the problem.  Not sure what I did to screw it up, but thank you guys!

---

