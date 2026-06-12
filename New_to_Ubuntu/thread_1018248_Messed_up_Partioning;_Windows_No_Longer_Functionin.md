---
title: "Messed up Partioning; Windows No Longer Functioning"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by HSKR on 2008-12-21
I was looking to upgrade from Hardy Heron up to Intrepid Ibex a few days ago, but it turned out that my Hardy's filesystem had been corrupted or some such, so I proceeded to burn a new CD with an 8.10 ISO on it. After burning, I began the installation process. Here's where I screwed up. I (foolishly / accidently) partitioned the entire disk space for Ubuntu, leaving no room for Windows. Realizing my mistake, I attempted to re-partition / reinstall, but to no avail, and windows appears to be lost. On one of my hard drives, a ST3160023A (yes, this is an old computer), I have Ubuntu 8.10 and no windows. The other drive, a Samsung SP 2004C, has Ubuntu 8.10 (which is not functioning) and Window XP Home Edition. When I try to start up XP, I receive an error message saying:

[QUOTE=ERROR]Error 13: Invalid or unsupported executable format[/QUOTE]

However, I did reboot and was able to load XP one time, but after a second reboot, I got the above error.

So, my question is, is there anyway I can recover my old Windows, uninstall Ubuntu, and then reinstall it with the correct partitioning?

---

### Post by HSKR on 2008-12-22
If they are no solutions, I think it'd be best to just wipe the whole thing.

---

### Post by drs305 on 2008-12-22
Try SuperGrubDisk. It works very well on screwed up systems; if you got windows to boot even once it is still intact. Download SGB from this site:
[http://www.supergrubdisk.org/index.php]("http://www.supergrubdisk.org/index.php")

The link is to linux page but the CD works on windows as well.

---

### Post by Duck2006 on 2008-12-22
If you boot up with the win xp cd,
Press r for recovery mode,
and do a fixmbr.
Can you boot to your win partition?

---

### Post by HSKR on 2008-12-22
> **Duck2006 said:**
> If you boot up with the win xp cd,
Press r for recovery mode,
and do a fixmbr.
Can you boot to your win partition?

Tried this, now on both drives I receive an error before I even get to GRUB:

[QUOTE=ERROR]Error loading operating system[/QUOTE]

I am currently posting from my mac.

I'm thinking I should've tried to SuperGrubDisk method first :(

---

### Post by HSKR on 2008-12-22
Once again, if there's really nothing I can do now, I'm just gonna reinstall both OS's.

---

### Post by Duck2006 on 2008-12-22
> **HSKR said:**
> Once again, if there's really nothing I can do now, I'm just gonna reinstall both OS's.

It may be best to do that, let us know how it does.

---

### Post by HSKR on 2008-12-22
Sure thing, and thanks! :)

---

### Post by HSKR on 2008-12-23
I've reinstalled Ubuntu on one of my hard drives and XP on the other. Things are running smoothly!

---

### Post by Duck2006 on 2008-12-23
> **HSKR said:**
> I've reinstalled Ubuntu on one of my hard drives and XP on the other. Things are running smoothly!

Good to hear it went well for you.

---

