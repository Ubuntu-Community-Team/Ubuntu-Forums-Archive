---
title: "Problems with Network Manager/Wicd"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by IamReck on 2008-04-29
I found Wicd a while ago and was looking to install it, and just did it today.  It worked great, but upon turning my computer off and on again, I could not get it to start.

So I have to go back to Network Manager.

Unfortunately, my Ubuntu Computer does not have internet access because Wicd is not working, and I can not connect to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) (it is too busy).

I have an Ubuntu 8.04 Live CD, I was wondering if there was anyway I could use it to get the Network Manager packages.  Or if anyone had a the Network Manager debian file anywhere...

---

### Post by Whiffle on 2008-04-29
Actually I think your problem might be that the wicd daemon isn't starting.  Try doing:

sudo /etc/init.d/wicd start

next time you boot it up, then try wicd.

---

### Post by IamReck on 2008-04-29
I have tried that, as well as all the things listed in the FAQ section of Wicd site.

Please answer my question about the Network Manager package, not how to fix Wicd.

---

### Post by IamReck on 2008-04-30
[[COLOR=#444444]http://packages.ubuntu.com/[/COLOR]]("http://packages.ubuntu.com/")  Is now back up, I was able to download the debian packages and reinstall Network Manager.
 
My original question still remains, in Hardy, how can I use my Live CD as a repository?

---

