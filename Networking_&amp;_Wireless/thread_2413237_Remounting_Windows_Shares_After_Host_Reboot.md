---
title: "Remounting Windows Shares After Host Reboot"
date: 2019-02-22
forum: Networking &amp; Wireless
---

### Post by bzowk2 on 2019-02-22
Hey Guys - 

I recently rebuilt my Plex server - this time using Ubuntu 18.04.  All of the media it accessed is located on my primary Windows 10 box, though; as it's in an 11 disk drive pool.  I've successfully mounted a couple of folders on the Ubuntu system using cifs and had no issues except for one thing.  

Whenever I need to restart the Windows system, I expect to loose access to the media for obvious reasons in my mounted shares.  When the PC is back up, those shares do not automatically re-mount; though as I am unable to browse to them.  I tried executing 'sudo mount -a" hoping it would remount them, but no go.  The only easy resolution so far is to restart the Ubuntu system where they then work fine again as they mount on boot.

What can I do to resolve this so I don't have to restart Ubuntu every time I loose network connectivity or restart the Windows system?  Worst case, I guess I could script something that uses cron to check the mounted folders then run a command if not accesible, but was hoping for a better solution or script perhaps.

Thanks!

---

### Post by TheFu on 2019-02-25
Use **autofs**, but I'd move all that media storage over to Unix where I would have much more control and easily provide solid access to other systems.  But that is just me.

BTW, sometimes Windows shares just lock up. I've never found a 100% solution around that issue.  About once a month, my Win7 share locks up. I've patched and applied KB registry modifications trying to fix it - no joy.

---

