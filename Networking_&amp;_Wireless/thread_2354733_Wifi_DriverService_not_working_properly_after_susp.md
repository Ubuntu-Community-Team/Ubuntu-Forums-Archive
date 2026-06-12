---
title: "Wifi Driver/Service not working properly after suspend or hibernate"
date: 2017-03-05
forum: Networking &amp; Wireless
---

### Post by C0NFU53D2 on 2017-03-05
Hey all, I have been away from the linux community for a while now, but I'm coming back.  So i tried googleing my problem, and i found other people with similar yet different problems and none of their fixes worked.  I originally had this problem on LinuxMint, but then I reformatted and installed Ubuntu to see if maybe it was distro related, but the problem persisted, so I'm coming to you guys with a new post.

So I have a fresh install of Ubuntu, and i installed the bcmwl-kernel-source driver for my wifi card, and it works just fine, untill i put my computer in hibernate or suspend it.  upon resuming the wifi card interface claims to be working, but it cannot see any wireless networks to connect to except a printer...

Any help would be greatly appreciated. Thanks!

---

### Post by wildmanne39 on 2017-03-05
Sounds like the network manager, you can find a work around here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1576747](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1576747)

---

### Post by C0NFU53D2 on 2017-03-05
Unfortunately, that didn't work, same result. :-(

Thanks for the quick reply btw!

---

### Post by wildmanne39 on 2017-03-05
Please post exactly what you did, and run the wireless script in my signature and follow the directions in the link for posting it to pastebin.
Thanks

---

### Post by C0NFU53D2 on 2017-03-05
ok, its at [http://paste.ubuntu.com/24122307/](http://paste.ubuntu.com/24122307/)
I also continued and followed the broadcom directions that followed, and the result is exactly the same.

---

