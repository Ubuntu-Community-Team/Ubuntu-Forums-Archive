---
title: "Profiles from Thunderbird Mozilla"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by ian19jam on 2009-05-22
I wish to transfer my Profiles from the Microsoft backup of My Thunderbird Mozilla to my Thunderbird Mozilla on Ubuntu 9.04 version 1386. Can anyone please tell me how to do this. I am very amateur so could you be very simple and clear about what I have to do.

Many thanks.

---

### Post by Didius Falco on 2009-05-22
> **ian19jam said:**
> I wish to transfer my Profiles from the Microsoft backup of My Thunderbird Mozilla to my Thunderbird Mozilla on Ubuntu 9.04 version 1386. Can anyone please tell me how to do this. I am very amateur so could you be very simple and clear about what I have to do.

Many thanks.

It's fairly simple. Here is a guide that will walk you through it step-by-step. The hardest part for me back when I made the switch was finding the right folder on Windows. <G>

[http://fosswire.com/post/2008/3/migrate-your-thunderbird-emails-from-windows-to-linux/](http://fosswire.com/post/2008/3/migrate-your-thunderbird-emails-from-windows-to-linux/)

If you are keeping your Windows Thunderbird install, though, you may want to consider sharing the profile.

Here is a guide to doing that:

[http://ubuntuforums.org/showthread.php?t=1138477](http://ubuntuforums.org/showthread.php?t=1138477)

If you go for door #2, my suggestion would be to use a shared DATA partition in NTFS format. 9.04 with ntfs-3g can read/write to NTFS with no problems, while Windows can get a bit sticky about ext3 partitions.

The advantage being that whether you use Thunderbird in Windows or Ubuntu, you have the same emails, rather than having some in one account and some in another.

I hope this helps...

Regards,

Didius

---

