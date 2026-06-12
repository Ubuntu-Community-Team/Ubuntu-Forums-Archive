---
title: "Users mounting flash drives"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by jw29 on 2007-04-20
Hello,

I am having problems trying to figure this out...

On our network, users are authenticated through LDAP.  Thus, they do not appear in any of the groups like plugdev, cdrom, etc. in /etc/group.  All we really need working is automounting USB flash drives, although access to the cdrom would be nice, also.

Is there something I can edit to give them permission to these devices?

I tried adding MODE="0666" to various lines in /etc/udev/rules.d/40-permissions.rules, but nothing I tried worked.  This method did work for giving the LDAP users the ability to use sound -- by adding MODE="0666" to the end of the SUBSYSTEM="sound" line.

I know I can just edit fstab (which is how it's set up now), but I'm sure there's probably a way to have it automatically mount them.

If you could provide any assistance or point me in the right direction, I'd really appreciate it.

Thank you.

---

### Post by chaos51 on 2008-04-16
Hi,
  I am running into this same problem with Gutsy.  Did you even find a solution?
 thanks,

---

### Post by chaos51 on 2008-04-16
Well, after playing around a lot in udev and with pmount and hal, I kind of got things working by changing the following in /etc/dbus-1/system.d/hal.conf

I changed:
  <policy group="plugdev">
    <allow send_interface="org.freedesktop.Hal.Device.Volume"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume.Crypto"/>
  </policy>


to this:
  <policy context="default">
    <allow send_interface="org.freedesktop.Hal.Device.Volume"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume.Crypto"/>
  </policy>

I must admit at the moment I don't know all the consequences of making that change (trying to find some info on it), but it looks like it allows as user to go to "Places"->"Computer" , right click on the flash drive and click "mount" and it puts a "disk" icon on the desktop which is then accessible to the user.

They can then right click the "disk" icon on the desktop and choose "unmount" to safely remove it.

While not as nice as just plugging it in and having it automatically pop-up on the desktop it is at least usable (with the caveat that I'm unclear to all the possible consequences of the change I made).  Not entirely smart on my part but at the moment it works until I can find something better.

---

