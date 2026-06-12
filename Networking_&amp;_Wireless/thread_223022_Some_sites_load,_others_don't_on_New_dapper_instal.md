---
title: "Some sites load, others don't on New dapper install"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by declaration on 2006-07-25
Hi,

I would be very appreciative for any help with this weird problem,

I have just installed Dapper on my desktop, booted it up, enable eth0 and opened firefox and Google opened immediately. However, if I try access almost any other website, it loads for 2+ minutes, frequently not loading at all.

All of the other computers on the network work perfectly (including an Ubuntu laptop!). I just can't figure out what the problem could be.

Have edited some settings in firefox (about:config) but the problem is not only with firefox.

The DNS settings in my "network-admin" are exactly the same as on the working ubuntu laptop.

Any help would be much appreciated- I am nearly tearing my hair out and it's too hot to be this frustrated!

Thanks

---

### Post by declaration on 2006-07-25
I just updated the firmware on my Linksys router but it still won't work.

In other news- I somehow found out that Hm.com (the clothes shop) will work. I'm gonna have fun with only about 5% of the internet I can tell.

---

### Post by declaration on 2006-07-25
update-

It behaves exactly the same under a static IP as under a DHCP- ie- not very well.

Just did a google search and I would say about 20-25% of sites will load up at full speed with the rest not working at all and a very few loading in about 90 seconds.

This is so frustrating!

---

### Post by declaration on 2006-07-25
right, am off to bed so won't be able to respond to anyones help.

I will be checking this thread as soon as I awake though so keep those ideas coming!

Thanks.

---

### Post by ilmorris on 2006-07-25
> **declaration said:**
> Hi,

I would be very appreciative for any help with this weird problem,

I have just installed Dapper on my desktop, booted it up, enable eth0 and opened firefox and Google opened immediately. However, if I try access almost any other website, it loads for 2+ minutes, frequently not loading at all.

All of the other computers on the network work perfectly (including an Ubuntu laptop!). I just can't figure out what the problem could be.

Have edited some settings in firefox (about:config) but the problem is not only with firefox.

The DNS settings in my "network-admin" are exactly the same as on the working ubuntu laptop.

Any help would be much appreciated- I am nearly tearing my hair out and it's too hot to be this frustrated!

Thanks


Have you changed the firefox settings for IPv6 yet?  With IPv6 enabled my system performed in exactly the same manner that you have described.  Disabling IPv6 in about:config within Firefox corrected my slow/no response issues for web pages.

---

### Post by declaration on 2006-07-26
yeah, I had disabled IPV6. 
Anyway, I awoke, booted and it worked!

Dont ask me why, but it did. :-D :-D

---

### Post by declaration on 2006-07-26
ok- my problem is back- dont know why but as before, some sites load but most dont.

This is the infuriating computer problem I have ever experienced. I dont know why it is, have any idea why it could be happening.

---

### Post by declaration on 2006-07-26
This problem is not ipv6 related.

I have disabled ipv6 both system wide and in firefox but the interney still will not function properly.

Its so strange that it would work for about 3 hours, but revert to non-working after a reboot.

---

### Post by mips on 2006-07-27
lets see your resolv.conf and interfaces files.

---

