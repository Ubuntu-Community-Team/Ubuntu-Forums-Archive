---
title: "how do you calculate swap?"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by 007casper on 2011-08-02
how do you calculate swap?

I have always followed psychocats instructions in setting swap "1.5 or 2 times the size of your computer's RAM".  
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Recently, I was told otherwise...

When setting a virtual server, the virtual server was set to minimum install, and I was advised to only use 256 MB swap image.  The ram on the virtual server was set to 512 MB.  I was surprised.  They said anything higher will create high Disk I/O rate, thrashing, and slow down the server. So, I set it to 256 MB for swap. The server seems to be snappy, which is good.  

Now, I am wondering.  How do you really calculate swap?

I also checked out...
[http://en.wikipedia.org/wiki/Swap_partition#Swapping_in_the_Linux_and_BSD_operating_systems](http://en.wikipedia.org/wiki/Swap_partition#Swapping_in_the_Linux_and_BSD_operating_systems)

any ideas?

---

### Post by mcduck on 2011-08-02
The rule for twice the amount of RAM was valid years ago when computers had much less RAM. Not so any more, and it's more than likely you won't really even end using the swap space much, apart from storing data when hibernating the system.

So, if you don't use hibernate, you just need a bit of swap defined just in case. A gigabyte or two would be a plenty.

..and if you *do* use hibernate, you need to have a bit more swap than you have RAM. Like swap=RAM+512MB for example. (hibernating stores all data from RAM into swap, so this gives you enough swap to do that plus a little more working space)

---

### Post by 007casper on 2011-08-03
thank you

---

