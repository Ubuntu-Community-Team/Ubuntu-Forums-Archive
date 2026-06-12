---
title: "Can't boot Ubuntu!"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by lesPaul456 on 2010-02-02
Hello,

I just installed Ubuntu 9.10 on a partition on my laptop (I'm dual-booting Vista and Ubuntu). So far everything has gone pretty smoothly. 

However, after connecting to the internet, the UpdateManager showed up and said I needed to install some packages, which I did. Then a message box appeared saying I need to restart. So I selected "Restart Now".

After rebooting, I got the normal Grub screen. I selected Ubuntu. Rather than booting up, however, I got this message on a black screen:

```

fsck from util-linux-ng 2.16
/dev/sda5: clean, 152807/917504 files, 76637/3666828 blocks
init: udevtrigger main process (495) terminated with status 1
init: udevtrigger post-stop process (497) terminated with status 1
init: udevmonitor main process (494) killed by TERM signal
init: networking main process (500) terminated with status 1
^@

```I have no idea what this means, or what I'm supposed to do. Any suggestions?

Thanks!

---

### Post by Psumi on 2010-02-02
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/433943](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/433943)

comment number 2

---

### Post by lesPaul456 on 2010-02-02
Thanks, I'll try it out.

---

