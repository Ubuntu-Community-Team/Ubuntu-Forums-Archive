---
title: "mac80211 nightmares..."
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by dgtldaydrmr on 2007-09-13
There seems to be limited # of posts on this topic perhaps someone may be able to help though...

Toshiba Qosmio F40
Intel AGN wireless

It's one nightmare after the next trying to setup the mac80211 package.
I have tried to closely follow the instructions on the site intellinuxwireless.org
The main problem is it assumes you know exactly what you are doing :P
I got as far as "make modules modules_install" and I get an error that is relatively foreign to me.


> make[1]: *** no rule to make target `init/main.o`, needed by `init/built-in.o`.
 Stop.
make: *** [init] Error 2


Any help would be greatly appreciated!
Thanks.




Update 1:
From what I have read the 2.6.22 Kernel has mac80211 integrated into it already.
So I will try updating to a newer Kernel and post my results.
I don't foresee a big issue installing the Intel drivers once the mac80211 issue is non existent :P
I am still looking for input from other users about this issue though!

---

### Post by dgtldaydrmr on 2007-09-13
kernel updated to 2.6.22 and followed directions in the following post.
[http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)

Everything appeared to work but still no wireless adapter showing up anywhere.
What am I missing or overlooking?

---

