---
title: "How to access files from Live CD Boot/Upgrade Issues"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by dodgerwv on 2009-11-01
Here's the error message that I get trying to boot after upgrading to 9.10:

init sreadahead main process (257 terminated with status1
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (2579) terminated with status1
General error mounting filesystems
A maintainance shell will now be started
CONTROL-D will terminate this shell and re-try
root@ dell-desktop:~#

Computer freezes at this point. It's a Dell Inspiron 530 if that matters. 

Used the Live CD to boot and all of my data is fine. Yes, I fully admit my idiocy for not backing up prior to the upgrade.

How can access my documents, pictures, and music from the Live CD to back them up in order to perform a fresh install or should I try to fix the boot loader? I'm guessing the easiest option for a relative newbie would be to do the fresh install?

Thanks in advance for any help!

---

### Post by philinux on 2009-11-01
Reboot and get to that root prompt.

Then type this is and press enter.

```
sudo apt-get update && sudo apt-get upgrade
```

Then type restart to reboot.

---

### Post by dodgerwv on 2009-11-01
No luck.  The screen is frozen at that point.  At this point, I'm willing to do a fresh install.  Just looking for help on how to get to my info.

---

### Post by philinux on 2009-11-01
Ok in that case all you need is a usb stick formatted ext3 or 4. Then use the livecd to copy your important stuff to it.

---

### Post by dodgerwv on 2009-11-01
What do I need to do to set the permissions?  I'm assuming that I have to somehow go into terminal and log in as myself.  I can't move some of the files by just opening the home folder.

---

