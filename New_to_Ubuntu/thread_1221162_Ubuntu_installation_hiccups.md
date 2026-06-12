---
title: "Ubuntu installation hiccups"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by MSXLS on 2009-07-23
Hello!
 
I heard lot about ubuntu & decided to install alongside win xp through wubi installer.
 
As it seems, the instalation does proceed through. But when i start ubuntu it seem to hang at following point, while saying
 
" formatting swap space in partition # of /host/ubuntu/disk...... "
 
and that is it.... Its been like this for more than 24 hours & progress bar does not show any update.
 
Furthermore, i tried using ms virtual pc - vm player - to install. But no avail.
 
These two programme have their own problems..
 
Somehow it does not get through.
 
My ubuntu cd is quite ok .... 
 
By the way the host file c: Is 10 gb ... And i am putting this onto other d or f: Drive having enough 8 - 10 gb space.
 
Reason i m adament on using ubuntu is i tried it on live cd - and it works fine & flawlessly. Hence its like - love at first site...
 
Please help....!!!
 
Msxls

---

### Post by masterkoppa on 2009-07-23
Something similar to this happened on my first ubuntu install. This was because of a badly burned cd. The LiveCD part worked flawlessly but when installing it failed to do so.

Therefore I would recomend you boot from the livecd and try the menu option "check cd for defects". This will check for a 100% integrity. If its no burned correctly try re-burning the iso.

Before doing that be sure to check the md5 checksum on the iso you downloaded, for more info see [here]("https://help.ubuntu.com/community/HowToMD5SUM").

GL and I hope this issue hasn't turned you around on trying out linux.

---

### Post by jmszr on 2009-07-23
MSXLS,

Welcome aboard!

First, have you defragmented your Windows d / f drives? When I installed Wubi I defragmented twice just on general principles, but at least once is necessary.
This utility (it used to be called jkdefrag) works very well:[http://www.mydefrag.com/](http://www.mydefrag.com/) .
 
Also are you aware of this: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) ? Might come in helpful.

The integrity check is very important.

---

### Post by Bucky Ball on 2009-07-23
Wouldn't bother with Wubi install again, personally. Both times I've tried it I ended up installing normally from the disk (not from within Windows).

You can choose to manually partition and just don't got near your 10Gb NTFS partition with Windows on it. It looks like you are lacking a Linux EXT3 swap file which is why you are getting the hold up.

A full install will wipe whatever is there when you set up your partitions:

/
/home
/swap

That easy (as long as the Wubi install hasn't screwed with your Windows install). And yes, could be a faulty disk.

---

