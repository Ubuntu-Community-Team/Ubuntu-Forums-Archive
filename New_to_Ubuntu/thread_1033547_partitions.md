---
title: "partitions"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by supererki on 2009-01-07
so i managed to mess up my ubuntu again so badly that i decided to go to fresh install... and im trying to be a bit smarter this time.
so please somebody give me a reasonable partition scheme. 
i mean. what system folders should i put to separate partitions (like /boot etc) .. and what fs to use. thanks

---

### Post by decoherence on 2009-01-07
I suggest using ext3. On partition for / one partition for /home (and of course one for swap... it'll take care of that.)

That's about as reasonable a partition scheme as you'll get. You can do more but there isn't much reason to unless you're running a server.

---

### Post by swoody on 2009-01-07
> **decoherence said:**
> I suggest using ext3. On partition for / one partition for /home (and of course one for swap... it'll take care of that.)

That's about as reasonable a partition scheme as you'll get. You can do more but there isn't much reason to unless you're running a server.

I would agree with this. I'd use all ext3 file systems, and have ~10GB for your '/' partition, whatever you have left over for your '/home' partition, and a swap size between your RAM size and up to double your RAM size (if you have very little RAM).

Having a separate '/home' partiton makes upgrading, or reinstalling Ubuntu VERY easy and hassle-free as it keeps your personal info separate from the OS's info :) You could always go more in depth with more partitions, but this is all I'd ever recommend to anyone.

---

