---
title: "Why is /home not formatted."
date: 2011-06-01
forum: New to Ubuntu
---

### Post by OldBoy44 on 2011-06-01
Hi all,

This is probably a naive observation but I am interested in knowing why a /home partition is not formatted. I have done a bit of reading but have not been able to get an answer that I understand. 
Thanks in advance for any response.

Cheers,

---

### Post by seawolf167 on 2011-06-01
All usable partitions are formatted, else they show as "Unallocated Space".

Windows formats in NTFS
Ubuntu formats in ext4 (or ext3 for older systems). So your /home partition is formatted as either ext3 or ext4
DOS and flash drives use FAT
etc, etc, etc.

---

### Post by TeoBigusGeekus on 2011-06-01
I guess you mean it's not formatted when you reinstall.
The /home partition holds all your personal preferences/settings of all the software you use: from your desktop wallpaper, to your most obscure setting of your most obscure app.
When you do a reinstallation and you leave your /home partition intact, you will magically see all your preferences reapplied on your new system.
So, say for example that you've configured Opera just the way you like it.
But suddenly, you decide to reinstall; leaving the /home partition unformatted and using it again as your new home folder, will keep the .opera folder intact, thus keeping all your preferences, bookmarks, etc. as they were.
When you install Opera after the reinstallation of your system, you will magically see when you open it that it is just the way you left it before you reinstalled.
I hope you get the idea.

---

### Post by jerome1232 on 2011-06-01
Do you mean that the automatic partitioner that Ubuntu uses doesn't format /home if it see's an existing one?

You need to put this in context to get a helpful answer, I assume the automatic partitioner may not format an existing /home to preserve personal data.

---

### Post by Locke_99GS on 2011-06-01
By default, /home is not separated into it's own partition.

---

### Post by OldBoy44 on 2011-06-01
Thanks for that seawolf167 - I feel a bit of a fool now. I'm sure I read that somewhere but maybe I misinterpreted what I saw.

Thank you!

I was referring to a fresh install with manual application.

---

### Post by seawolf167 on 2011-06-01
> **aussiebean said:**
> Thanks for that seawolf167 - I feel a bit of a fool now. I'm sure I read that somewhere but maybe I misinterpreted what I saw.

No worries at all! See jerome or Teo's posts above - the confusion is probably here: if you have an *existing* /home partition you don't want to format (again) it since formatting erases everything on the partition, so then you wouldn't format it (i.e. since it is already formatted)

---

### Post by OldBoy44 on 2011-06-01
Hi and thanks guys for your response.

I get it now - 

Cheers, :p

Edit - I just had to add this edit - this is really a great forum, the response was amazing!

---

