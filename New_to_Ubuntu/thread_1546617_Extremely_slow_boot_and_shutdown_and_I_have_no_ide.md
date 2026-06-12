---
title: "Extremely slow boot and shutdown and I have no idea why."
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Atrophy on 2010-08-05
Hi everyone =) 

I've been using Ubuntu for a few months now. I have the 64 bit version of 10.04. My issue is that when booting into Ubuntu, it's extremely slow. I'm talking minutes here. When I shut down the computer, the same thing occurs. Occasionally it won't even shut down but just hang. It may not be hanging, but after about 5 minutes I get tired of waiting. 

I have no idea why this is happening. 

Some other specifications that seem important are my system is set to dual boot along with Win 7 64-bit. The model of my computer is the Asus M50. Instead of copying all the specs, the computer can be found on Newegg here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834220343&cm_re=asus_m50-_-34-220-343-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220343&cm_re=asus_m50-_-34-220-343-_-Product)

I hope someone can point me in the right direction to solving this issue. I'm happy to cooperate with anyone who's willing to do so.

---

### Post by corrytonapple on 2010-08-05
Is it slow shutting down in 7? Are you using programs that use a lot of memory? Looks like a good computer.

---

### Post by NightwishFan on 2010-08-05
Generally a long boot is caused by a floppy drive enabled in the bios (even if you do not have a floppy). Turn off any such options first to see if boot improves. Also, perhaps post your /var/log/syslog here either as a file or inside code (#) tags.

---

### Post by Atrophy on 2010-08-05
I've done a bit of reading thus far - seen the issues with the floppy drive. I've made sure this is definitely not enabled. 

A friend of mine suggested it may be an issue with ext4 and recommended reinstalling with ext3.

Win 7 boots and shuts down normally. 

Before I post it, I want to say that /var/log/syslog is *huge*. Perhaps it would be smaller after a reboot? I'm not sure how this file works exactly.
ror

As far as memory intensive programs go - i'm not running anything out of the ordinary. Chrome and compiz seem to be the most resource intensive. Other than that I typically have open office up, vlc, rtorrent or transmission, skype, and that's about it.

I also have a blank ext3 partition formatted and ready to go... but i'm not sure what to copy and how I would change grub and anything else I'd need to make the system boot properly.

Update: This only happens when I fully shutdown. The slowness doesn't occur when I reboot.

---

### Post by Atrophy on 2010-08-05
Im going to narrow this problem down:

There is a 30 second pause after I select Ubuntu in Grub and when Ubuntu actually starts loading. 

How do I get rid of this pause?

---

### Post by NightwishFan on 2010-08-05
Is this relevant perhaps?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/247960/comments/27](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/247960/comments/27)

---

