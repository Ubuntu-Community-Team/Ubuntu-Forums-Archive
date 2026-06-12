---
title: "question about upgrade with / on one drive and one for /home"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-06-28
Hi Ubuntu Community:

I installed Ubuntu on a new machine and used the custom install to:

[LIST]
[*]put the operating system (/) on one drive, and
[*]to put my /home directory on a different drive.
[/LIST]

The hard drive I've installed the OS on is an old mechanical hard drive, and I'll want to replace it with an SSD in a few months.

When I want to replace the mechanical drive with the SSD, I wondered how I do it.

Do I do a custom install again, and
[LIST]
[*]define 2 partitions on the SSD (one for / and one for swap) - and check the format box, and
[*]define the other hard drive to have my /home on it, [COLOR="Red"]**BUT NOT CHECK THE FORMAT BOX?**[/COLOR]
[/LIST]

Thanks!
Phil Smith de Duluthistan, GA

---

### Post by grahammechanical on 2011-06-28
I would say Yes.

Set the second drive to have a mount point of /home and most definitely do not mark it for format.

Create two partitions on the SSD and set a mount point of / and /swap. The SSD drive will need formatting anyway. Then when the OS installs it will know where /home is located.

I once converted a /home folder into a /home partition but the OS failed to load because it could not find the /home folder or the configuration files in it. A fresh install of the OS into the partition mounted as / allowed it to pick up the /home partition which = a working OS.

Regards.

---

### Post by nothingspecial on 2011-06-28
> **Phil Smith said:**
> Hi Ubuntu Community:

I installed Ubuntu on a new machine and used the custom install to:

[LIST]
[*]put the operating system (/) on one drive, and
[*]to put my /home directory on a different drive.
[/LIST]

The hard drive I've installed the OS on is an old mechanical hard drive, and I'll want to replace it with an SSD in a few months.

When I want to replace the mechanical drive with the SSD, I wondered how I do it.

Do I do a custom install again, and
[LIST]
[*]define 2 partitions on the SSD (one for / and one for swap) - and check the format box, and
[*]define the other hard drive to have my /home on it, [COLOR="Red"]**BUT NOT CHECK THE FORMAT BOX?**[/COLOR]
[/LIST]

Thanks!
Phil Smith de Duluthistan, GA

Yep, that's how you do it :D

---

### Post by amjjawad on 2011-06-28
If I were you, I would backup my important files, format both and install on the new HDD only and perhaps use the old one for some other purposes. But that's me :)

---

### Post by Old Jimma on 2011-06-28
Dear Community:

Thank you for your comments an confirmation on how to install a new upgraded OS at / while maintaining the /home on another drive.

Now for the reality test....

Having screwed things up so badly and so often, I must wholeheartedly agree with [COLOR="Red"]**amdjawad**[/COLOR]... :o

Perhaps rule #1 of fooling with Ubuntu is: "BACK THINGS UP FIRST!"

:P

Many thanks!
Phil Smith de Duluthistan, GA

---

### Post by tgm4883 on 2011-06-28
> **Phil Smith said:**
> Dear Community:

Thank you for your comments an confirmation on how to install a new upgraded OS at / while maintaining the /home on another drive.

Now for the reality test....

Having screwed things up so badly and so often, I must wholeheartedly agree with [COLOR="Red"]**amdjawad**[/COLOR]... :o

Perhaps rule #1 of fooling with Ubuntu is: "BACK THINGS UP FIRST!"

:P

Many thanks!
Phil Smith de Duluthistan, GA

Yep, can't forget the #1 rule when it comes to determining if data is important.

Is it backed up? No? Then it's not important.

---

### Post by Old Jimma on 2011-06-28
How did you guys get so many beans???

---

### Post by dFlyer on 2011-06-28
Reminding people to backup first and helping the one that didn't backup first. Murphy's law applies, If anything can go wrong it will if proper precaution are not taken.

---

### Post by amjjawad on 2011-06-28
> **Phil Smith said:**
> How did you guys get so many beans???

One Post = One Bean :)

---

### Post by amjjawad on 2011-06-28
> **Phil Smith said:**
> Perhaps rule #1 of fooling with Ubuntu is: "BACK THINGS UP FIRST!"


Yes, better safe than sorry.

***My other golden rule is = NO OS is Perfect :)***

---

### Post by nothingspecial on 2011-06-28
> **Phil Smith said:**
> How did you guys get so many beans???

You get a bean for asking as well.

---

