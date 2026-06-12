---
title: "No Wireless Networks detected after installing Broadcom STA (BCM4311) drivers"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by computerandu on 2011-05-04
Hi all,

I installed Ubuntu 11.04 (wireless was working while installing). Wireless networks were even available after restating and using it for the first time...then there were message from ubuntu that restricted drivers are available for Broadcom STA (BCM4311) (why did it ask me to download the wireless drivers when wireless was working on the first hand..??).
Any ways... I said...why not...I clicked on the activate button...it installed the driver and asked me to restart...i restarted it ..and there you go...wireless is on...but it detects no networks...
:(

---

### Post by xellink on 2011-05-04
> **computerandu said:**
> Hi all,

I installed Ubuntu 11.04 (wireless was working while installing). Wireless networks were even available after restating and using it for the first time...then there were message from ubuntu that restricted drivers are available for Broadcom STA (BCM4311) (why did it ask me to download the wireless drivers when wireless was working on the first hand..??).
Any ways... I said...why not...I clicked on the activate button...it installed the driver and asked me to restart...i restarted it ..and there you go...wireless is on...but it detects no networks...
:(

Have you updated? If it doesn't work after updating, you can try removing the drivers

[I]sudo apt-get remove bcmwl-kernel-source

[/I]This is a bug in 11.04. If the previous drivers work stable, then it should be fine. On the other hand, look at this post

[http://ubuntuforums.org/showthread.php?t=1744363](http://ubuntuforums.org/showthread.php?t=1744363)

You may want to consider downloading one of the other broadcom drivers and installing it instead (found in the post on the link above).

Or download here
32 bit: [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)
64 bit: [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb)

---

### Post by computerandu on 2011-05-04
> **xellink said:**
> Have you updated? If it doesn't work after updating, you can try removing the drivers

[I]sudo apt-get remove bcmwl-kernel-source

[/I]This is a bug in 11.04. If the previous drivers work stable, then it should be fine. On the other hand, look at this post

[http://ubuntuforums.org/showthread.php?t=1744363](http://ubuntuforums.org/showthread.php?t=1744363)

You may want to consider downloading one of the other broadcom drivers and installing it instead (found in the post on the link above).

Or download here
32 bit: [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)
64 bit: [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb)



I guess your information is pretty concise...will try to work with it once i reach home...thanks for the download links though....

---

### Post by hbpasti on 2011-05-04
This worked for me:
[http://ubuntuforums.org/showthread.php?t=1745437]("http://ubuntuforums.org/showthread.php?t=1745437")

---

### Post by computerandu on 2011-05-05
Thanks for everyone suggestion ...its working now...i deleted the newly installed propriety driver and then installed the one downloaded from the ubuntu repository....turned it off (not restart... strange but worked) ...and now its working flawlessly....

I hereby declare the thread closed...

---

