---
title: "Karmic-Partition Mount Authentication"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Darce on 2009-10-31
Hi guys,

Installed Karmic yesterday and love it. I'd been using Jaunty for six months or so.
I've noticed since I (fresh) installed Karmic, whenever I access a certain partition for the first time after a reboot, I need to Authenticate.

I never had to do this for this particular partition under Jaunty.
Is there a permission or security setting I can change ?

Not a REAL problem, just a little annoying    ;)

Cheers,

Tim

---

### Post by RC1139 on 2009-10-31
Follow this link, it has a section for automatically mounting on boot.
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by raulih on 2009-11-02
> **Darce said:**
> I've noticed since I (fresh) installed Karmic, whenever I access a certain partition for the first time after a reboot, I need to Authenticate.

See this: [http://art.ubuntuforums.org/showthread.php?p=8219205#post8219205](http://art.ubuntuforums.org/showthread.php?p=8219205#post8219205)

---

### Post by Darce on 2009-11-02
> **raulih said:**
> See this: [http://art.ubuntuforums.org/showthread.php?p=8219205#post8219205](http://art.ubuntuforums.org/showthread.php?p=8219205#post8219205)

Thanks for the info Raulih.

Followed the post, but the file being referred to in the Authentication dialog box (org.freedesktop.devicekit.disks.filesystem-mount-system-internal) doesnt exist in my filesystem, or at least, doesnt show up with the 'search for files' tool.

Though it does seem to be going in the right direction, so I'll follow that thread and abandon this one.

Thanks again,

Tim

---

### Post by Darce on 2009-11-02
Problem solved thanks to pjomega.

Cheers and thanks to all that helped !

---

### Post by raulih on 2009-11-02
> **Darce said:**
> Followed the post, but the file being referred to in the Authentication dialog box (org.freedesktop.devicekit.disks.filesystem-mount-system-internal) doesnt exist in my filesystem, or at least, doesnt show up with the 'search for files' tool.

It's said unclear. File is /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

and there is action id "org.freedesktop.devicekit.disks.filesystem-mount-system-internal" and editing "defaults > allow_active" to "yes" solved it to me.

---

### Post by Darce on 2009-11-02
Probably more to do with my mind being unclear ;)

Thanks again !

---

