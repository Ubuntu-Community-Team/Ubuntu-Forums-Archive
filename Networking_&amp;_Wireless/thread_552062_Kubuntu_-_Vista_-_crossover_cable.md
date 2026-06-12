---
title: "Kubuntu - Vista - crossover cable"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by Leonti on 2007-09-16
Hello!
I have a laptop with Kubuntu 7.04.
My brother has a laptop with Vista.
I want to use crossover cable to exchange some files between our laptops.
After a research I set static ips on both laptops.
PING command is working properly - I'm able to ping my laptop from my brother's laptop and vice versa.
When I connect laptops Windows Vista see this network as Undefined network.

But what next?
I have samba on my Kubuntu. My brother has file sharing enabling. But our laptops see only computers in our wireless network (which is miserably slow).
How can I make our laptops to see each other with crossover cable?

I tried o use proftpd. My brother is able to see files via ftp. Downloading speed is good, but it takes very long time to connect to my ftp or to get directory listing. For example it takes impossible long time to copy  folder with photos from my computer to his. But downloading single file is quite simple.

Can anybody help me? I need a solution to file sharing via samba (which is better) or solution to my ftp problem.
Thank you for any help! Leonti

---

### Post by pheeror on 2007-09-16
> It takes very long time to connect to my ftp or to get directory listing.
I have same problem here. Only windows machines behave this way. I guess windows does so, because they try to find your machines via wins, broadcast and lot of other things prior to DNS. I've never been so interest in it to sniff it out :-) Try another ftp client and use ip instead of name.

---

### Post by JBAlaska on 2007-09-16
There is a known bug in Vista that does that, not only with Vista to Linux but also vista to XP, there is a hotfix MS KB931770
Here's the M$ info ```
http://support.microsoft.com/kb/931770/en-us
```

M$ would have you beg for this fix...the heck with that, here's the rapidshare link lol.
```
http://rapidshare.com/files/23337348/windows6.0-kb931770-x86.msu.htm
```

It works a treat.

---

