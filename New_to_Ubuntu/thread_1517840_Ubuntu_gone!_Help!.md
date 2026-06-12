---
title: "Ubuntu gone! Help!"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by tonsil on 2010-06-25
I was using Ubuntu 10.04 happily for a few months now, when something happened today. During the boot there were some error messages all in text, something regarding ext3. They were too quick for me to take note, and when I restarted my PC Ubuntu started working again. However it froze while browsing, so I restarted and it worked a little bit. But now when I boot, I can't even see the login screen. It just stays there black. I've tried recovery mode from the grub menu to no avail. I've tried every option in the grub menu and the result is the same; a black sreen.

So I plugged in my other hard drive; I keep it seperate, and I have Xubuntu 10.04 on it. When I use gigolo to mount the partition I get this error message:

Connecting to "65 GB Filesystem" failed.

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Do you have any idea what could have happened? What can I do?

---

### Post by barney385 on 2010-06-25
I think you can use the liveCD and run fsck.

I'd check around to be sure though.

Here's a link with a similar dilemma: [http://www.linuxquestions.org/questions/linux-hardware-18/mount-wrong-fs-type-bad-option-bad-superblock-on-dev-hdc3-373428/](http://www.linuxquestions.org/questions/linux-hardware-18/mount-wrong-fs-type-bad-option-bad-superblock-on-dev-hdc3-373428/)

---

### Post by tonsil on 2010-06-25
I can't seem to be running some of the software, but fsck solved it! THANK YOU!!!

---

