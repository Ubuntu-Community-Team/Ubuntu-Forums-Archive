---
title: "Slow internet speeds when connected behind router in Gutsy"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by fistikuffs on 2007-10-27
Hi I'm pretty new to linux in general and I'm certainly no network expert so if someone could help it would be great.

I was initially connecting to the net directly  through my dsl modem with the default auto dhcp settings in Ubuntu. I've just recently installed a wireless router and i've connected my ubuntu desktop to the router through an ethernet cable. I used basically the same tcp/ip settings i used in xp i.e. a static ip, default router, subnet mask and two dns servers. 
I can connect to the internet fine but the connection is a lot slower than it was when connected directly to the dsl modem. The ubuntu desktop dual boots with xp and there has been no performance decrease when running xp so hopefully its just some settings i need to change in ubuntu. Does anyone have any ideas?

Thanks for your help

---

### Post by Lambert on 2007-10-28
After connected for a few minutes, run the following command and post output here.

```

sudo ethtool -S eth0

```

replace eth0 with your interface if different.

Also try this as I believe this might be more of the solution.

Edit your hosts file so it looks like this.

```

127.0.0.1 localhost.localdomain localhost _______

```

Insert the hostname that you set up for you computer in the blank line.

---

### Post by moe_syzlak on 2007-11-29
this prolem has been solved here ---> [http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744)

please search the forums for a solution BEFORE asking for help. many problems advanced and some of the noob problems (such as "how do i get root on my computer," or "how to install xxxxx package" that is in the repository) have been fixed. and you can get the answers to your problem by searching

---

### Post by fistikuffs on 2007-12-23
Thanks for replying and moe_syzlak the solution you linked to was posted after i posted this thread so unless you're saying there is some way to search future threads maybe you should check things out before you slap down some more noobs. Thanks again!

---

